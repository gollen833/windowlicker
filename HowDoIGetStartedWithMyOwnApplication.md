The question we get asked most often is "How do I plug this into my own application"

What you need to do is make your top-level window, and make a driver for it.

The top level driver is a little different from the others, as you will give it a GesturePerformer...

Here's the code from the CalculatorDriver, adapt as you need...

```
public class CalculatorDriver extends JFrameDriver {
    @SuppressWarnings("unchecked")
    public CalculatorDriver() {
        super(new GesturePerformer(), named(MAIN_WINDOW), showingOnScreen());
    }
}
```