# OCA JAVA PREP

### The structure of Java .class and Java source code file:

* .java is a source code file
* .class is bitecode

----
* A real world object is described by a class:
```java
class ClassName {
  String Name;
}
```
* This class then resides in ClassName.java file
* ClassName.java is given to compiler and it outputs ClassName.class with bytecode in it

----

###### Structure of the Java class //object defenition, not bytecode
* There are different components in making of the Java class:
  * The `package` statement
  * The `import` statements
  * Comments
  * Class declaration:
    * Variables
    * Comments
    * Constructors
    * Methods
    * Nested classes
    * Nested Interfaces
    * Enumerators

----
###### package statement
* Classes that are compiled in the same dir. A class in package is implicitly imported in other classes of package, so import declaration is not needed.
* All classes are a part of some package. If no package is defined, class belongs to default package, wich does not have a name
* package declaration is the first (non comment) statement in class definition, and there can only be one
* Main reason for packages is to guarantee unique class names
* if you need to use two classes with the same name from several packages, use the full package name
* `sealed package` -- you cannot add more classes to it

###### import statement
* Classes and Interfaces in the same package can use each other without imports
* To use a `class` or `interface` from another package, you mus use its fully qualified names
* Use `import` to be able to only use the simple name of  `class` or `interface` in your code

###### Comments
###### class declaration
* Basically this:
```java
class Foo{
  //...
}
```
* The declaration of a class is composed of these:
  * Access modifiers
  * Nonaccess modifiers
  * Class name
  * If class extends another class, name of the base class
  * If the class implements any interface, names of all the implemented Interfaces
  * Class body, in `{ ... }`

| public | final | class | ClassName | extends | BaseClassName | implements | InterfaceName | {} |
| ---    | ---   | ---   | ---       | ---     | ---           | ---        | ---           | ---|
| Access modifier | Nonaccess modifier | Keyword | Name | Keyword | Name | Keyword | Name| |
| optinal | optional | needed | needed | optional | optional | optional | optional | needed|

###### class definition
* Class is a design used to specify the properties an behavior of object
* A class is a design from which an object can be created
* A __top level__ class or an interface is such that it is not defined within another class or interface
* A __nested__ class or interface is defined in another class or interface

###### variables
* `instance variables` -- each object (instance of a class) has its own copy
* `class variable` -aka `static variable` -- shared by all objects of a class

###### methods
* `instance methods` -- manipulates `instance variables`
* `class methods` aka `static methods` -- works with `static variables`

###### constructors
* Creates and initializes the object of a class
* Class can have multiple different (overloaded) constructors

----
#### Structure and components of a Java source code file
* defines classes and Interfaces

###### Interface
* `interface`  -- abstract type that contains no data or code, but defines behaviors as method signatures
* use interfaces when you see that something in your design will change frequently
* `interface` specifies a contract for the classes to implement
* Interface is __not__ a class
* Java class can implement multiple interfaces
```java
interface Controls {
  void changeChannel(int channelNumber);
  void increaseVolume();
  void decreaseVolume();
}
```
* Abstract class VS interface:
    * use abstract class when there is strong relationship between the abstract class and the derived classes, use interface when there is not.
    * Abstract class can have non abstract methods and other stuff, interface can only have method definitions, so any implementing class has to provide its own implementations

    * uses:
      * __abstract class:__
        * if you need to use inheritance
        * if you need non public members, because interface is all public methods only
        * if you need more methods in future, because with interface, when adding new methods, those methods then have to be defined in all classes that implemented the interface
      * __interface:__
        * When you thing  code will not change for a time
        * When you want something similar to multiple inheritance

###### Single and multiple class definitions in .java file:
* in one .java file, you can define:
  * a single class
  * multiple classes
  * a single interface
  * multiple interfaces
  * multiple classes and interfaces

* classes and interfaces can appear in any order
* in one .java file, there can only be one `public` class or interface, and its name must match name of .java
  * `public` class name should match .java name
  * if (not in a class body)`public` interface name should match .java name

----
### Executable Java applications
###### Executable Java class VS non-executable Java class:
* in `executable` classes, jvm starts execution at main(), defined in class
* in `non-executable` classes no main() is defined, there is no entry point in them

###### Main() method
* Makes a class executable
```java
public class HelloExam {
  public static void main(String args[]) {
    System.out.println("Hello exam");
  }
}
```
* main() must take in String argsName[] or String argName
* These two are quvivalent:
  ```java
  public static void main(String[] arg){}
  ```

  ```java
  static public void main(String[] arg){}
  ```

###### Java ellipsis (...)
* The ellipsis ( ... ) that follows the data type indicates that the method parameter may be passed as an an array or multiple comma-separated values, or a single value:

```java
class Foo {
	static int method(int... arg) {
		int sum = 0;
		for (int i = 0; i < arg.length; i++)
			sum += arg[i];
		return sum;
	}
}

class Bar {
	int a, b, c, d;
	int[] e = { 1, 2, 3 };
	Foo foo = new Foo();
	int r1 = foo.method(a); // single arg BUT NOT VALID WITHOUT ELLIPSIS
	int r2 = foo.method(a, b, c, d); // coma separeated list BUT NOT VALID  WITHOUT ELLIPSIS
	int r3 = foo.method(e); // array
}
```

###### Java arrays
* These two are quvivalent:
  * `type[] name`
  * `type name[]`

----
#### Java packages
* Packages are used to group together related set of classes and interfaces
* Packages provide access protection
* Packages provide namespace management
* Packages can have subpackages
* Package naming often have strict rules
* Package works like a namespace
* Package naming convention:
`com.organisationname.category.subcategory`
* Package names are all lowercase
* Package and subpackage names are seperated by a `.`

###### Directory structure and package hierarchy
* The hierarchy of packages should match directory structure

###### Classpath and packages
* Allows the JVM to find your classes
* Classpath is .classpath file in the main project directory, which contains paths in xml format.
* classpath is collection of all directories and archive files that are starting points for locating classes
*

###### import packages statement
* import lets you use simple name instead of fully qualified name for classes and interfaces in different packages
* imports do not increase the file size, it simply lets you use a different name

###### importing single vs all members of a classpath
* unlike C++, importing a class does not add to filesize of .class filesize

###### recursively importing subpackages
* not possible

###### static imports
* `import static` -- imports all static members (methods and variables) of a class
* `import static packagename.classname.*;`
* static import declaration imports static members from classes, allowing them to be used without class qualification.
* use it when you require frequent access to static members from one or two classes.
```java
import static java.lang.Math.*; // imports PI
public class HelloWorld {
    public static void main(String[] args) {
        out.println("A circumference of " + (PI * 5) + " cm");
    }
}
```

#### Java access modifiers
* access modifiers are applied to classes, interfaces and their members
* access modifiers control the accessibility of class and its members outside the class and the package

  * `default` -- *members(including classes) are only accessible to classes and interfaces in the same package*
  * `public` -- *makes class available to classes outside its package, import is still necessary though*
  * `protected` -- *access to members from classes in the same package and derived classes in whichever package*
  * `private` -- *private members are not accessible outside the class they are defined in*

###### Access to members
* Standard way is to access class members (in the same package or if package is imported) (call the respective class constructor first) `constructedClassName.membername`
* From a class that extends baseclass, baseclass members can be acessed by their name, no previous baseclass constructor is needed, or allowed.

#### Nonaccess modifiers
* Nonaccess modifiers change the default properties of class and its members
* nonaccess modifiers are:
  * `abstract` -- for __class__ and __metods__
    * class can not be instantiated. It can or cannot define any abstract methods. Non abstract classes cannot contain abstract methods
    * An abstract class can extend a concrete class and vice versa.
    * An abstract class can implement interfaces.
    * An abstract class can extend another abstract class.
    * The first concrete class in the hierarchy must supply actual method implementations for all abstract methods
    * `abstract interface` -- `intertface` is abstract by default, so the following two are the same:
      * `interface Foo{}`
      *  `abstract interface Foo{}`
    * `abstract methods` -- does not have a body and is implemented in a derived class.
    ```java
    abstract class Person{
        public void displayName(); // empty body does not make an abstract method
        public abstract void doSomething(); // abstract method
    }
    ```
    * There is no such thing as abstract variables

    ```java
public abstract class Figure
{
	/* because this is an abstract method the
	   body will be blank  */
	public abstract float getArea();
}

public class Circle extends Figure
{
	private float radius;
	public float getArea()
	{
		return (3.14 * (radius ^ 2)); 	
	}
}

public class Rectangle extends Figure
{
	private float length, width;
	public float getArea(Figure other)
	{
		return length * width;
	}
}
    ```
  * `static` -- for __variables__ and __methods__ and __classes__ and __interfaces__
    * `static` members cannot be overriden by inherited classes, but can be redefined
    * static members are forbidden from accesing instance members
    * `static variable` aka `class variable`
      * common to all instances to class
      * can be accessed even if there are no instances of class
      * `static final` would make a constant
      * it is advisable to access static members through base classname, but can be accessed using child classname aswell      
    * `static methods`
      * cannot use instance variables of the class they are defined in
      * can access and manipulate static variables
    * `static class` -- not for __top level__
    * `static intertface` -- not for __top level__
  * `final` -- for __class__ and __variable__ and __method__
    * `final` is -- *only about the reference itself, and not about the contents of the referenced object*
    * `final class` -- *cannot be extended*
    * `final variable` -- *value is assigned only once, but you can call methods on it*
    * `final method` -- *cannot be overriden by a derived class*
    * __interfaces cannot be marked final__
    * `static` and `final` __nonaccess modifiers together define constants__
      * by convention, constants are UPPER_CASE
  * `synchronized` -- *cant be accessed by more than one thread at a time*
  * `native` -- *calls for methods or libraries from c++ or some other language*
  * `strictfp` -- *Makes sure that float calculations are same on all platforms*
  * `transient` -- *object is not being serialized*
  * `volatile` --*variable can be modified by different threads*
