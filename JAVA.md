#JAVA
* Compiled bytecode can run on any JVM, reghardless of computer architecture
* JVM translates bytecode to platforms's machine language
* Everything is an object, except for primitive data types

###### JAVA BYTECODE

* Does not directly support floating point operations beyond 32bits
* Bytecode has a lot of goto's in it
* There are several compilers that translate Java code to bitecode, beyont hte standart `javac`
* `GNU Compiler for Java` directly compiles Java source to machine instructions
* Platform independent

###### JVM


* Virtual computer
* Catches common programming errors, like going past the end of array or using null pointer
* Before executing, JVM verifies the bytecode:
  * Branches are always to valid locations
  * Datas is initialized and references are type - safe
  * Access to `private` or `package private` data and methods is rigidly controlled
* How bytecode interpreter and just in time compiler are implemented, depends on JVM implementation

###### JAVA BYTECODE INTERPRETER

* For each hardware architecture, different Java bytecode interpreter is needed
* Code execution by java bytecode interpreter is always slower than execution of the same programm compiled in native machine language

###### JUST IN TIME COMPILER

* Translates Java bytecode in native machine language while running the programm
* Faster than interpreter
* This technique is applied to parts of programm that are frequently executed

###### JAVA APPLETS

* runs in rectangle region in browser
* Browser support will end very soon
 
###### JDK

* Implementation of either  `Java SE`, `Java EE`, or `Java ME` platforms
* software development kit, has tools like:
  * javac
  * javadoc
  * jar
  * others
* It gots JRE with extra compinnents in it

###### MEMORY MANAGEMENT

* gots garbage collector
* garbage collection can happen at any time
* no pointer arithmetics
* There are several types of garbage collectors

###### SWING

* gui library for Java SE
* Swing components are not implemented by platform-specific code, therefore they are called **lightweiht**
* Will be replaced by JavaFX

###### GENERICS


