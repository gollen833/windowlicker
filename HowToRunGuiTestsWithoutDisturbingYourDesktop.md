## Linux ##

Install Xvfb or Xnest.  Xvfb is an off-screen virtual X display.  Xnest is a virtual X display that is "nested" within a window of another display.  Xvfb is most useful for automated testing by a [continuous integration](http://martinfowler.com/articles/continuousIntegration.html) server, so we will use that for this document but the principles apply just as well to Xnest.

Start Xvfb in the background as display 1 (assuming you have only one display already, which will have id 0):
```
% Xvfb :1 &
```

Set the DISPLAY environment variable to point at the virtual display:
```
% export DISPLAY=:1
```

Run your tests or start your build server.  For example:
```
% ant system-tests
```

## MacOS ##

Unknown.  Suggestions welcome!

## Windows ##

Unknown.  Suggestions welcome!