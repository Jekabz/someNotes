# C++ IW QUESTIONS

* Object is an instance of class

###### inheritance types in c++
  * Single
  * Multilevel
  * Multiple
  * Hierarchical
  * Hybrid

###### what is `protected` access?
* If a class member is protected then it is accessible in the inherited class. However, outside the both the private and protected members are not accessibleIf a class member is protected then it is accessible in the inherited class. However, outside the both the private and protected members are not accessible

###### abstraction vs encapsulation
###### keyword `volatile`
###### What is an inline function?
* A function prefixed with the keyword inline before the function definition is called as inline function. The inline functions are faster in execution when compared to normal functions as the compiler treats inline functions as macros.

###### storage class
 * names:
   * auto
   * static
   * extern
   * register
   * mutable

###### shallow vs deep copy
* Shallow copy does memory dumping bit-by-bit from one object to another. Deep copy is copy field by field from object to another. Deep copy is achieved using copy constructor and or overloading assignment operator.Shallow copy does memory dumping bit-by-bit from one object to another. Deep copy is copy field by field from object to another. Deep copy is achieved using copy constructor and or overloading assignment operator.

###### virtual function
* A virtual function with no function body and assigned with a value zero is called as pure virtual function.

###### What is an abstract class in C++?
###### What is a reference variable in C++?
* alias

###### Explain the static member function.
* A static member function can be invoked using the class name as it exits before class objects comes into existence. It can access only static members of the class.

###### What are/is the operator/operators used to access the class members?
* Dot (.) and Arrow ( -> )Dot (.) and Arrow ( -> )

###### Can we initialize a class/structure member variable as soon as the same is defined?
* No, Defining a class/structure is just a type definition and will not allocated memory for the same.

###### Standard template library

######  Name the default standard streams in C++. Name the default standard streams in C++.
* cin, cout, cerr and clog.

###### When a class member is defined outside the class, which operator can be used to associate the function definition to a particular class?
* Scope resolution operator (::)

######  What is a destructor?
* A destructor is the member function of the class which is having the same name as the class name and prefixed with tilde (~) symbol. It gets executed automatically w.r.t the object as soon as the object loses its scope. It cannot be overloaded and the only form is without the parameters.

######  Can I use malloc() function of C language to allocate dynamic memory in C++?
* Yes, as C is the subset of C++, we can all the functions of C in C++ too.

###### Can I use ‘delete’ operator to release the memory which was allocated using malloc() function of C language?Can I use ‘delete’ operator to release the memory which was allocated using malloc() function of C language?
* No, we need to use free() of C language for the same.

###### What is a friend function?
* A function which is not a member of the class but still can access all the member of the class is called so. To make it happen we need to declare within the required class following the keyword ‘friend’.

###### What is a friend class?
* A class members can gain accessibility over other class member by placing the class declaration prefixed with the keyword ‘friend’ in the destination class.

###### What is a copy constructor?
* A copy constructor is the constructor which take same class object reference as the parameter. It gets automatically invoked as soon as the object is initialized with another object of the same class at the time of its creation.

###### struct vs class
* By default the members of struct are public and by default the members of the class are private.By default the members of struct are public and by default the members of the class are private.

##### What is the role of the file opening mode ios::trunk?
* If the file already exists, its content will be truncated before opening the file.

###### What is a namespace?
###### What is a class template?
######  How can we catch all kind of exceptions in a single catch block?
```C++
catch(…){}
```
###### What is keyword auto for?
###### What is the purpose of extern storage specifier.
* Used to resolve the scope of global symbolUsed to resolve the scope of global symbol

######  When should we use the register storage specifier?
* If a variable is used most frequently then it should be declared using register storage specifier, then possibly the compiler gives CPU register for its storage to speed up the look up of the variable.If a variable is used most frequently then it should be declared using register storage specifier, then possibly the compiler gives CPU register for its storage to speed up the look up of the variable.

###### Where an automatic variable is stored?
* Every local variable by default being an auto variable is stored in stack memoryEvery local variable by default being an auto variable is stored in stack memory

###### What is a container class?
* A class containing at least one member variable of another class type in it is called so

###### What is a token?What is a token?

###### What are the different ways of passing parameters to the functions? Which to use when?
* call by value
* call by address
* call by reference

###### Which operator can be used to determine the size of a data type/class or variable/object?
* sizeof()

######  How can we refer to the global variable if the local and the global variable names are same?
* We can apply scope resolution operator (::) to the for the scope of global variable.

######  What are available mode of inheritance to inherit one class from another?
* public
* private
* protected

###### Are the exceptions and error same?
* No, exceptions can be handled whereas program cannot resolve errors.

###### Which function is used to move the stream pointer for the purpose of reading data from stream?
* seekg()

###### cpp header file
###### What is the order of objects destroyed in the memory?
* The objects are destroyed in the reverse order of their creation.The objects are destroyed in the reverse order of their creation.
