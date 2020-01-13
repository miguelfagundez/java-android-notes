# Garbage collector.

Memory could be a heap or a stack. An stack keeps an order of each object as they are created, which is a static memory allocation.
However, JVM implements a heap approach. This means that each object is created dynamically in memory.

![StackVsHeap](https://www.guru99.com/images/java/052016_0744_JavaStackan14.jpg)

If you wan to understand more how works this momery allocation, you can read this [tutorial!](https://www.guru99.com/java-stack-heap.html).

Garbage collection is the process to look in the heap memory, detecting which objects are in use and which objects are not. The objects
that are not used (they do not have a reference) can be deteled by the GC. A referenced object means that at least one part of your
program still remains a pointer to an object. An unreferenced object means that is not longer need in your program; therefore,
GC delete them from memory.

The heap is divided by three pools:
* Young generation.
* Old generation.
* Permanent generation.

![GCGenerations](https://upload.wikimedia.org/wikipedia/commons/5/52/JavaGCgenerations.png)
Via  [wikipedia!](https://de.wikipedia.org/wiki/Datei:JavaGCgenerations.png).

Newly objects are in the young generation. Objects that are long-lived are eventually moved from the Young Generation to the 
Old Generation. Finally, Metadata such as classes and methods are stored in the Permanent Generation. During a garbage collector cycle,
unused objects are removed from all generations.

Finally, we can request to JVM to run Garbage collection throughout:

```
System.gc();
or
Runtime.getRuntime().gc();
```

However, there is not guarantee that these methods will run the Garbage collector. 
