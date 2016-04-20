#INTERFACES
* Specifies __what__ classes should do, without telling them __how__
* All methods of an interface are automatically `public`
* `interface` cannot have instance fields
* `interface` can have constants defined in them, thwy are the automatically `public static final`
* Since Java SE 8, you can implement methods in interface
* WHen implementing a method from an Iterface, you have to declare it as `public`
* you can refer to objects by their interface type variables<;
```Java
class Foo implements Bar{}
Bar x = new Foo();
```

----
* AS OF java 8, you can add `static` methods to interfaces
* Before, `static` methods were put in something called companion classes

###### Default Methods
* You can supply a `default` implementation for any `interface` method
```java
public interface Foo<T>{
  default int foo(T other){return 0;}
}
```
* this allows to provide implementation only to methods that are needed, because default methods need not be implemented

----
######What if method with the same name is declared in an interface and a superclass or another interface?
* superclass wins, not really
* with interfaces, you must resolve the conflict by overriding that method, `default` or not, it does not matter:
```Java
interface Named
{
default String getName() { return getClass().getName() + "_" + hashCode(); }
}

class Student implements Person, Named
{
//Overrides
public String getName() { return Person.super.getName(); }

}
