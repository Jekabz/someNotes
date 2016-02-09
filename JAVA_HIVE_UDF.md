#JAVA HIVE UDFs AND UDAFs

-----------------------

#### UDFs

* There are 2 interfaces to do this:
  * `org.apache.hadoop.hive.ql.exec.UDF` -- *the simple API for __primitive__ data types*
  * `org.apache.hadoop.hive.ql.udf.generic.GenericUDF` -- *the more complex API for __complex__ data types*

------------------------
#### THE COMPLEX API

* `org.apache.hadoop.hive.ql.udf.generic.GenericUDF` requires to implement 3 methods:
  * `abstract Object evaluate(GenericUDF.DeferredObject[] arguments);` -- *takes args, returns __Writeable__ result. called once for every row of data being processed*
  * `abstract String getDisplayString(String[] children);` -- *returns some string, does not matter*
  * `abstract ObjectInspector initialize(ObjectInspector[] arguments);` -- *used for input validation __passes data to UDF__*
* many functions used in `GenericUDF` return `objects`, therfore type checking might be an issue
* Type checking must be done at runtime

`initialize()` is called first time UDF is invoked, it does:
  * Verifies that the input is of the correct type
  * Set up and return an ObjectInspector of the UDF output type
  * Stores input in class variables
 
`evaluate()` processes the input.
  * gets input from class variables, that were initialized in `initialize()`
 
generic structure:
```java
 public interface GenericUDF {
    public Object evaluate(DeferredObject[] args) throws HiveException;
    public String getDisplayString(String[] args);
    public ObjectInspector initialize(ObjectInspector[] args) throws UDFArgumentException;
  }
```

------------------------
###### WIERD STUFF

* Java object[] is eqvivalent to Hive struct<>
* Java ArrayList<> is eqvivalent to Hive array<>

------------------------

------------------------

### UDF VS UDAF

* `UDF` -- *processes fields in __one__ input row and outputs one value*
* `UDAF` -- *processes fields in __several__ input rows and outputs only one value*

------------------------

------------------------

#### UDAFs

* Computes partial rezsult, because input rows are passsed one after another

-------------------------
-------------------------

#### DEFERREDOBJECT[]

* A Defered Object allows us to do lazy-evaluation and short-circuiting.
* GenericUDF use DeferedObject to pass arguments.
