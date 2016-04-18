#Miscellenious Stuff

----
#####Access to mutable class objects

* `mutable` -- *the object on the heap can be changed from reference*
* `immutable` -- *Immutable means that once the constructor for an object has completed execution that instance can't be altered.*
* if in class you declare a getter method to mutable object, it can be changed by its mutator methods, __breaking__ the encapsulation and making a vulnerable code!

* __What if you need to return a reference to a mutable object?__
  * Clone it:
  ```java
class Employee
{
. . .
public Date getHireDay()
{
return (Date) hireDay.clone(); // Ok
}
. . .
}
```

----
* static constant that you have used many times is System.out . It is declared in the System class as follows:
```java
public class System
{
. . .
public static final PrintStream out = . . .;
. . .
}
```

----
```java
int a;
if(a=1){};
```
* TYPE MISMATCH, cannot convert from int to boolean

----
```java
{
  int a;
  {
    int a; //cannot redefine variable in inner block
  }
}
```

----
* Reading user input:
```java
Scanner scanner = new Scanner(System.in);
String line = scanner.nextLine();
String word = scanner.next();
String number=scanner.nextInt();
```

----
* String comparison:
```java
"Hello".eqalsIgnoreCase("hello");
```
----

#### Method parameters
* __JAVA IS ALWAYS PASS BY COPY!__
* __primitive types__ are passed by value, that means that a __copy__ of a primitive value is made and passed to the method. Whatever method does, it cannot modify the original primitive type value that was passed to it.
* __object references__  - a __copy__ of reference is created, so you can now call a method of the object, that changes its state

----
#### Initializing the data fields in a Class:

* Set the value in constructor
* Assign the value in declaration
* Use initialization block
  * Only runs when an object of that class is constructed
  *  Initialization block runs __before__ constructor!
  ```JAVA
  class Foo{
    private static int nextId;
    private static int id;
    //initialization block:
    {
      id = nextId;
      nextId++;
    }
  }
  ```
  * It is legal to set fields in initialization blocks even if they are only defined later in the class.
  ```java
  class Foo{
    {
      a = 10; //legit
    }
    int a;
  }
  ```
  * class can have multiple initialization blocks, they are then executed in the order of appearance
  * initialization blocks can be marked as `static`:
  ```java
  class Foo{
    static
    {
      a = 10; //legit
    }
    static int a;
  }
  ```  
