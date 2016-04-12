# GENERIC COLLECTIONS

![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-12%2016:52:23.png)
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
####ITERATORS
* Iterates through elements of a `collection` class
* `Iterator` -- *traverse forward*
* `ListIterator` -- *traverse both directions*

######ITERATOR
* `Iterator` has taken place of `Enumeration` that iterates legacy classes like `Vector`
* Without __generics__:
```Java
import java.util.ArrayList;
import java.util.Iterator;

public class IteratorDemo1 {

  public static void main(String args[]){
    ArrayList names = new ArrayList();
    names.add("Chaitanya");
    names.add("Steve");
    names.add("Jack");

    Iterator it = names.iterator();

    while(it.hasNext()) {
      String obj = (String)it.next();
      System.out.println(obj);
    }
  }

}
```
* with __generics__:
```Java
import java.util.ArrayList;
import java.util.Iterator;

public class IteratorDemo1 {

  public static void main(String args[]){
    ArrayList <String>names = new ArrayList<>();
    names.add("Chaitanya");
    names.add("Steve");
    names.add("Jack");

    Iterator<String> it = names.iterator();

    while(it.hasNext()) {
      String obj = (String)it.next();
      System.out.println(obj);
    }
  }

}
```
* `Iterator` vs `Enumeration`:
  * `Iterator` iterates over a `collection`
  * `Iterator` allows the caller to remove elements from a collection
  * has different method names, but the same functionality

######LISTITERATOR
* goes both forward or back:
```java
import java.util.ArrayList;
import java.util.List;
import java.util.ListIterator;

public class ListIteratorExample {
  public static void main(String a[]){
    ListIterator<String> litr = null;
    List<String> names = new ArrayList<String>();
    names.add("Shyam");
    names.add("Rajat");
    names.add("Paul");
    names.add("Tom");
    names.add("Kate");
    //Obtaining list iterator
    litr=names.listIterator();

    System.out.println("Traversing the list in forward direction:");
    while(litr.hasNext()){
       System.out.println(litr.next());
    }
    System.out.println("\nTraversing the list in backward direction:");
    while(litr.hasPrevious()){
       System.out.println(litr.previous());
    }
  }
}
```
* `ListIterator` can only traverse `list`
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
* Set is a collection that cannot hold duplicate elements
* Set is an interface
######HASHSET
* no particular order of iteration, nor is the order going to be constant over time
* permits the `null` element
* no duplicates, old value overwritten
* fail fast iterator -- if hashset is modified after iterator creation, exception occurs

```Java
import java.util.HashSet;
public class HashSetExample {
   public static void main(String args[]) {
      // HashSet declaration
      HashSet<String> hset = new HashSet<String>();

      // Adding elements to the HashSet
      hset.add("Apple");
      hset.add("Mango");
      hset.add("Grapes");
      hset.add("Orange");
      hset.add("Fig");
      //Addition of duplicate elements
      hset.add("Apple");
      hset.add("Mango");
      //Addition of null values
      hset.add(null);
      hset.add(null);

      //Displaying HashSet elements
      System.out.println(hset); //null, Mango, Grapes, Apple, Orange, Fig
    }}
```

######LINKEDHASHSET
* maintains the insertion order
* same as hashset

######TREESET
* sorts the elements in ascending order (alphabetic for Strings)

----
####MAPS
* key value pairs
* no duplicate keys

######HashMap
* no particular order of iteration
* permits `null` key / value
```java
import java.util.HashMap;
import java.util.Map;
import java.util.Iterator;
import java.util.Set;
public class Details {

   public static void main(String args[]) {

      /* This is how to declare HashMap */
      HashMap<Integer, String> hmap = new HashMap<Integer, String>();

      /*Adding elements to HashMap*/
      hmap.put(12, "Chaitanya");
      hmap.put(2, "Rahul");
      hmap.put(7, "Singh");
      hmap.put(49, "Ajeet");
      hmap.put(3, "Anuj");

      /* Display content using Iterator*/
      Set set = hmap.entrySet();
      Iterator iterator = set.iterator();
      while(iterator.hasNext()) {
         Map.Entry mentry = (Map.Entry)iterator.next();
         System.out.print("key is: "+ mentry.getKey() + " & Value is: ");
         System.out.println(mentry.getValue());
      }

      /* Get values based on key*/
      String var= hmap.get(2);
      System.out.println("Value at index 2 is: "+var);

      /* Remove values based on key*/
      hmap.remove(3);
      System.out.println("Map key and values after removal:");
      Set set2 = hmap.entrySet();
      Iterator iterator2 = set2.iterator();
      while(iterator2.hasNext()) {
          Map.Entry mentry2 = (Map.Entry)iterator2.next();
          System.out.print("Key is: "+mentry2.getKey() + " & Value is: ");
          System.out.println(mentry2.getValue());
       }

   }
}
```

######TreeMap
* slower than HashMap
* red - black tree
* orders elements based on values
```java
import java.util.TreeMap;
import java.util.Set;
import java.util.Iterator;
import java.util.Map;

public class Details {

   public static void main(String args[]) {

      /* This is how to declare TreeMap */
      TreeMap<Integer, String> tmap =
             new TreeMap<Integer, String>();

      /*Adding elements to TreeMap*/
      tmap.put(1, "Data1");
      tmap.put(23, "Data2");
      tmap.put(70, "Data3");
      tmap.put(4, "Data4");
      tmap.put(2, "Data5");

      /* Display content using Iterator*/
      Set set = tmap.entrySet();
      Iterator iterator = set.iterator();
      while(iterator.hasNext()) {
         Map.Entry mentry = (Map.Entry)iterator.next();
         System.out.print("key is: "+ mentry.getKey() + " & Value is: ");
         System.out.println(mentry.getValue());
      }

   }
}
```

######LinkedHashMap
* maintains insertion order
* double linked list
```java
import java.util.LinkedHashMap;
import java.util.Set;
import java.util.Iterator;
import java.util.Map;
public class LinkedHashMapDemo {
    public static void main(String args[]) {
         // HashMap Declaration
         LinkedHashMap<Integer, String> lhmap =
                 new LinkedHashMap<Integer, String>();

         //Adding elements to LinkedHashMap
         lhmap.put(22, "Abey");
         lhmap.put(33, "Dawn");
         lhmap.put(1, "Sherry");
         lhmap.put(2, "Karon");
         lhmap.put(100, "Jim");

         // Generating a Set of entries
         Set set = lhmap.entrySet();

         // Displaying elements of LinkedHashMap
         Iterator iterator = set.iterator();
         while(iterator.hasNext()) {
            Map.Entry me = (Map.Entry)iterator.next();
            System.out.print("Key is: "+ me.getKey() +
                    "& Value is: "+me.getValue()+"\n");
         }
    }
}
```

----
####PROPERTIES CLASS

----
####SYNCHRONIZED COLLECTIONS

----
####UNMODIFIABLE COLLECTIONS

----
####ABSTRACT IMPLEMENTATIONS

----
