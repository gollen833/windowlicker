The default behaviour of Window Licker can be tweaked by setting system properties.

| **Property** | **Purpose** | **Default** |
|:-------------|:------------|:------------|
| com.objogate.wl.poll-delay | The time in milliseconds that the Prober waits between polls of a probe | 100         |
| com.objogate.wl.timeout | The maximum time in milliseconds that the Prober will wait for a probe to execute successfully. | 1000        |
| com.objogate.wl.keyboard | The name of the keyboard layout.| The current input locale. |

All the system properties that Window Licker uses and their default values, where appropriate, are defined as constants in the [SystemProperties](http://code.google.com/p/windowlicker/source/browse/trunk/java/com/objogate/wl/SystemProperties.java) interface.