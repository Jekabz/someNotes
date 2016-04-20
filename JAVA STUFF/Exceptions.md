#Exceptions
* Constructors can also throw exceptions
* overriden supperclass method throw more general exceptions, it also cannot throw any exceptions if the supperclass method does not

----
* Throwing an exception is easy if one of the existing exception classes works for you:
  * Find an appropriate exception class.
  * Make an object of that class.
  * Throw it.
* Once a method throws an exception, it does not return to its caller.

----
#### Catching Exceptions
```Java
try{
  //code
}
catch(Exception e){
  //code
}
```
* Often the best choice is just to `throw` the exception to the caller
* Do catch those exceptions that you know how to handle
* As of Java SE7, you can catch multiple exception types in the same `catch` clause:
```Java
try{
  //code
}
catch(oneEcption | anotherException){ //needed when Catching exception types that are not subclasses of one another.

}
```

----
* You can throw an exception in a catch clause, typically when you want to change the exception type:
```Java
try
{
access the database
}
catch (SQLException e)
{
Throwable se = new ServletException("database error");
se.initCause(e);
throw se;
}
```

----
######Finally
```java
InputStream in = new FileInputStream(...);
try{
  //code
}
catch{    //optional
  //code  //optional
}         //optional
finally{
  in.close;
}
```
* `finally` can yield unexpected result if gots `return`, it will mask whatever `return` there was in the `try` blocks

######The Try-with-Resources Statement
######Stack Trace Elements
######Tips for Using Exceptions
* Exception handling is not supposed to replace a simple test
  * Use exceptions for exceptional circumstances only.
* Do not micromanage exceptions.
  * wrap the __entire__ task in try block. If one operation fails, you can abandon the task
* Make good use of the exception hierarchy.
  * Do not hesitate to turn an exception into another exception that is more appropriate.
* Do not squelch (mute) exceptions.
* Propagating exceptions is not a sign of shame.
  * Higher-level methods are often better equipped to inform the user of errors or to abandon unsuccessful commands.
