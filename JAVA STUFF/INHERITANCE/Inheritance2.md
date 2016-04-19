#INHERITANCE

####Classes, Superclasses, and Subclasses

* Subclass extends class
* `super` will call the parent class method version
* inheritance cannot ever take away any fields or methods
* `dynamic binding` -- Automatically selecting the appropriate method at runtime, if class method overrides Superclass method
  * `dynamic binding` maketh the code extensible without need to alter the existing code. Yo can, for example, add a new class and refer to it by its parent class reference. In this case, you do not need to alter method calls in code that uses this reference
* `static binding` -- compiler knows exactly which method to call, if it is marked as `private`, `static`, `final`, or ia a constructor
* arr of derived class type can be assibned to parent class reference, but yo cannot put in arr a var of Superclass type!
* when subclass overrides a parent class method, subclass method's return type has to be that of a parent class, or one that is derived from it (covariant return types)
* subclass can only have overriden method that is at least as visible as the Superclass method

----
* in `final class`, all methods are Automatically `final`, this is not true for variables

----
* You can cast only within an inheritance hierarchy.
* best do casts like this:
```Java
if(parentClassObject instanceof childClassObject){
  childClassObject foo = (childClassObject)parentClassObject;
}
```

----
####abstract class
* as you move up the inheritance tree, classes become more general, so at some point a class becomes only a base for other classes to extend

----
####Object - the superclass

* `equals` method, as implemented in the Object class, determines whether two object references are identical


######Equality Testing and Inheritance
* `static boolean equals(type[] a, type[] b);` -- returns true if the arrays have equal lengths and equal elements in corresponding positions
* `static boolean equals(Object a, Object b);` -- returns true if a and b are both null , false if exactly one of them is null , and a.equals(b) otherwise.

######The hashCode Method
* The __hash code__ is an integer that is derived from an object
* `hashCode` has to be consistent for one object
* `hashCode()` is used for bucketing in Hash implementations like `HashMap`, `HashTable`, `HashSet`, etc.
* The value received from `hashCode()`` is used as the bucket number for storing elements of the set/map. This bucket number is the address of the element inside the set/map.
* When you do `contains()` it will take the hash code of the element, then look for the bucket where hash code points to. If more than 1 element is found in the same bucket (multiple objects can have the same hash code), then it uses the `equals()` method to evaluate if the objects are equal, and then decide if `contains()` is true or false, or decide if element could be added in the set or not.

######The toString Method
* Most (but not all) `toString()` methods follow this format: the name of the class, then the field values enclosed in square brackets:
`java.awt.Point[x=10,y=20]`
* Used for logging

######Generic ArrayList

######Object Wrappers and Autoboxing
* converts primitive types to objects
* done by compiler not JVM
* wrapper classes are __immutable__ and __final__ (no Subclasses)
* do not compare wrapper classes with `==`, because result depends on implementation

######Enumerators
* Use Enums when a variable can have only one of a small set of possible values (constants)
* Typically used for flags or type codes

----
####Reflection Library
* Reflection analyzes the capabilities of classes
* Interest more tool builders for other Java programmers
