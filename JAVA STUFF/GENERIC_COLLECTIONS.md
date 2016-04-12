# GENERIC COLLECTIONS

![pic]()
* collection i a data structure and an object
* it holds references to objects of its own type

* `Collection` -- *root interface in the collections hierarchy from wich interfaces set Queue and List are derived*
* `Set` -- *a collection with no duplicates*
* `List` -- *can have duplicates*
* `Map` -- *key - value pairs, no duplicate keys*
* `Queue` -- *first in, first out, but other orders are possible*

* classes and interfaces in the __collections__ framework are members of package `java.util`
* with `generics` you can specify the exact type of references, the collection will hold + there is compile type safety

----

#### TYPE WRAPPER CLASSES FOR PRIMITIVE TYPES
* these:
  * `Boolean`
  * `Byte`
  * `Character`
  * `Double`
  * `Float`
  * `Integer`
  * `Long`
  * `Short`
* allows to manipulate primitive type values as objects
* this is needed, because some data structures cannot manipulate variables of a primitive type, but can manipulate objects
* these wrapper classes have methods, that are useful

----
####AUTOBOXING AND AUTO - UNBOXING
* in old times, before even Java SE5, you had to create a wrapper class for the primitive value and then insert that in a collection, and if you wanted to retrieve an object from a collection, you got to invoke a method of the wrapper class that you got from collection:

```Java
Integer[] integerArray = new Integer[ 5 ]; // create integerArray
// assign Integer 10 to integerArray[ 0 ]
integerArray[ 0 ] = new Integer( 10 );
// get int value of Integer
int value = integerArray[ 0 ].intValue();
```
* what __boxing__ and __unboxing__, you deal with this automatically:

```Java
Integer[] integerArray = new Integer[ 5 ]; // create integerArray
integerArray[ 0 ] = 10; // assign Integer 10 to integerArray[ 0 ]
int value = integerArray[ 0 ]; // get int value of Integer
```

----
####INTERFACE COLLECTION AND CLASS COLLECTION
* interface collection:
  * root interface in the collection heirarchy. from which other are derived
  * interface collection contains __bulk operations__ for adding, clearing and comparing objects in a collection
  * provides a method, that returns an __Iterator__ object
  * other methods
  * Collection is used as a parameter type in methods to allow *polymorphic* processing of all objects that implement interface Collection

* class collection
  * provides static methods that search, sort, and do other operations on collections
  * `Synchronized collection` -- *for use with multithreadind*
  * `unmodifiable collection` -- *view, but no add or delete*

----
####LISTS
* Ordered collection with duplicate elements
* List indexes are zero based
* interface `List` is implemented in:
  * `ArrayList` -- *resizeable, inefficient to include elements not in the end*
  * `LinkedList` -- *efficient insertion(removal too) of elements in the middle. Used for stacks, queues and deques*
  * `Vector` -- *resizeable, inefficient to include elements not in the end*
* `Vector` vs `ArrayList`:
  * nearly identical
  * `Vector` is Synchronized, `ArrayList` is not
  * `Vector` is legacy, it was before collections, so it has methods that are not part od interface `List`, but has identical tasks
  * Unsynchronized collections provide better performance than synchronized ones
  * if no multithreading, use ArrrayList
  * `ArrayList` behaves like `Vector` without synchronization, so they execute faster
* Autoboxing occurs with Lists

----
######ArrayList and Iterator
```java
Iterator<type> name = collectionName.iterator();
while(iterator.hasNext()){
  //do stuff
}
```
* iterator is unusable, if the collection is changed.


----
####COLLECTION methods
* List methods, they are polymorphic:
  * sort
  * binarySearch
  * reverse --
  * shuffle --*Randomly orders a List ’s elements.*
  * fill -- *Sets every List element to refer to a specified object.*
  * copy --*Copies references from one List into another.*
* Collection methods:
  * min
  * max
  * addAll -- *Appends all elements in an array to a Collection .*
  * frequency -- *Calculates how many collection elements are equal to the specified element.*
  * disjoint --*Determines whether two collections have no elements in common.*

----
####STACK CLASS OF java.util

----
####CLASS PriorityQueue and InterfaceQueue

----
####SETS

----
####MAPS

----
####PROPERTIES CLASS

----
####SYNCHRONIZED COLLECTIONS

----
####UNMODIFIABLE COLLECTIONS

----
####ABSTRACT IMPLEMENTATIONS

----
