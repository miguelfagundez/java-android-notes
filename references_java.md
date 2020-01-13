# References in Java

* Strong
* Weak
* Soft
* Phantom

## Strong references

This is the ordinary reference in Java that everybody write every day. These references
are not eligible for garbage collection and they are kept in memory. Normally, we use 
a variable to hold a reference of a class, data type, etc. Example:

```
public TextView myTextView = findViewById(R.id.textview1);
private String string = "some value here"; 
```

These are examples of strong references. However, if a strong reference points to null
then it will become eligible for java collection.

```
string = null; 
```

## Weak references

Variables or objects are referenced by it may be garbage collected if the JVM is running out
of memory. The object is not enough strong to remain in memory. Example:

```
public WeakReference<TextView> myTextView;
public WeakReference<Class_name> object = new WeakReference<Class_name>();
```

## Soft references

This reference is almost the same as WeakReference; However, it remains in memory a little bit
more time. Normally, this reference resists Garbage collection unless the system is out of 
memory. Example:

```
public SoftReference<TextView> myTextView;
public SoftReference<Class_name> object = new SoftReference<Class_name>();
```

## Phantom references

Objects were defined as a pahntom reference are eligible for garbage collection, but before removing
JVM puts them into a special queue called "reference queue". It is used to know exactly an object 
has been removed from memory. Example:

```
//Creating a Reference Queue
ReferenceQueue<class_name> refName = new ReferenceQueue<class_name>();
//Creating Phantom Reference 
PhantomReference<class_name> refPhantom = new PhantomReference<class_name>(class_object, refName);
```
