Because the Swing GUI and the Window Licker test run in separate threads, you cannot use Window Licker to assert that something has _not_ happened in the same way as you do in a vanilla unit test.

A unit test would test that something does not happen by invoking the object under test and then, when the invocation has returned, asserting that the object has not changed state.  Alternatively, it might use [mock objects](http://www.mockobjects.com) to check that the object under test does not make any calls to its neighbours.

However, when Window Licker performs an input gesture, the system under test processes that input on Swing's event dispatch thread and may spawn off worker threads to complete the processing in the background.  The system under test may not even have _started_ processing the input events by the time Window Licker has performed the  gesture and control has returned to the test.  Therefore, if the test asserts that nothing has happened after the gesture the system under test will not have finished processing the input and the assertion will succeed immediately without actually testing anything.

A test could wait for some fixed period and then check that the unwanted event did not occur, but that makes tests run slowly and we ideally want tests to succeed fast.

Instead, the test should interact with the system in a way that should not cause the unwanted behaviour and then stimulate it in a way that will have an observable effect. The test can wait for the observable effect and then check that the unwanted event did not occur in the meantime.

See [this calculator test](http://code.google.com/p/windowlicker/source/browse/trunk/calculator-example/end-to-end-tests/com/objogate/wl/example/calculator/tests/ExampleWhenNothingHappensTests.java) for an example.

You might also like to see page 18 of [this presentation](http://www.natpryce.com/presentations/xpday-2008.pdf) Nat gave at XPDay 2008