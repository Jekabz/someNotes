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
    ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-28%2015:48:26.png)

###### String methods()
* `char charAt()` -- *gives number, returns char at that number, or runtime exception*
* `int indexOf(char x, int startPozitionForSearch)` -- *returns index of first occurance of a char or -1, if no char is found*
* `String substring(int start, int fin)` -- *returns a substring between indexes at start(inclusive) and fin(not inclusive)*
* `String trim()` -- *removes (only) leading and trailing whitespace (within a string, whitespace stays)*
* `String replace(old, new)` -- *replaces old with new. Both parameters must be String or int, both at the same time*
* `int length()` -- *returns int how many chars are in String. Starts counting from 1*
* `boolean startsWith(String startSequence, int startPosition)` -- *true if string from startPosition mach startSequence*
* `boolean endsWith(String endSequence)` -- *true if ... you get it*

###### method chaining()
* this is valid:
```Java
  String foo = "MyString ".replace("My", "Your").trim().concat("Content");
  //YourStringContent
```
* evaluated from left to right

----
#### String objects and operators
* Operators that can be used with String: +, +=, ==, !=
```Java
String foo = 10 + 22 +"Blue"; //32Blue
String bar = "" + 10 + 22 + "Blue"; //1022Blue

String lang = "Java";
lang += " is everywhere!"; //Java is everywhere

String initializedToNull = null;
initializedToNull += "Java"; // nullJava
```

###### determining equality of Strings
* `stringOne.equals(stringTwo);` -- *use this!*
* `stringOne == stringTwo` -- *do not use this!*

----
#### StringBuilder
* package java.lang
* use StringBuilder when dealing with large strings or need to modify the contents of a String often, StringBuilder impruves performance for this

###### StringBuilder class is in fact mutable
* uses non-final char[] to store its value

###### Create StringBuilders
* Has overloaded constructors:
```Java
  StringBuilder sb1 = new StringBuilder(); // no args
  StringBuilder sb2 = new StringBuilder(sb1); // another StringBuilder
  StringBuilder sb3 = new StringBuilder(50); // int
  StringBuilder sb4 = new StringBuilder("foo"); // String
```
* default constructor, a char[16] is created
* String constructor makes char[str.lenght()+16]

###### StringBuilder methods
![pic]()
