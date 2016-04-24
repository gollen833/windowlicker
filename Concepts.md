### Component Driver ###

Tests use [ComponentDriver](http://code.google.com/p/windowlicker/source/browse/trunk/java/com/objogate/wl/driver/ComponentDriver.java)s to interact with and make assertions about the user interface of the system under test.  A Component Driver
uses Gestures and Probes to interact with a real user interface component and provides the test with a convenient, higher level API.

### Gesture ###

A [Gesture](http://code.google.com/p/windowlicker/source/browse/trunk/java/com/objogate/wl/Gesture.java) interacts with the user interface through the input devices.  Window Licker runs tests by performing Gestures and using Probes to observe the results.

There are a number of primitive gestures, such as pressing or releasing a mouse button or key or moving the mouse. Gestures can be composed into new gestures.  For example, typing text is performed by a sequence of gestures, each of which types one character by performing three gestures: pressing a key, waiting for a short while and then releasing the key.

### Probe ###

A Probe samples the system and reports whether the last sample satisfies some test criteria.  It can describe itself and why the last sample (if any) did not satisfy its test criteria.

Probes are run asynchronously by a [Prober](http://code.google.com/p/windowlicker/source/browse/trunk/java/com/objogate/wl/Prober.java), which is responsible for inserting the probe into the system under test,  synchronising with its execution and reporting the result of the probe.

### ComponentFinder ###

A ComponentFinder is a Probe that looks for GUI components that match a set of criteria specified by Matchers.  The probe is successful if it finds at least one matching component.

### ComponentSelector ###

A ComponentSelector is a ComponentFinder that expects to find a single GUI component.  It fails if it finds none or more than one.

### Matcher ###

Window Licker uses [Hamcrest](http://code.google.com/p/hamcrest) Matchers to describe user interface components that are searched for by ComponentFinders.

### Query ###

A Query returns the value of a component's property so that it can be matched by a Matcher.  It is used to make assertions about a component's state.  Component Driver classes define static factory methods that return queries for the underlying component's properties.

### Tracker ###

An object that represents a, possibly moving, location on screen.  The mouse movement gesture uses a Tracker to define the destination of the movement so that the mouse can be used to interact with animated components.