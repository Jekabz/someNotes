#COLLECTIONS

----
#### Java data structures

###### Enumeration
* Not a data structure
* Enumeration interface defines methods to enumerate (obtain one at a time) the elements on a collection of objects
* Legacy stuff and is superceded by iterator
* methods:
  * `boolean hasMoreElements()`
  * `Object nextElement()` -- *This returns the next object in the enumeration as a generic Object reference.*

```Java
import java.util.Vector;
import java.util.Enumeration;

public class EnumerationTester {

   public static void main(String args[]) {
      Enumeration days;
      Vector dayNames = new Vector();
      dayNames.add("Sunday");
      dayNames.add("Monday");
      dayNames.add("Tuesday");
      dayNames.add("Wednesday");
      dayNames.add("Thursday");
      dayNames.add("Friday");
      dayNames.add("Saturday");
      days = dayNames.elements();
      while (days.hasMoreElements()){
         System.out.println(days.nextElement());
      }
   }
}

```
###### BitSet
* Array that holds bit values
* BitSet can increase in size as needed
* Constructors:
  * BitSet()
  * BitSet(int size)

###### Vector
###### Stack
###### Dictionary
###### Hashtable
###### Properties

----
