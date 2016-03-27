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
* when keyword __new__ is used
```java
class Person{}
class Whatever{
  Person person; //reference variable, no actual Person object is created
  Person person1 = new Person();// creates an object and a reference variable
}
```
* Strings are little different:
```java
class Foo{
  String string1 = new String("foo"); // valid
  String string2 = "bar"; // also valid
}
```
```java
class Phone {}
class TestPhone {
	TestPhone(){new Phone();} //object is created, but cannot be accessed
}
```
###### object is accessible
* access is done using reference variable
* access is granted while in scope and while reference variable != null and while it is not set to point to another object

###### object is inaccesible
* You can be sure only about which objects are marked for garbage collection. You can never be sure exactly when the object will be garbage collected.

----
#### Methods with arguments and return values
* method is used to define the behavior of an object
* things to know about methods:
  * return type
  * method parameters
  * return statement
  * access modifiers
  * nonaccess modifiers
