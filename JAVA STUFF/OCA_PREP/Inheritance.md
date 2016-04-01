#Inheritance

#### Inheritance with classes
* class inherits properties and behaviours from another class
```java
class Employee { // superclass aka parent class aka base class
  String name;
  String address;
  String phoneNumber;
  float experience;
}
class Programmer extends Employee { // subclass aka derived class aka extended class aka child class
  String[] programmingLanguages;
  void writeCode() {}
}
class Manager extends Employee { // subclass aka derived class aka extended class aka child class
  int teamSize;
  void reportProjectStatus() {}
}
```
* code that works with base class, also works with subclass, so Inheritance makes the code extensible this way

* Inheritance enables you to reuse code that has already been
defined by a class. Inheritance can be implemented by extending a class.

###### a derived class contains an object of its base class
* derived class can directly access members of its base class:
```java
class Employee{
  String name;
}
class Programmer extends Employee{
  void accessName(String foo){
    name = foo;
  }
}
```

* When a class extends another class, (inherits from it), the subclass contains within an object of the base class.(this is not true for all members of the base class though)

###### base members that are inherited by derived class
* Inherited are:
  * `defaulto` -- if base and derived classes are in the same package
  * `protected`
  * `public`

###### base members that are NOT inherited by derived class
* Not inherited are:
  * `private` members of the base class
  * `default` if base and derived classes are in separate packages
  * base class constructors. Derived class can call them though

###### Derived class defines additional members
* Derived classes can have their own constructors and static members
* if derived class defines a member with the same name as parent class member, only new members are visible to code that uses the derived class

######Abstract  VS concrete base class
* Abstract class groups the common members of its derived classes, but cannot itself be instantiated
* Abstract class can have abstract methods, that would force the derived classes to provide their own implementation
* if derived class does not define abstract method from base class, it must itself be an abstract class
* Base class can be abstract class even if it does not have any abstract methods
* You can use variables of an Abstract base class to refer to objects of its derived class


----
#### interfaces
* An interface can only define constants. Once it’s assigned, you can’t change the value of a constant.
* The variables of an interface are implicitly public , final , and static.
  ```java
  interface MyInterface {
  int age = 10;
  }
  ```
  is equvivalent to:
  ```java
  interface MyInterface {
  public static final int AGE = 10;
  }
  ```
* The methods in interfaces are implicitly public:
  * When implementing an interface, you must implement all its methods with access modifier `public`
  * Class that implements an interface, cannot make its methods more restrictive:
  ```java
  interface Relocatable {
  void move();
  }
  class CEO implements Relocatable {
  void move() {} // Compilation error, because default access is more restrictive than public!
  public void move(){} // This is how it should be!
  }
  ```

###### Class cannot extend multiple classes:
* Multiple inheritance is not allowed because the derived class may inherit different implementations for the same method signature

###### Implementing multiple interfaces
* an interface can extend multiple other interfaces
* because interfaces do not define method implementations, multiple methods of the same signature are allowed.

###### what if implemented interface and extended concrete class has the same method signature?
* Interface makes an abstract class that has to be implemented, and it overrides any method with the same signature in any parent class:
```java
public class Bar {
	public static void main(String... args) {
		Whatever whatever = new Whatever();
		whatever.setName("someName ");
		System.out.println(whatever.getName()); // someName from interface
	}
}

class Foo {
	protected String name;
	void setName(String name) {
		this.name = name + "from base class";
	}

	String getName() {
		return name;
	}
}

interface Baar {
	void setName(String name);
}

class Whatever extends Foo implements Baar {
	public void setName(String namePassed) {
		name = namePassed + "from interface";
	}
}
```

#### reference variable and object types
* the type of object reference variable may differ from the type of object being referred to
* an object can be referred to by these types:
  * its own type
  * its base class (type)
  * implemented interfaces

###### using derived class variable to access its own object
* basically uses its own type, nothing fancy:
`type name = new type();`
* with this reference variable, you can access all the variables and methods that are defined in its base class and interface

###### using variable of base class type to access object of derived class type
* this kind of reference only has access to members that are inherited from the base class. No interface methods and derived class members are accessible

###### using variable of an implemented interface to access a derived (implemented) class object
* this kind of reference can only access members defined in the implemented interfaces

###### why access an object by its base class or implemented interface?
* You may not be concerned about the details -- base class
* You may only be interested in specific implementation of interface -- use interface
* You can make an array of different objects this way

----
#### Casting
* casting allows to get to other members, if object is referred to by superclass or an interface
`type name = ((ChildClass)SuperclassReference).variableName;`

#### this and super
* __this__ and __super__ are implicit object references, these variables are defined and initialized by the JVM for every object in its memory

###### this
* points to objects own instance
* `this` may be used to differentiate between an instance variable and some local or method variable or parameter

###### using this to access constructors
```java
class ClassName{
  String string;
  ClassName(String string){
    this.string = string;
  }
  ClassName(String string, String foo){
    this(string); //calls previous constructor
  }
}
```
* You can also call the default constructor from within another constructor, but then it has to be the first statement in it( not even if is allowed):
```java
ClassName(whatever){
  this(); //must be the first statement
  //whatever
}
```

* __this__ refers to the instance of the class in which it’s used. this can be used to access the inherited members of a base class in the derived class.

###### object reference super
* __super__ refers to the parent of a class
* you can use super to access the member of a parent class in case of a name clash

###### using super to access the constructors of a base class
* if present, a call to a parent class constructor must be the first statement in a child class constructor, otherwise, the call to super(); is automatically inserted by the compiler

###### using super and this in static methods
* super and this are implicit object references, but static members belong to a class itself, therefore it is not possible to use super and this for static members

----

#### Polymorphism
###### Polymorphism with classes
* class inherits from another class and both of them have methods with the same signature. Java will execute the method that belongs to reference variable type class
* Basically you got an abstract class and it has an abstract method. the abstract method is implemented by the child classes. These classes are having the abstract class type reference variable. This variable is used to call the methods, which then have different implementations. Now you got Polymorphism!

###### polymorphic methods are also called overriden methods
* @ Override is not used, because class inherits from an abstract class and has an abstract method, instead "overriden" simply refers to the fact that the method signatures are identical!
* @ Override must be used if overriding concrete class though!
* __polymorphic methods do not always have to be abstract__
* the return type of overriden method in child class can be a subclass of parent class method's return type
* child class version of the method has to hava same or less restrictive access modifiers

###### variable and method binding in compile and runtime
* variables bind at compile time, whereas methods bind at runtime
* variables:
  * the reference type determines, which variable (base or child) will be used
* methods:
  * will execute the overriden method in child class

----
#### Polymorphism with interfaces
* always involves abstract methods, because interface
* if you refer to objects by interface, these objects can have and does have different implementation for abstract methods defined in interface. therefore by calling interface methods on different objects, one method will return different behaviours!

----
