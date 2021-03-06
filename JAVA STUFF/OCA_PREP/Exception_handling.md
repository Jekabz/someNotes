# Exception handling
###### Exceptions have to be handled seperately
* basically use try with multiple catch blocks to preserve the code readability
  * this way, exception handlers are defined seperately.
* you can pinpoint the offending code by providing the stack trace
  * stack trace works with both handled and unhandled Exceptions
* You can make a custom exception by extending Exception or any of its subclasses

#### What happens when an exception is thrown?
* normal flow of program is disrupted
* an exception is an object
  * all types of exceptions subclass `java.lang.Throwable` and at runtime the most appropriate subtype is created.
  * exception is initialized with some info and passed to JVM
  * JVM then looks for code through tracked method calls, that can handle this exception (passes the exception back through execution history until it hits main())

###### try cach finally
```java
try{
  // Try to execute your code
}
catch(exceptionType){
  // handle the exception
}
finally{
  // Some code that will always execute
}
```
* methods throw exceptions
```java
void methodName() throws someException{ //when calling this method, you need an exception handler!
  if(true) throw new someException;
}
```

* When calling a method that can throw __checked exception__(do not extend *RuntymException*), enclose it with try block. Catch blocks then have to handle all the checked exceptions

----
* `finally` block is for cleanup code, it can, for example, close database connections and release other resources
* `finally` block will execute even if catch block defines __return__
* `finally` will not execute, if app is terminated by catch or if jvm runs into a fatal error
* if both catch and finally has returns, the calling method receives return from the finally block!
* if catch block returns a primitive value, finally cannot modify it!
* if catch block returns a reference variable, finally block can modify the return by catch!
* finally will always execute, even if no exception is thrown

###### order of exceptions caught
* for unrelated (no inheritance) classes, order does not matter!
* for related classes, order does matter!
  * derived class exceptions first, base class exceptions after, because otherwise the derived class exception can never be reached

###### you can re-throw an exception;
```java
import java.io.*;
public class ReThrowException {
  FileInputStream soccer;
  public void myMethod() throws FileNotFoundException{ //exception is thrown
    try {
      soccer = new FileInputStream("soccer.txt");
    }
      catch (FileNotFoundException fnfe) {
      throw fnfe;
    }
  }
}
```
* this will not work with runtime exceptions, because it must not be caught or thrown

###### methods that throw a checked exception vs methods that handle the exception
* If method dont wish to handle the checked exception, it can throw it using the throws clause in its statement
* method must either catch the exception or rethrow it to its caller

###### nested try-catch
* you can do that

----
#### exception types
* exceptions:
  * Runtime exception
    * do not catch them
  * Checked exception
  * error

![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-02%2015:02:47.png)
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/classjava_1_1lang_1_1Throwable__inherit__graph.png)
* Anything that is a subclass of Exception except for RuntimeException and its subclasses is a __checked exception__.


###### checked exception
* Checked exception is an unacceptable condition that is __foreseen__ by the author of the method, but is outside of control, like file not found.
* if a method that uses another method that may throw a checked exception, you need to make shure that:
  * method is enclosed in try-catch __or__
  * method specifies this exception to be thrown in its method signature

###### runtime exception aka unchecked exception
* Runtime exception is a representation of a programming error
* Runtime exception can not be a part of method signature
* Runtime exceptions can be caught

###### errors
* serious exception thrown by JVM
* needs not be a part of method signature, errors are not needed to be caught
* can be caught by an exception handler:
```java
try{
  myMethod();
}
catch (StackOverflowError s){
  // do something
}
```

#### common exception classes and categories

* ArrayIndexOutOfBoundsException and IndexOutOfBoundsException
  * When you try to access an invalid array position, ArrayIndexOutOfBoundsException is thrown
  * When you try to access an invalid ArrayListposition, IndexOutOfBoundsException is thrown.
* ClassCastException
  * ClassCastException is thrown when an object fails an IS-A test with the class type to which it’s being cast
  * You can use the instanceof operator to verify whether an object can be cast to another class before casting it
* IllegalArgumentException
  * ArgumentException is thrown to specify that a method has passed illegal or inappropriate arguments
* IllegalStateException
  * As an author of code, you can throw IllegalStateException to signal to the calling method that the method being requested for execution can’t be called for the current state of an object.
* NullPointerException
  * This exception is thrown by the JVM if you try to access a method or a variable with a null value
* NumberFormatException
  * fails to convert from String to number
* ExceptionInInitializerError
* StackOverflowError
* NoClassDefFoundError
  * Not a coding issue, check your classpath
* OutOfMemoryError
  * Runs out of __heap__ memory, can make no new objects

----
