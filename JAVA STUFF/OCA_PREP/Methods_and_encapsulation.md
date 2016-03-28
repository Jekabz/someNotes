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
    * type of value that method returns
    * can be primitive type or an object of a class or an interface
    * returned info need not be saved (assigned to a variable)
  * method parameters
    * a comma seperated list of parameters
    * no limit as to how many can be there
    * method __parameters__ are the passed members, method __arguments__ are actual values that get passed
    * arrays can be passed
    * only __one__ ellipsis can be defined as argument and it should be the last on the list
  * return statement
    * If the return type of a method is int , the method can return a value of type byte
    * exits from a method with or without a value
    * void methods can also have a return; then they end execution, but return nothing
    * non void methods can only return non void returns
    * No code can follow (be executed) return statement, if it does, its compilation error
    * method can only return zero or one value
  * access modifiers
  * nonaccess modifiers

#### overloaded methods
* Same name, different parameter list (different types or different order)
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-27%2018:37:56.png)
* easy to add methods with similar functionality
```java
  int intVal = 10;
  boolean boolVal = false;
  String name = "eJava";
  System.out.println(intVal);
  System.out.println(boolVal);
  System.out.println(name);
```
* overloaded methods may or may no have different return type or access modifiers, it does not matter. Arg list matters
* derived classes also can have overloaded methods

###### Argument list
* compiler may not distinguish between methods:
```java
class MyClass {
  double calcAverage(double marks1, int marks2) {}
  double calcAverage(int marks1, double marks2) {}

  public static void main(String args[]) {
    MyClass myClass = new MyClass();
    myClass.calcAverage(2, 3); //compilation error! int can be passed to double
  }
}
```

----
#### Class constructors
* Constructor is a method that creates and returns an object of the class they are defined in
* Constructor does not have a return type
* Constructor has the same name as the class they are in`
* Constructor can have  access modifiers

###### user - defined constructors
* constructor can have access modifiers: __public, default, protected, private__
* adding a return type to a constructor will make it into another method, it will no longer be a constructor

###### initializer blocks vs constructors
* initializer block is defined within a class and not a method
* executes __before__ the constructor
```java
class Foo {
	{System.out.println("This is initializer block");}
	Foo() {System.out.println("This is constructor");}
}

public class Bar { // if more than one class, the main() has to be in public (?)
	public static void main(String... args) {
		Foo foo = new Foo();
		/*
		This is initializer block
		This is constructor
		*/
	}
}
```
* initializer blocks are used to initialize the variables of __anonymous__ classes
* __anonymous__ class is a type of inner class (advanced)
* initializer blocks accept no arguments

###### default constructor
* if there is no user defined constructor, compiler adds it
* else nothing

###### overloaded constructors
######invoking overloaded constructor from another constructor
* uses this and not a name:
```java
class Employee {
  String name;
  int age;
  Employee() {
    // no code in this line allowed
    this(null, 0); //this line must be the first statement
  }
  Employee(String newName, int newAge) {
    name = newName;
    age = newAge;
  }
}
```
* none of other methods in class can call a constructor of its own class, not even static methods

----
#### Accessing object fields
###### Object field
* Object field aka instance variable
* Use setters and getters

----
#### Encapsulation
* By exposing object functionality only through methods, you can
prevent your private variables from being assigned any values that don’t fit
your requirements.
* One of the best ways to create a well-encapsulated class is
to define its instance variables as private variables and allow access to these
variables using public methods

###### passing objects and primitives to methods
* Passing primitives
  * a copy of primitive type value is passed to method
  * the passed primitive type value cannot be altered by method, because copy is passed
  * When you pass a primitive variable to a method, its value remains the same after the execution of the method.
* Passing object references
  * method reassigns the object reference passed to it to another variable
    * state of the object, which was passed on to the method, remains intact.
    ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-27%2023:34:45.png)
  * method modifies the state of the object reference passed to it
    * basically call an instance method to do something like change the state of instance

 ----
