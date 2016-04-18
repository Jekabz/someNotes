#class design guidelines:
* This makes good oop:

* __Always keep data private__:
  * Anything else violates encapsulation
  * this way, changes in data representation will not affect the users of the class

* __Always initialize data:__
  * Java does not initialize local variables for you, but does initialize the instance fields of objects
  * You should not rely on the defaults and initialize the variables explicitly

* __Do not use too many basic types in a class:__
  * Instead, it is better to replace multiple related uses of basic types with other classes
  * This makes for easier understanding and change

* Not all fields need individual field accessors and mutators
  * do not make getters and setters for fields that do not need them

* Break up classes that have too many responsibilities

* Use sensible names

* Prefer immutable classes
  * no method can change the state of an __object__
  * instead of mutating the object, methods return an object with a modified state
  * This is needed because mutations could happen concurrently when multiple threads try to update the object state at the same time, the results of this are unpredictable
  * immutable class objects are safe to share among multiple threads
