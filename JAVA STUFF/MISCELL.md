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
