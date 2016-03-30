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
