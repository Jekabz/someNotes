#DESIGN HINTS FOR INHERITANCE

* Place common operations and fields in the superclass
* Do not use `protected` fields
  * anyone can inherit from your class and directly access `protected` members, therefore breaking encapsulation
  * in the same package, all classes can access `protected` members, therefore breaking encapsulation
* Use inheritance to model the __is a__ relationship
* Dont use inheritance unless all inherited methods make sense
* Dont change the expected behavior when you override the method
* Use polymorphism not type information
  ```Java
  if (x is of type 1)
    action 1 (x);
  else if (x is of type 2)
    action 2 (x);
  ```
  * if `acction1` and `action2` represent a common concept, make it a method of a common superclass or interface, then simply call `x.action()`
* Dont overuse Reflection
