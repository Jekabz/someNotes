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
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-28%2018:58:53.png)
* `charAt` `indexOf` `subString` `lenght` work exactly like their String counterparts
* `append()`
  * puts the specified value at the end of the existing value
  * overloaded to accept different data types, including arrays: `sb.append(arrName, int inclStartPos, int inclEndPos);`
  * also accepts __Object__, but when sb is printed, it would give `ClassName@hashcode`, because it calls targets toString(), that might not be overriden
* `insert()`
  * also overloaded
  * allows to insert data at a particular position
  ```Java
  class InsertStringBuilder {
    public static void main(String args[]) {
      StringBuilder sb1 = new StringBuilder("Bon");
      sb1.insert(2, 'r');
      System.out.println(sb1); //Born
    }
  }
  ```
  ```Java
    StringBuilder sb1 = new StringBuilder("123");
    char[] name = {'J', 'a', 'v', 'a'};
    sb1.insert(1, name, 1, 3); // after the first index in sb1, insert chars in range from 1(incl) to 3(incl) from name
    System.out.println(sb1); // 1ava23
  ```
* `delete() and deleteCharAt()`
  * delete(int inclusiveStart, int nonInclusiveFin) removes chars in a substring
  * deleteCharAt removes char at a specific position
* `trim()` -- no such method in StringBuilder
* `reverse()` -- 123 -> 321
  * All at once, no reversing for substrings
* `replace()`

  ```Java
  class ReplaceStringBuilder {
    public static void main(String args[]) {
      StringBuilder sb1 = new StringBuilder("0123456");
      sb1.replace(2, 4, "ABCD");
      System.out.println(sb1); //01ABCD456
    }
  }
  ```

  * String.replace() vs StringBuilder.replace()
    ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-28%2020:31:20.png)
* `subSequence()`
  * returns type CharSequence
  ```Java
  StringBuilder sb1 = new StringBuilder("0123456");
  System.out.println(sb1.subSequence(2, 4)); //32
  System.out.println(sb1); //0123456
  ```

----
#### StringBuffer
* StringBuffer methods are only executable by one thread at a time, so possible inconsistencies are avoided at the cost of lower performance
* Otherwise, StringBuffer is same as StringBuilder
* If you need to access your code from multiple threads, use StringBuffer otherwise use StringBuilder

----
### Arrays
* Array is an object
* Arrays can store:
  * primitive data types (stores actual values)
  * objects (stores memory adresses / references)
* Array members are stored in contineous memory locations, thus improving speed

###### Array declaration
* Square brackets can follow type or name or both:
```Java
    int[] arr1Name;
		int arr2Name[];
		int[][] arr3Name;
		int arr4Name[][];
		int []arr5Name[];
```
* Specifying the size at declaration is invalid:
```Java
    //compilation err:
		int[3] arr1Name;
		int arr2Name[1];
		int[8][] arr3Name;
```
* Arr types:
  * primitive data type
  * interfaces
  * abstract classes
  * concrete class (simply not ans abstract one)
  * arr cannot be of type __null__

######Array allocation
* Size of array cannot change once allocated
* keyword `new` is needed, because Arr is an object
```Java
		int[] arr1Name = new int[3];
		int arr2Name[] = new int[3];
		int[][] arr3Name = new int[2][2];
		int arr4Name[][] = new int[2][2] ;
		int []arr5Name[] = new int[2][2];
    int []arr5Name[] = new int[2][]; //this is OK
    int []arr5Name[] = new int[[2];  //this is not OK
```
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-28%2022:45:14.png)
* Once allocated, all the array elements store their default values

###### Array initialization
* Java compiler does not check the rannge of index positions, so this compiles ok:
```Java
int arr[] = new int[2];
char w = 't';
System.out.println(arr[-5]); //compiles ok
System.out.println(arr['D']); //compiles ok
System.out.println(arr[w]); //compiles ok
```
* to access arr positions, you need to pass in char , byte , short , or int

###### declaration, allocation and initialization combo
* `type name[] = {val, val};`
```Java
int intArray[] = new int[]{0, 1};
int intArray[] = {0, 1};

String[] strArray = new String[]{"Summer", "Winter"};
String[] strArray = {"Summer", "Winter"};

int multiArray[][] = new int[][]{ {0, 1}, {3, 4, 5}};
int multiArray[][] = { {0, 1}, {3, 4, 5} };
```
* Size of array does not need and cannot be specified, its calculated by input

```Java
//valid:
int intArray[];
intArray = new int[]{0, 1};

//not valid:
int intArray[];
intArray = {0, 1};
```

###### asymmetrical multidimensional arrays
###### interface, abstract class and class arrays
* __interface array__
  * Array of classes that implement the same interface:
  ```Java
interface MyInterface {}
class MyClass1 implements MyInterface {}
class MyClass2 implements MyInterface {}
class Test {
MyInterface[] interfaceArray = new MyInterface[]
  {
    new MyClass1(),
    null, // null is allowed
    new MyClass2()
  };
}
  ```

* __abstract class array__
  * Array of classes that extends the same abstract class:
  ```Java
abstract class Vehicle{}
class Car extends Vehicle {}
class Bus extends Vehicle {}
class Test {
Vehicle[] vehicleArray = {
  new Car(),
  new Bus(),
  null}; //null is allowed
}
```

* __object array__
  * Any class in Java extends java.lang.Object, so Object arr can have any class in it:

```Java
    interface MyInterface {}
    class MyClass1 implements MyInterface {}
    abstract class Vehicle{}
    class Car extends Vehicle {}
    class Test {
       Object[] objArray = new Object[] {
          new MyClass1(),
          null, // null is valid
          new Car(),
          new java.util.Date(),
          new String("name"),
          new Integer [7] // Other arrays are valid
        };
    }
```
![pic]()

###### Members of an array
*
