#Methods and encapsulation
#### Scope of variables
* `local variables`aka method local
* `method parameters` aka method arguments
* `instance variables` aka attribute, field or nonstatic variable
* `class variable` aka static variable

###### local variable
* defined within a method()
* stores intermediate results of calculation
* lives within a methodor some other block and only accessible from it
* scope of variable is method

###### method parameters
* `public void foo(type myVariable){}`
* accessible in all of the method

###### instance variables
* stores the state of an object
* available as long as an object aka instance lives
* instance variable is defined within the class, out of all the methods
* accessible to all __nonstatic__ methods defined in class

###### class variable
* stores values that should be shared by all objects of a class
* defined using keyword __static__
* class variable belongs to a class and is shared among all the objects of type class
* To access the class variable, no object is obligatory, but can be used
  * `Classname.staticvariablename = something;`
  * `objectname.staticvariablename = something;`
* __scope__ of class variable:
  * Available to all the objects of the class
  * Depends on the access modifier of both the class and itself

###### overlapping variable scopes
* static and variables cannot have the same name as any other variables
* this is valid:
```java
class MyPhone {
    static boolean softKeyboard = true;
    String phoneNumber;
    void myMethod() {
      boolean softKeyboard = true;
      String phoneNumber;
  }
}
```

----
#### Object's life cycle
* Java Object gots finalize() method, that is called before garbage man kills the object
* Java classes can override finalize()

###### birth of an Object
