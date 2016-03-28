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
 ![pic]()
 ![pic]()
