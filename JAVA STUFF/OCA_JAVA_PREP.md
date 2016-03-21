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
```java
interface Controls {
  void changeChannel(int channelNumber);
  void increaseVolume();
  void decreaseVolume();
}
```

###### Single and multiple class definitions in .java file:
* in one .java file, you can define:
  * a single class
  * multiple interfaces
  * multiple classes and interfaces
  * multiple classes
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
* These two are quvivalent:
  * `void functionName(String[] stringArrName){}`
  * `void functionName(String ... StringArrName){}`

###### Java arrays
* These two are quvivalent:
  * `type[] name`
  * `type name[]`

