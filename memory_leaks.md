# Memory Leaks

A memory leak is an object that our application is not longer used, but the garbage collector fails to recognized these objects as unused. The result is that these objects remains in memory taking valuable space and resources that never freed for other used objects.
There are multiple problems due to memory leaks. These problems go to erratic behavior, slow down in performance, or even worse, crash the app.

We have to try to evaluate during early stages of a development these issues. There are common patterns that can be avoid.

![leak](https://www.holdapp.com/sites/default/files/blog_img/leak.png)

Android Performance Patterns: [image source!](https://youtu.be/BkbHeFHn8JY?t=43s)

## View outside the UI thread.
If a view is unused but still referenced, this view and its whole subhierarchy of children cannot be freed. So, its whole associated activity also stays in memory. To fix it, we must avoid defining views outside the UI thread.

Leak memory:
```
code line 1
code line 2
```

Solution:
```
code line 1
code line 2
```

## Thread leak.
If a thread is running in the background and an implicit reference exists, then a possible memory leak is presented. To fix it, we have to make sure our thread is a static class and interrupt it in the destroy callback.

Leak memory:
```
code line 1
code line 2
```

Solution:
```
code line 1
code line 2
```

## Anonymous classes.
Sometimes and anonymous class instance lives longer than its container. If this class calls any method or member of its container, it would retain the container instance. To fix it, we should be sure that the anonymous class does not call any method or members of the container class or making this as static class.

Leak memory:
```
code line 1
code line 2
```

Solution:
```
code line 1
code line 2
```

## Inner classes.
Inner classes are another common source of memory leaks because they can also have a reference to their container classes. To fix it, we should convert any inner class to static class. Static class does not have any reference to the container class, so we do not have to option to leak our activity class.

Leak memory:
```
code line 1
code line 2
```

Solution:
```
code line 1
code line 2
```

## Static variables. 
Static variables which are referencing activities must be avoided. They will not be collected due to these variables are associated with the class directly and not with an instance of the class.

Leak memory:
```
code line 1
code line 2
```

Solution:
```
code line 1
code line 2
```

## Singleton object.
If this object references an activity, then a leak memory could be occurred. One way to handle is creating a new method that must be called in the OnDestroy callback to clear the reference.

Leak memory:
```
code line 1
code line 2
```

Solution:
```
code line 1
code line 2
```

