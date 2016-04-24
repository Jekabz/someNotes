#Building a Multitable Relational Database

######Define objects
* major entity translates to a table, it has attributes - table columns

----
* `collation` is a set of rules that determines how strings in a character set compare to one another. Every character set gots a default `collation`

----
####KEYS
* `KEY` is an attribute that unique identifies a row in a table, ti cannot be __null__

######Primary KEYS
* All tables should have a PK, but can b defined without

```sql
CREATE TABLE Foo(
  Whatever   CHAR(10) PRIMARY KEY,
  Something  CHAR(10)
);
```
* `composite key` a combo of cloumns that quarantee uniquness
```sql
CREATE TABLE Bar(
  Whatever   CHAR(10) NOT NULL,
  Something  CHAR(10) NOT NULL,
  Info       CHAR(10),
  CONSTRAINT myKey PRIMARY KEY
  (Whatever, Something)
);
```
* There can also be tables with a column for which the only purpose is to be the PRIMARY KEY

######FOREIGN KEYS
* Column or Columns in a table that references a PRIMARY KEY in another table
* must not be unique
```sql
CREATE TABLE FooBar(
  Something INTEGER PRIMARY KEY,
  keykey    CHAR(10),
  CONSTRAINT SomethingSome FOREIGN KEY (keykey) REFERENCES Bar (Whatever)
);
```

----
