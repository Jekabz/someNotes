#Lambda Expressions
* `Lambda Expression` is a block of code that you can pass around so it can be executed later, once or several times
* Until SE8, giving someone a block of code hasn’t been easy. You couldn’t
just pass code blocks around. Java is an object-oriented language, so you had to construct an object belonging to a class that has a method with the desired code.
* `lambda` expression is like a method without a name

----
* You never specify the result type of `lambda Expression`, it is concluded from context
```Java
(type parameter, type anotherParameter) ->{
  //if single expression, its value is returned
}
//this is valid if only one parameter:
parameter ->{
  return;
}

()->{
  //code
}
```

----
