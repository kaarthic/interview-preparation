<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## C++ Interview Questions

* **Define structured programming.**  
Structured programming techniques use functions or subroutines to organize the programming code. The programming purpose is broken into smaller pieces and organized together using function. This technique provides cleaner code and simplifies maintaining the program. Each function has its own identity and isolated from other, thus change in one function doesn't affect other.

* **Explain Object oriented programming.**  
Object oriented programming uses objects to design applications. This technique is designed to isolate data. The data and the functions that operate on the data are combined into single unit. This unit is called an object. Each object can have properties and member functions. You can call member function to access data of an object. It is based on several techniques like encapsulation, modularity, polymorphism, and inheritance.

* **List down elements of an object oriented language.**  
	* **Class**  
		A class is a user defined data type. It serves as a template of the objects. You can define structure and behavior of an object using class. It includes data and the member functions that operate on data.

	* **Inheritance**  
		Inheritance enables a new class to reuse the state and behavior of old class. The new class inherits properties and methods from the old class and is called as derived class and the old class is called as base class. The methods thus inherited can be extended using overriding facility of C++.

	* **Encapsulation**  
		The wrapping up of data and member function into an object is called encapsulation. The data is not accessible to the outside world and only those functions which are wrapped into the object can access it. An encapsulated objects act as a "black box" for other parts of the program which interact with it. They provide a service, but the calling objects do not need to know the details how the service is accomplished.

	* **Polymorphism**  
		Polymorphism enables one common interface for many implementations that allows objects to act differently under different circumstances. You can also achieve polymorphism in C++ by function overloading, operator overloading and implementation inheritance.

* **What is function prototype in C++?**  
A function prototype is a declaration of a function that omits the function body. It specifies the function's name, argument types and return type. E.g. int add(int, int)

* **What are the ways to comment statement in C++?**  
C++ supports two types of comments.  
/* */ is used for commenting a block of code.  
// is used for single line comments.

* **Define Structure in C++.**  
The C++ programming technique allows defining user defined datatypes through structure. The syntax to declare structure is as follows:

```
struct student {
	char name[100]
	char address[250]
};
```

* **Explain typecasting.**  
Typecasting enables data type conversion. C++ supports implicit conversions and explicit conversion. Implicit conversions automatically performed when a value is copied to a compatible type. If there is an operation between an int and a float, the int is promoted to float before performing operation automatically by the compiler.  
You can cast explicitly as follows.

```
int i, j, k;
k = i * long(j);
```

* **Define void pointer using C++.**  
In C++, void represents the absence of type, so void pointers are pointers that point to a value that has no type. The void pointers can point to any data type.
You can declare void pointer as follows.

```
void *p;
```

* **When do you use :: Operator in C++?**  
:: is the scope resolution operator. When local variable and global variable are having same name, local variable gets the priority. C++ allows flexibility of accessing both the variables through a scope resolution operator.

* **Define reference variable in C++.**  
A reference variable is just like pointer with few differences. It is declared using & operator. A reference variable must always be initialized. The reference variable once defined to refer to a variable can't be changed to point to other variable. You can't create an array of references the way it is possible with pointer.

* **What is const qualifier?**  
const qualifier is used to specify the variable that can't be change throughout the program. Variables with const qualifier are often named in uppercase.

* ￼**When do you use bool data type?**  
The bool data type can take only two values true or false.

* **What is function overloading in C++?**  
You can have multiple functions with same name using function overloading facility of C++. You can use same name for multiple functions when all these functions are doing same thing.

* **What is operator overloading in C++?**  
With this facility in C++, you can give additional meaning to operators.

* **Define Inline Function.**  
When the function is defined Inline, the C++ compiler puts the function body inside the calling function. You can define function as Inline when the function body is small and need to be called many times, thus reduces the overhead in calling a function like passing values, passing control, returning values, returning control.

* **Define class using C++.**  
A class holds the data and functions that operate on the data. It serves as the template of an object.

* **Explain constructors and destructors.**
	* **Constructors** are the member functions of the class that executes automatically whenever an object is created. Constructors have the same name as the class. Constructors initialize the class. Constructors canít have return type.  
	* **Destructors** are called when the objects are destroyed.
Destructors are usually used to deallocate memory and do other cleanup for a class object and its class members when the object is destroyed. A destructor is called for a class object when that object passes out of scope or is explicitly deleted. A destructor takes no arguments and has no return type.

* **When do you use this pointer?**  
'this pointer' is used as a pointer to the class object instance by the member function. The address of the class instance is passed as an implicit parameter to the member functions.

* **What is new and delete operator?**  
In C++, when you want dynamic memory, you can use operator new. It returns a pointer to the beginning of the new block of memory allocated.
When memory allocated by new operator is no longer required, it is freed using operator delete.

* **Explain the difference between structures and classes.**  
Syntactically and functionally, both structures and classes are identical. By default, members of structures have public accessibility and public inheritance from their parent(s), while members of classes are private and inherit privately from their parent(s).

* **Define local class in C++.**  
Local class is define within the scope of a function and nested within a function. E.g.

```
int func1() {
	class localclass1 {
	};
}
```

* **Explain container class and its types in C++.**  
A container stores many entities and provide sequential or direct access to them. List, vector and strings are such containers in standard template library. The string class is a container that holds chars. All container classes access the contained elements safely and efficiently by using iterators. Container class is a class that hold group of same or mixed objects in memory. It can be heterogeneous and homogeneous. Heterogeneous container class can hold mixed objects in memory whereas when it is holding same objects, it is called as homogeneous container class.

* **Define an Iterator class.**  
A container class hold group of objects and iterator class is used to traverse through the objects maintained by a container class. The iterator class provides access to the classes inside a container. They are objects that point to other objects. Iterator points to one element in a range, and then it is possible to increment it so that it points to the next element.  
There are several different types of iterators:  
	&nbsp;&nbsp;&nbsp;input_iterator  
	&nbsp;&nbsp;&nbsp;output_iterator  
	&nbsp;&nbsp;&nbsp;forward_iterator  
	&nbsp;&nbsp;&nbsp;bidirectional_iterator  
	&nbsp;&nbsp;&nbsp;random_iterator  
	&nbsp;&nbsp;&nbsp;reverse_iterator
	
* **Define storage classes in C++.**  
Storage class defined for a variable determines the accessibility and longevity of the variable. The accessibility of the variable relates to the portion of the program that has access to the variable. The longevity of the variable refers to the length of time the variable exists within the program.

* **Auto**  
Automatic variable, also called as local variable and it has scope only within the function block where it is defined.

* **External**  
External variable are defined outside any function and memory is set aside for this type of variable once it is declared and remained until the end of the program. These variables are also called global variables.

* **Static**  
The static automatic variables, as with local variables, are accessible only within the function in which it is defined. Static automatic variables exist until the program ends in the same manner as external variables. In order to maintain value between function calls, the static variable takes its presence.

* **Define namespace in C++.**  
Namespaces groups together entities like classes, objects and functions under a name. Namespaces provide a way to avoid name collisions of variables, types, classes or functions. Namespaces reduces the use of nested class thus reduces the inconvenience of handling nested class.

* **Define access privileges in C++.**  
You have access privileges in C++ such as public, protected and private that helps in encapsulation of data at various level.
	* **Private**  
		If data are declared as private in a class then it is accessible by the member functions of the class where they are declared. The private member functions can be accessed only by the members of the class. By default, any member of the class is considered as private by the C++ compiler, if no specifier is declared for the member.
	* **Public**  
The member functions with public access specifier can be accessed outside of the class. This kind of members is accessed by creating instance of the class.
	* **Protected**  
Protected members are accessible by the class itself and it's sub-classes. The members with protected specifier act exactly like private as long as they are referenced within the class or from the instance of the class. This specifier specially used when you need to use inheritance facility of C++. The protected members become private of a child class in case of private inheritance, public in case of public inheritance, and stay protected in case of protected inheritance.

* **What is the default access level?**  
The access privileges in C++ are private, public and protected. The default access level assigned to members of a class is private. Private members of a class are accessible only within the class and by friends of the class. Protected members are accessible by the class itself and its sub- classes. Public members of a class can be accessed by anyone.

* **Explain friend class in C++.**  
When a class declares another class as its friend, it is giving complete access to all its data and methods including private and protected data and methods to the friend class member methods. Friendship is one way only, which means if A declares B as its friend it does NOT mean that A can access private data of B. It only means that B can access all data of A.

* ￼**What is virtual function?**  
Virtual function is the member function of a class that can be overriden in its derived class. It is declared with virtual keyword. Virtual function call is resolved at run-time (dynamic binding) whereas the non-virtual member functions are resolved at compile time (static binding).

* **What are pure virtual functions?**  
Pure virtual function is the function in the base class with no body. Since no body, you have to add the notation =0 for declaration of the pure virtual function in the base class. The base class with pure virtual function can't be instantiated since there is no definition of the function in the base class. It is necessary for the derived class to override pure virtual function. This type of class with one or more pure virtual function is called abstract class which can't be instantiated, it can only be inherited.

```
class shape {
	public: virtual void draw() = 0;
};
```

* **Define default constructor.**  
Default constructor is the constructor with no arguments or all the arguments has default values.

* **Define abstraction.**  
The process of hiding unnecessary data and exposing essential features is called abstraction. Abstraction is separating the logical properties from implementation details.

* **What is overriding?**  
Defining a function in the derived class with same name as in the parent class is called overriding. In C++, the base class member can be overridden by the derived class function with the same signature as the base class function. Method overriding is used to provide different implementations of a function so that a more specific behavior can be realized.

* **What is copy constructor?**  
A copy constructor is a special type of constructor that is used to create an object as a copy of an existing object. It takes an argument which is a reference to the object to be copied.

* **C++ supports multiple inheritance. What is the "diamond problem" that can occur with multiple inheritance? Give an example.**  
A university has people who are affiliated with it. Some are students, some are faculty members, some are administrators, and so on. So a simple inheritance scheme might have different types of people in different roles, all of whom inherit common "Person" class. The Person class could define abstract `getRole()` method which would then be overridden by its subclasses to return the correct role type.  
But now what happens if we want to model a the role of a Teaching Assistant (TA)? Typically, a TA is both a grad student and a faculty member. This yields the classic diamond problem of multiple inheritance and the resulting ambiguity regarding the TA’s `getRole()` method:

```
// Person
public abstract Role getRole();
// Faculty Member
public Role getRole() {
	return Role.Faculty;
}
// Graduate Student
public Role getRole() {
	return Role.GradStudent;
}
// TA
public Role getRole() {
	return ???
}	
```

	Which `getRole()` implementation should the TA inherit? The simple answer might be to have the TA class override the `getRole()` method and return a newly-defined role called "TA". But that answer is also imperfect as it would hide the fact that a TA is, in face, both a faculty member and a grad student.

* **What will `i` and `j` equal after the code below is executed? Explain your answer.**  

```
int i = 5;
int j = i++;
```

	After the above code executes, `i` will equal 6, but `j` will equal 5.  
When the operators unary increment (`++`) and decrement (`--`) precede a variable, the value of the variable is modified first and then the modified value is used. For example, if we modified the above code snippet to insted say `int j = ++i;`, `i` would be incremented to 6 and `j` would be set to that modified value, so both would end up being equal to 6.  
However, when these two operators follow a variable, the unmodified value of the variables is used and then it is incremented or decremented.

* **What will the line of code below print out and why?**  

```
cout << 25u - 50;
```
	
	The answer is not -25. Rather, thw answer is 4294967271, assuming 32 bit integers. Why?  
In C++, if the types of two operands differ from one another, then the operand with the "lower type" will be promoted to the type of the "higher type" operand, using the following type of hierarchy (listed here form highest type to lowest type): long, double, float, unsigned long int, long int, unsigned int, int (lowest).  
So when the two operands are, as in our example, `25u` (unsigned int) and `50` (int), the `50` is promoted to also being an unsigned integer (i.e., `50u`).  
Moreover, the result of the operation will be of the type of the operands. Therefore, the result of the above code will itself be an unsigned integer as well. So the result of `-25` converts to `4294967271` when promoted to being an unsigned integer.

* **What is the error in the code below and how should it be corrected?**  

```
my_struct_t *bar;
/* ... */
memset(bar, 0, sizeof(bar));
```
	
	The last argument to `memset` should be `sizeof(*bar)`. `sizeof(bar)` calculates the size of `bar` (i.e., the pointer itself) rather than the size of the structure pointed to by `bar`.  
A sharp candidate might point out that using `*bar` will cause a dereferencing error if `bar` has not been assigned. Therefore an even safer solution would be to use `sizeof(my_struct_t)`.


