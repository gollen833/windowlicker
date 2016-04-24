If you are using Linux, you can use the listener feature of JUnit to wrap "recordmydesktop", showing you what happens when the tests are running.

Add this to the `<junit>` ant task

```
   <formatter classname="com.objogate.wl.build.RecordingFormatter"/>
```


The code is not currently packaged as part of Window Licker, however you can see the code required

See the following:

http://code.google.com/p/windowlicker/source/browse/trunk/tools/src/main/com/objogate/wl/build/RecordMyDesktopWrapper.java
http://code.google.com/p/windowlicker/source/browse/trunk/tools/src/main/com/objogate/wl/build/RecordingFormatter.java