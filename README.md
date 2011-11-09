# PyOpenNI #

## Introduction ##

**PyOpenNI** is a project providing bindings for the [OpenNI](http://openni.org) computer vision library on Python. It is a fork of [onipy](http://code.google.com/p/onipy) but adds many improvements to it:

 * Removed unnecessary `OpenNI` prefixes.
 * Uses CMake, the popular cross-platform buildsystem, to configure & compile the bindings.
 * Autodetects needed libraries and warns you if they're not found.
 * Code cleanup and formatted according to [PEP 8](http://www.python.org/dev/peps/pep-0008) rules.

PyOpenNI is written with the [Boost.Python](http://www.boost.org/doc/libs/release/libs/python/doc/index.html) libraries.

## Using the bindings ##

**An example script that uses the bindings:**

```python
from openni import *

ctx = Context()
ctx.init()
gest = GestureGenerator()
gest.create(ctx)
    
def gesture_detected(gesture, id, endPoint):
    print "Detected gesture %s!" % gesture

for gesture in gest.get_supported_gestures():
    gest.add_gesture(gesture)
gest.register_gesture_callbacks(gesture_detected)

input_raw("Press ENTER to quit.")
```

We tried to respect the C++ names and structure.  
See the documentation (stored at `doc/`) for more details.