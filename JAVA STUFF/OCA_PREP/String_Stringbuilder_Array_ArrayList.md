# String, StringBuilder, Array, ArrayList

#### String class
* resides in Java.lang package
###### Create string objects
* the `==` compares adresses in two reference Variables
 ```Java
 String string1 = new String("foo");
 String string2 = new String("foo");
 System.out.println(string1 == string2); // false, because string1 is not the same object that string2 is

 String string3 = "bar";
 String string4 = "bar";
 System.out.println (string3 == string4); //true, because both refer to the same object
 ```
 * This is so, because in jvm, there is a `pool` of string objects
 * if no object "bar" can be found in pool, a new "bar" object is created
 * if "bar" can be found, a new reference is made to it instead
 ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-28%2015:12:23.png)
 ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-28%2015:12:35.png)
* String constant pool aka String pool.
* String gots overloaded constructors, so this is valid:
```Java
  String girl = new String("Shreya");
  char[] name = new char[]{'P','a','u','l'};
  String boy = new String(name);

  StringBuilder sd1 = new StringBuilder("String Builder");
  String str5 = new String(sd1);

  StringBuffer sb2 = new StringBuffer("String Buffer");
  String str6 = new String(sb2);
```
###### class String is immutable
* once created, the contents of an object of class String can never be modified
* this helps to reuse String objects for increased performance
* string objects can be shared among multiple reference variables, without fear of change to their values
* How?
  * String class holds a `private final char value[];` of fixed size
  * `final` makes sure that the value is initialized only once
  * methods of `String` do not modify the `char value[]`
    * All methods that seem to modify the contents of String, do in fact make and return a __new__ String object with modified value
    ![pic]()
