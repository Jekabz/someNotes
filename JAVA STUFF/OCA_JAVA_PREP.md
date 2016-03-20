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
