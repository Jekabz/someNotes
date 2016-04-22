#SQL INTRO AND DATA TYPES

######Wiew
* `view` -- a subset of a database that an application can process. It may contain parts of one or more tables.
* `Views` are sometimes called `virtual` tables. To the application or the user, views
behave the same as tables. Views, however, have no independent existence. Views allow you to look at data, but views are not part of the data.

######Schema
* `schema` -- structure of an entire database
* `schema` is metadata and as such, is part of the database.

######Domains
* a set of posssable values for a column

######Constraints
* `Constraints` -- rules that determine what values the table attributes can haveth
* prevents entering invalid data in the column

----
* With `SQL` you tell __what__ you want, rather than telling how to get it, `DBMS` does the rest

####SQL Statements
######Data TYPES
* Different implementations, might support Different data types, but these should be there:
  * Numerics
  * Binary
  * Strings
  * Booleans
  * Datetimes
  * Intervals
  * XML
* These types do have subtypes
* there are also collection types and user defined types

######Numerics:
* `Integer`
  * no `fractional` part
  * precision (how many digits can have) depends on `SQL` implementation
* `Smallint`
  * precision <= `integer` precision
* `Bigint`
  * precision >= `integer` precision
* `Numeric`
  * can have fractional component
  * you specify this yourself
  * `scale` is a number of digits in fractional part
  * `precision` includes `scale`
* `Decimal`
  * Similar to `Numeric`
  * Can haveth fractional component
  * You can specify `precision` and `scale`

######Approximate Numerics:
* will not store __exact__ value, but allows for much greater range of values:
  * `Real`
    * single precision floating point number
  * `Double precision`
    * more precision than single precision folating point number
  * `Float`
    * you can specify the precision yourself
    * use this

######Character Strings
* `Character` or `Char`
  * `Char(x)` -- can hold x chars
    * if enters less than x, the rest is padded with blanks
  * `Char` -- can hold 1 char
* `Character Varying` or `Varchar`
  * `VARCHAR (x)` -- holds max of x chars
    * no padding
* `Character Large Object`
  * Use for large character strings
  * restrictions:
    * Not for usage as `PRIMARY KEY`
    * Not for usage as `FOREIGN KEY`
    * Not to be used as `UNIQUE` predicte
    * Can only be compared for equality or inequality

######NATIONAL CHARACTER, NATIONAL CHARACTER VARYING, and NATIONAL CHARACTER LARGE OBJECT data types
* for chars from different alphabet

######Binary Strings
* `Binary`
  * `BINARY (16)` -- holds binary string 16 bytes in length
* `Binary Varying`
  * `Vabinary (x)` -- holds binary string of max lenght of x
* `Binary Large` (BLOB)
  * can store files like images
  * restrictions:
    * Not for usage as `PRIMARY KEY`
    * Not for usage as `FOREIGN KEY`
    * Not to be used as `UNIQUE` predicte
    * Can only be compared for equality or inequality

######Booleans
 * can have `true`, `false` and `unknown`

######Datetimes
* There are 5 of them, depends on implementation
  * `Date`
  * `Time without time zone`
  * `Timestamp without time zone`
  * `Time with time zone`
  * `Timestamp with time zone`

######Intervals
* relate closely to the datetime data types
* diff between two `datetime` values

######XML type

----
####ROW types
* You may never use it

######Collection types
* Two collections may be compared to each other only if they are both the
same type, either ARRAY or MULTISET, and if their element types are comparable

* `Array`
  ```sql
CREATE TABLE CUSTOMER (
  CustID  INTEGER  PRIMARY KEY,
  LastName  CHARACTER VARYING (25),
  Phone  CHARACTER VARYING (15) ARRAY [3] --can store 3 phone numbers
) ;
  ```

* `Multiset`
  * Unordered collection

######REF types
* a *pointer* to something

######User defined types
* data type designed to match with oop host language object type
* gots attributes and methods:
  * `public` -- *available to all users of UDT*
  * `private` -- *available to UDT itself*
  * `protected` -- *available to UDT itself and its subtypes*
* behaves like a __class__
* There are two types of UDT

  *__Distinct types___:
    * Simpler than __Structured types__
    * a single data type
    * constructed from one of the predefined data types, called *source* type
    * Multiple distinct types that are constructed from single source type are not directly comparable - they are `distinct`
    ```sql
    CREATE DISTINCT TYPE USdollar AS DECIMAL (9,2);
    ```
    ```sql
    CREATE TABLE Invoice(
      InvId  INTEGER PRIMARY KEY,
      Total USdollar,
    );
    ```
  *__Structured types__:
    * list of attribute definitions and methods
      * `constors`
        * When creating structured udt, dbms automatically makes a constructor for it, to initialize the udt attributes
      * `mutators` and `observers`
        * `mutator` changes the attribute value
        * `observer` retrieve tha value of attribute
          * you can invoke the `observer` in SELECT to retrieve the value from database
      * `subtypes` and `supertypes`
       * `maximal supertype` -- has no supertype
       * `leaf subtype` -- has no subtypes
    ```sql
CREATE TYPE Foo AS  -- create UDT
Title CHAR(40),     -- attribute
COST  DECIMAL(9,2), -- attribute
NOT FINAL;          -- Allows subtypes

CREATE TYPE Bar UNDER Foo FINAL; -- subtype inherits supertype attributes

CREATE TABLE Foobar(
  Whatever Bar,
  );

BEGIN
  DECLARE a = Bar; -- temp var
  SET a = Bar(); -- calls the constructor
  SET a = a.Title('whatever'); --mutator functionality
  SET a = a.Cost(9.99);
  INSERT INTO Foobar VALUES (a);
END
    ```

* You can also create UDT from `collection` types like arr

####NULL values
* field that does not contain data values
* in Numeric field, null != 0
* in character field, null != ''

####Constraints
* restrictions for data that can be entered in a database table

#### SQL in CLIENT/SERVER System
