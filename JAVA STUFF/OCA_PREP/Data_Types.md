#DATA TYPES

#### Primitive variables
* Simplest data types
* Java is strongly typed language, apart from JavaScript
* A literal is a fixed value that can be assigned to some variable
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-26%2011:31:59.png)

* `byte`
  * 8 bits
  * –128 to 127, inclusive
* `short`
  * 16 bits
  * –32,768 to 32,767, inclusive
* `int`
  * 32 bits
  * –2,147,483,648 to 2,147,483,647, inclusive
* `long`
  * 64 bits
  * –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807, inclusive
* `float`
* `double`
* `char`
* `boolean`
  * `boolean switch = true;`
  * __true__ or __false__, nothing else

----
###### whole numbers
* You can assign integer literals in different  numberic systems:
* This works with byte, short, int and long
 * `int decVal = 267;`
 * `int octVal = 0413;` -- __0__ (null)
 * `int hexVal = 0x10B;` -- __0x__
 * `int binVal = 0b100001011;` -- __0b__

* since Java 7, you can add `_` for readability, but not after letters:
  * `long value = 0b0_1001;` -- *valid*
  * `long value = 0b_0_101;` -- *invalid*
  * `long value = 0_b0_101;` -- *invalid*
  * `long value = _0120010;` -- *invalid*
  * `long value = 0120010_;` -- *invalid*
  * `long value = 012100_L;` -- *invalid*
  * `int i = Integer.parseInt("46_54");` -- *fails at runtime*
* By default, System.out.println() will print out a number in its decimal base.

----
###### floating point numbers
`float a = 10.0f;` -- *correct*
###### chars

`char char = 'D';`-- *assignment uses single quotes*
* Double quotes are for string
* `char char = 122;` -- *valid, will assign ASCII char by number*
* `char char = '\u0122';` -- *valid, assigns chars by unicode*
* __char__ values are all positive, but you can cast negative number to char
* __char__ can be manipulated by arithmetic operators, because that is just a number

----
###### identifiers
* unlimited (?) length
* starts with letter, currency sign, or _
* can have currency signs, but no special chars
* can have digits, but not at the beginning
* hyphen `-` is not allowed


###### object reference variables
* objects are instances of classes
* reference type is a variable name that "points" to memory adress where an object resides
* object reference is like a a handle that allows the access to object
* references can point to null
* objects can have no references, but they will get killed by garbage man
* several reference variables can point to one object
* to compare referred object, use `equals()`

###### reference variables VS primitive variables
* reference variables hold address of an object, but primitive type holds data
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-26%2017:43:11.png)

###### operators
* only by casting can you assign bigger type to smaller tipe
```java
long foo= 10;
int bar = (int)foo;
```
###### arithmetic operators
* `10.0/6=1.66`
* `10.0/6.0=1.66`
* `10/6.0=1.66`
* `10.0%6.0=4.0`
```java
    int a = 10;
		int b = 10;
		a = ++a + a + --a- --a + a++; //32
		b = 10 + 11 + 11 - 10 + 9 +1;  //32
```

----
###### relational operators
* The operators < , <= , > , and >= work with all types of numbers, both integers (includ-ing char ) and floating point

###### logical operators
* && AND || ARE SHORT - CIRCUIT OPERATORS
* real world application - check if reference variable has value and only then invoke method on it:
```java
String name = "hello";
if (name != null && name.length() > 0){
    System.out.println(name.toUpperCase());
}
```
###### operator precedence
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-03-26%2020:22:05.png)
