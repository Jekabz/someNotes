#Flow Control

#### switch statement:
* compares variable to multiple values
```java
int val = 4;
switch(val){
  case 1:
    // Do something
    break;
  case 4:
    System.out.println("got it");
    break;
  case 6:
    // Do something
    break;
  default:
    // Do something
    break;
}
```
* The following two code snippets have the same logics:
```java
String day = "SUN";
if (day.equals("MON") || day.equals("TUE")||
  day.equals("WED") || day.equals("THU"))
  System.out.println("Time to work");
else if (day.equals("FRI"))
  System.out.println("Nearing weekend");
else if (day.equals("SAT") || day.equals("SUN"))
  System.out.println("Weekend!");
else
  System.out.println("Invalid day?");

//--------------------------

switch (day) {
  case "MON":
  case "TUE":
  case "WED":
  case "THU": System.out.println("Time to work");
  break;
  case "FRI": System.out.println("Nearing weekend");
  break;
  case "SAT":
  case "SUN": System.out.println("Weekend!");
  break;
  default: System.out.println("Invalid day?");
}
```
###### Arguments passed to switch
* char
* byte
* short
* int
* String

###### limitations for labels:
* needs to be compile time constants, so no variables allowed (final variables are allowed)
```java
final int a = 10;
final int b = 20;
final int c; //defined, but not initialized
c = 30; // initialized later, but does not matter for switch

switch (a) {
case b+c: System.out.println(b+c); break; //compilation error
}
```

* __null__ is not allowed as case label

----

#### For loop
```java
for (initialization; condition; update) {
statements;
}
```
* initialization executes only once, you can initialize multiple variables of the same type
* update executes after code in the body has executed. can have coma seperated statements, executed in order of appearance

###### enhanced for loop
```java
ArrayList myList :
ArrayList<String> myList= new ArrayList<String>();
myList.add("Java");
myList.add("Loop");

// Standard for loop:
for(Iterator<String> i = myList.iterator(); i.hasNext();)
  System.out.println(i.next());

// Enhanced for loop:
for (String val : myList)
  System.out.println(val);
```
* You can read the colon (:) as "in"
```java
for(type<generics>name : collection);
```
* calling methods on enchanced loop variable will change collections info

###### limitations of enhanced for loop
* cant be used to initialize an array and modify its elements
* cant be used to delete or remove the elements of a collection
* cant be used to iterate over multiple collections or arrays in the same loop
* dont use the enhanced for loop to initialize, modify or filer

----
#### While and do while loop
```java
do{

}while(true); //do not forget the semicolon
```

###### break
* When you use the break statement with nested loops, it exits the inner loop.

###### labeled statements
* these types of statements can have labels:
  * a code block {}
  * all loops:
    * for
    * enhanced for
    * while
    * do while
  * if
  * switch
  * expressions
  * Assignments
  * return statements
  * try block
  * throws statement
* example:
```java
String[] programmers = {"Outer", "Inner"};
outer: //label
for (int i = 0; i < programmers.length; i++) {}
```

* no dublicate labels allowed

###### labeled break statements
```java
String[] programmers = {"Outer", "Inner"};
outer:
for (String outer : programmers) {
  for (String inner : programmers) {
    if (inner.equals("Inner"))
      break outer; // exits outer loop !!!
    System.out.print(inner + ":");
  }
}
```

###### labeled contineue statements
```java
String[] programmers = {"Paul", "Shreya", "Selvan", "Harry"};
outer:
for (String name1 : programmers) {
  for (String name : programmers) {
    if (name.equals("Shreya"))
      continue outer; // skips remaining code and start with its next iteration
    System.out.println(name);
  }
}
```

----
