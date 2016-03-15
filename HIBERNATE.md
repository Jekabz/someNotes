# HIBERNATE FRAMEWORK

* Framework for mapping object oriented domain to relational database
* Maps Java classes to database tables
* Maps from Java data types to SQL data types
* Generates SQL calls and handles object conversion of the result set

---------------------------------------------
#### MAPPING (from java classes to database tables)

* Configuration stored in xml or java annotations
* Objects in a front-end application follow OOP principles, while objects in the back-end follow database normalization principles, resulting in different representation requirements. This problem is called `object-relational impedance mismatch`. Mapping is a way of resolving the object-relational impedance mismatch problem.

* Hibernate maps Java classes to database tables and from Java data types to SQL data types

-----------------------------------------------
#### HIBERNATE ADVANTAGES:

* Hibernate takes care of mapping Java classes to database tables using only XML files
* Provides simple APIs for storing and retrieving Java objects directly to and from the database.
* If there is change in Database or in any table then the only need to change XML file properties.
* Abstract away the unfamiliar SQL types and provide us to work around familiar Java Objects.
* Hibernate does not require an application server to operate.
* Manipulates Complex associations of objects of your database.
* Minimize database access with smart fetching strategies.
* Provides Simple querying of data.

------------------------------------------------
#### HIBERNATE APPLICATION ARCHITECTURE:

###### SOME CORE CLASSES:

* Configuration Object
  * First object to be created in any Hibernate app, created only once during initialization
  * Has config files for db connection -- *hibernate.properties* and *hibernate.cfg.xml*
  * Has Class Mapping Setup -- makes connection between Java classes and db tables

* SessionFactory Object
  * Created by abovementioned SessionFactory object
  * Used by all threads in app
  * Heavy object, so it is created during app startup and kept for later use
  * One SessionFactory object per DB
  
* Session Object
  * gets physical connection with a DB
  * Lightweight object and is instantiated each time an interaction with DB is needed
  * Not thread safe, so should not be kept open for a long time. 
  * Meant to be created and destroyed as needed

* Transaction Object
  * Represents a unit of work with DB
  * This object is optional
 
* Query Object
  * Use `Hivbernate Query Language` string to interact with DB
 
* Criteria Object
  * ??
  
 ----------------------------


