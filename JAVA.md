#JAVA
* Compiled bytecode can run on any JVM, reghardless of computer architecture
* JVM translates bytecode to platforms's machine language
* Everything is an object, except for primitive data types

###### JAVA BYTECODE

* Does not directly support floating point operations beyond 32bits
* Bytecode has a lot of goto's in it
* There are several compilers that translate Java code to bitecode, beyont hte standart `javac`
* `GNU Compiler for Java` directly compiles Java source to machine instructions
* Platform independent

###### JVM

* Virtual computer
* Catches common programming errors, like going past the end of array or using null pointer
* Before executing, JVM verifies the bytecode:
  * Branches are always to valid locations
  * Datas is initialized and references are type - safe
  * Access to `private` or `package private` data and methods is rigidly controlled
* How bytecode interpreter and just in time compiler are implemented, depends on JVM implementation
* Each Java process is run in its own sandbox and, by default, cant interact with other java apps
* Finds and loads classes lazily

###### CLASSPATH	

* Specifies location of user-defined classes and packages, used by JVM or javac
* Default value is current folder

###### JAVA BYTECODE INTERPRETER

* For each hardware architecture, different Java bytecode interpreter is needed
* Code execution by java bytecode interpreter is always slower than execution of the same programm compiled in native machine language

###### JUST IN TIME COMPILER

* Translates Java bytecode in native machine language while running the programm
* Faster than interpreter
* This technique is applied to parts of programm that are frequently executed

###### JAVA APPLETS

* runs in rectangle region in browser
* Browser support will end very soon
 
###### JDK

* Implementation of either  `Java SE`, `Java EE`, or `Java ME` platforms
* software development kit, has tools like:
  * javac
  * javadoc
  * jar
  * others
* It gots JRE with extra compinnents in it

###### MEMORY MANAGEMENT

* gots garbage collector
* garbage collection can happen at any time
* no pointer arithmetics
* There are several types of garbage collectors

###### SWING

* gui library for Java SE
* Swing components are not implemented by platform-specific code, therefore they are called **lightweiht**
* Will be replaced by JavaFX

###### GENERICS
* generics:

```java
List<String> v = new ArrayList<>();
v.add("test");
Integer i = v.get(0); // (type error)  compilation-time error
```
* no generics

```java
List v = new ArrayList();
v.add("test");
Integer i = (Integer)v.get(0); // Run time error
```
###### MANIFEST FILE

* Contains metadata for a group of accompanying files
* Jar has .mf file, it can specify entry point in a programm and file has values

###### JAR

* Aggregates many Java .class files and metadata and resources (text, images). .mf file often needs to be first, if the programm is executable
* .jar files are archive files, built on top of .zip file format

###### JAVA KEYWORDS

* variable, that is defined with constant value, uses `final` keyword

```java
final int a;
//by convention, constant names are written in capital letters
final int HEAD_COUNT = 1;
```
* literals or constants are values that are assigned to variables
* `static` modifies variables, methods, code blocks and inner classes
* `static` means that fields and methods belong to the class rather than an instance of the class
* `static` attributes are the same and shared between all objects of the class
* `static` method of class can be accessed just by class name, without creation of class instance
* `static` initialization blocks contain code that is only run once and can initialize static variables

###### TYPE CASTING

* Value can be casted, if number of bytes of type value is cast to is larger or equal to the number of bytes for current type
* Booleans cannot be casted to any other primitive type

###### REFERENCE VARIABLES

* Object variables are reference variables
* When variable of costum object is defined, reference variable is created which points to null
* When object is created, reference refers (points) to the place in memory, where object is created

```java
String user = new String("user");
```
* `user` is reference to object which contains string "user"
* reference variables store adress to the object

###### PRIMITIVE TYPES

* A primitive-type variable can store exactly one value of its declared type at a time
* Primitive-type instance variables are initialized by default. Variables of types byt e, char, short, int, long , float and double are initialized to 0 . Variables of type boolean are initialized to false

###### REFERENCE TYPES

* All nonprimitive objects, like classes
* Reference-type variables store the location of an object in the comput-
er’s memory. Such variables refer to objects in the program. The object that’s referenced may contain many instance variables and methods
* A reference to an object is required to invoke an object’s instance methods. A primitive-type variable does not refer to an object and therefore cannot be used to invoke a method.

###### JAVA POINTERS

* Java has pointers in form of references, they store memory adress of object
* References allow to access the members and methods of the pointed to object
* References do not grand access to memory location of object
* No pointer arithmetics

###### RUNNING JAVA PROGRAMMS

```
javac programmname.java
java programmname
```
* adding .class to programmname returns an error

###### JAVA CLASSES

* Public class must be placed in a file with the same public class name .java
* `public static voind main(String[] args){} ` is a method not a class
* `()` after name means that it is a method
Classname.java:
```java
public class Classname{
    //code...
}

###### DISPLAY FORMATTED TEXT IN STANDART OUTPUT

```java
system.out.printf("%s\n%s\n","Welcome to", "Java Programming!" ); //adds newline
```

###### GET USER INPUT

```java
import java.uti.Scanner;

public class Foo{
    public void main(String[] args){
        int number;
        Scanner inputScanner = new Scanner(Sistem.in);
        number = input
    }
}
```

###### IMPORTING JAVA CLASSES

* By default, `java.lang` is imported in every java programm and so there is no need for seperate import declaration

###### MAIN METHOD

* Any class can contain main() method. JVM only invokes main() that is in the class used to execute the application 
* Main() is **static**, because this lets JVM to invoke main without creating an instance of the class

###### PACKAGE

* Classes that are compiled in the same dir. A class in package is implicitly imported in other classes of package, so import declaration is not needed

###### LOCAL VARIABLES 

* Variables declared in a body of a method
* When method terminates, variable is lost

###### CLASS CONSTRUCTORS

* An important difference between constructors and methods is that constructors
cannot return values, so they cannot specify a return type (not even void ). Normally, con-
structors are declared public
* Keyword new requests memory from the system to store an object, then calls the corresponding class’s constructor to initialize the object.

------------------
###### STATIC METHODS

* Define frequently used tasks
* Static methods in the same class can call each other directly
* Static method from another class is called like this:

```java
classname.methodname(arg);
```
-----------------
###### OPEN GIT PROJECTS IN ECLIPSE

* `file/import/projects from git (with smart import)/...` -- *imports default project in eclipse*
* to convert default project to java project, add these sections to `.project` file in working dir:
```xml
<buildSpec>
    <buildCommand>
        <name>org.eclipse.jdt.core.javabuilder</name>
        <arguments>
        </arguments>
    </buildCommand>
</buildSpec>
<natures>
    <nature>org.eclipse.jdt.core.javanature</nature>
</natures>
```
* configure build path, add libraries
* *before adding jar files in build path, directories in package explorer are shown as packages*
* *after adding jar files in build path, directories in package explorer appear as normal*

--------------------------
###### @Override

* If a class inherits a method from its super class, then there is a chance to override the method provided that it is not marked final.

---------------------------
###### INTERFACE

* Interface is a group of related methods with empty dodies
```java
interface Bicycle {
    void speedUp(int increment);
    void applyBrakes(int decrement);
}
```
* To implement an interface, do like this:

``` java
class MyBicycle implements Bicycle {
    int speed = 0;
    int gear = 1;

   // The compiler will now require that methods
   // speedUp, and applyBrakes
   // all be implemented. Compilation will fail if those
   // methods are missing from this class.

    void changeGear(int newValue) {
         gear = newValue;
    }

    void speedUp(int increment) {
         speed = speed + increment;   
    }

    void applyBrakes(int decrement) {
         speed = speed - decrement;
    }
}
```
