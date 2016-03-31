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
