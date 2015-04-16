<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## Java Interview Questions

* [**Java Keywords**](#Keywords)
* [**Key Concepts**](#KeyConcepts)
* [**Multithreading**](#Multithreading)
* [**Collections**](#Collections)


### [](id:Keywords)Java Keywords

* **What are the different types of modifiers:**  

| Modifier | Accessible in the same package | Accessible in different package |
|:------------:|:-----:|:----------------------------:|
|	Private		|	No	|	No	|
|	Protected	|	Yes	|	Yes, only if the class extends the main class  |
|	Default		|	Yes	|	No	|
|	Public		|	Yes	|	Yes	|


* **What is the use of final keyword**  
The final keyword can be assigned to
	1. Class level variable
	2. method
	3. class
	4. Objects  

	If a final is assigned to a variable, the variable behaves likes a constant. It means that the value of variable once set cannot be changed.

	```
final int i = 1;
i = 5; // error
	```

	If a final is assigned to a method, then it cannot be overridden in its child class.

	```
class Parent {
	final void print() {
		System.out.println("Inside");
	}
}
class Child extends Parent {
	public final void print() {
		// error cannot override final method
		System.out.println("Inside");
	}
}
	```

	If a class is made final, then no other class can extend it and make it as parent class. E.g. String Class.

	Final objects are instantiated only once.

	```
final Map map = new HashMap();
map.put("key", "value");
map = new HashMap(); // error
	```


* **What is the use of synchronized keyword?**  
This keyword is used to prevent concurrency. Synchronized keyword can be applied to static/non-static methods or a block of code. Only one thread at a time can access synchronized methods and if there are multiple threads trying to access the same method then other threads have to wait for the execution of method by one thread. Synchronized keyword provides a lock on the object and thus prevents race condition.

	```
public void synchronized method() {
	public void synchronized staticmethod() {}
	public void myMethod() {
		synchronized (this) { // synchronized keyword on block of code
		}
	}
}
	```


* **What is volatile keyword?**  
In general each thread has its own copy of variable, such that one thread is not concerned with the value of same variable in the other thread. But sometime this may not be the case. Consider a scenario in which the count variable is holding the number of times a method is called for a given class irrespective of any thread calling, in this case irrespective of thread access the count has to be increased. In this case the count variable is declared as volatile. The copy of volatile variable is stored in the main memory, so every time a thread access the variable even for reading purpose the local copy is updated each time from the main memory. The volatile variable also have performance issues.


* **What is a transient variable?**  
If some of the properties of a class are not required to be serialized then the variables are marked as transient. When an object is deserialized the transient variables retains the default value depending on the type of variable declared and hence lost its original value.


* **What is a strcitfp modifier?**  
Strictfp is used with variable only . It is used to restrict floating point calculations ( fp ) to ensure portability ( platform Independent ). When this modifier is specified, the JVM adheres to the Java specifications ( IEEE-754 floating-point specification ) and returns the consistent value independent of the platform. That is, if you want the answers from your code (which uses floating point values) to be consistent in all platforms, then you need to specify the strictfp modifier.


* **What is a static variable?**  
Static keyword can be used with the variables and methods but not with the class. Anything declared as static is related to class and not objects.  
  
	**Static variable** : Multiples objects of a class shares the same instance of a static variable
	
	```
public class Counter {
	private static int count = 0;
	private int nonStaticCount = 0;  
	public void incrementCounter() {
		count++;
		nonStaticCount++;
	}

	public int getCount() {
		return count;
	}

	public int getNonStaticCount() {
		return nonStaticCount;
	}

	public static void main(String[] args) {
		Counter countObj1 = new Counter();
		Counter countObj2 = new Counter();
		countObj1.incrementCounter();
		countObj1.incrementCounter();
	}
}
	```
	
	```
Output:
Static count for Obj1: 2
NonStatic count for Obj1: 1
Static count for Obj2: 2
NonStatic count for Obj2: 1	
	```
	
		In the above program, obj1 and obj2 share the same instance of static variable count hence if the value is incremented by one object, the incremented value will be reflected across the other objects.
	

* **What is a static method?**  
A method defined as static is called static method. A static method can be accessed without creating the objects. Just by using the Class name the method can be accessed.

	Static method can only access static variables and not local or global non-static variables.
	
	```
public class Test {
	public static void printMe() {
		System.out.println("Hello World");
	}
}
	public class MainClass {
	public static void main(String[] args) {
		Test.printMe();
	}	}
	```
	
	```
Output:
Hello World
	```
	
	Also static method can call only static methods and not non static methods. But non-static methods can call static methods.
	

* **Why static methods cannot access non static variables or methods?**  
A static method cannot access non static variables or methods because static methods can be accessed without instantiating the class, so if the class is not instantiated the variables are not initialized and thus cannot be accessed from a static method.


* **What is static class?**  
A class cannot be declared static. But a class can be said a static class if all the variables and methods of the class are static and the constructor is private. Making the constructor private will prevent the class to be instantiated. So the only possibility to access is using Class name only


* **What is throw keyword?**  
Throw keyword is used to throw the exception manually. It is mainly used when the program fails to satisfy the given condition and it wants to warn the application.The exception thrown should be subclass of Throwable.

	```
public void parent() {
	try {
		child();
	} catch (MyCustomException e) { }
}
public void child {
	String iAmMandatory = null;
	if (iAmMandatory == null) {
		throw (new MyCustomException("exception using throw keyword"));
	}
}
	```
	

* **What is the use of throws keyword?**  
Throws clause is used to throw the exception from a method to the calling method which could decide to handle exception or throw to its calling method in a class.

	```
public void parent)() {
	try {
		child();
	} catch(MyCustomException e) { }
}
public void child throws MyCustomException {
	// put some logic so that the exception occurs
}
	```
	
	
### [](id:KeyConcepts)Key Concepts


* **Why is main() method static?**  
To access a static method class object is not needed. The method can be accessed directly with the help of ClassName. So when a program is started the JVM search for the class with main method and calls it without creating an object of the class.


* **What is the difference between static and instance methods?**  
Instance method belongs to the instance of a class therefore it requires an instance before it can be invoked, whereas static method belongs to the class itself and not to any class instance so it doesn’t need an instance to be invoked.  
Instance methods use dynamic (late) binding, whereas static methods use static (early) binding.  
When the JVM invokes a class instance method, it selects the method to invoke based on the type of the object reference, which is always known at run-time. On the other hand, when the JVM invokes a static method, it selects the method to invoke based on the actual class of the object, which may only be known at compile time.


* **Can static block throw exception?**  
Yes, static block can throw only Runtime exception or can use a try-catch block to catch checked exception.  
Typically scenario will be if JDBC connection is created in static block and it fails then exception can be caught, logged and application can exit. If System.exit() is not done, then application may continue and next time if the class is referred JVM will throw NoClassDefFounderror since the class was not loaded by the Classloader.


* **What is the difference between abstract class and interface?**

	| Abstract | Interface |
	|:--------:|:---------:|
	| Contains at least one abstract method. | Can only contain only abstract methods. |
	| Can have `public`, `private`, `protected` or default variables and also constants. | Variable is by default `public final`. |
	| A class can extend only 1 abstract class | A class can implement multiple interfaces. |
	| Not compulsory to implement all methods when extended. | Compulsory to implement all methods when implemented. |
	| Can simply implement a new method. | If new implementation is added, all classes need to implement the interface. |
	

* **Explain with example to describe when to use abstract class and interface.**  
Consider a scenario where all Cars will have 4 tires and other features can be different.
In this case any subclass of Car has to have 4 tires. This is a case where abstract class will be used and a default implementation for tires will be provided.

	```
public abstract class Car {
	private final static TOTAL_TIRES = 4;
	public abstract String getCarName();
	public final int getNoOfTires() {
		return TOTAL_TIRES;
	}
}
	```
	
	Consider a scenario where Cars can have any number of tires and other features can also be different. In this case interface will be created.
	
	```
public interface Car {
	public abstract String getCarName();
	public abstract int getNoOfTyres();
}
	```
	
	
* **Does Java support multiple inheritance? Why?**  
Java doesn't support multiple inheritance but it provide a way through which it can enact it. Consider the scenario is C++:

	```
Class A {
	public void add() {
		// some text
	}
}
Class B {
	public void add() {
		// some text
	}
}
Class C extends A, B {
	public static void main(String[] args) {
		C objC = new C();
		objC.add(); // compiler gets confused
	}
}
	```
	
	This is called the **Diamond Problem**.
	
	This problem in Java is taken care with the use of interfaces.
	In Java, similar problem would look like:
	
	```
interface A {
	add();
}
interface B {
	add();
}
class C implements A, B {
	add() {
		// doesn't matter which interface it belongs to
	}
}
	```
	

* **Can `this` keyword be assigned null value?**  
No


* **What are the different types of references in Java?**  
A normal reference in Java is known as a strong reference. The java.lang.ref package defines three other types of references—soft, weak and phantom references. Each type of reference is designed for a specific use.

	A **SoftReference** can be used to implement a cache. An object that is not reachable by a strong reference (that is, not strongly reachable) but is referenced by a soft reference is called softly reachable. A softly reachable object may be garbage collected at the discretion of the garbage collector. This generally means that softly reachable objects will only be garbage collected when free memory is low, but again, it is at the discretion of the garbage collector. Semantically, a soft reference means **"keep this object unless the memory is needed."**
	
	A **WeakReference** is used to implement weak maps. An object that is not strongly or softly reachable, but is referenced by a weak reference is called weakly reachable. A weakly reachable object will be garbage collected during the next collection cycle. This behavior is used in the class java.util.WeakHashMap. A weak map allows the programmer to put key/value pairs in the map and not worry about the objects taking up memory when the key is no longer reachable anywhere else. Another possible application of weak references is the string intern pool. Semantically, a weak reference means **"get rid of this object when nothing else references it."**
	
	A **PhantomReference** is used to reference objects that have been marked for garbage collection and have been finalized, but have not yet been reclaimed. An object that is not strongly, softly or weakly reachable, but is referenced by a phantom reference is called phantom reachable. This allows for more flexible cleanup than is possible with the finalization mechanism alone. Semantically, a phantom reference means **"this object is no longer needed and has been finalized in preparation for being collected."**
	

* **How to change the heap size of a JVM?**  
The old generation's default heap size can be overridden by using the -Xms and -Xmx switches to specify the initial and maximum sizes respectively:  
	java -Xms 'initial size' -Xmx 'maximum size' program
	
	Example:  

	```
java -Xms64m -Xmx128m program
	```

* **What is the difference between instaneof and isInstance(Object obj)?**  

	| instanceof | isInstance(Object obj) |
	|:----------:|:----------------------:|
	| Reserved word for Java | method of java.lang.Class |
	| Used to check whether the object is type of a particular class or its subclass | Used to identify object of a particular class |
	

* **Java supports pass by value or pass by reference?**  
Java supports only pass by value. The arguments passed as a parameter to a method is mainly primitive data types or objects. For the data type the actual value is passed.  
Java passes the references by value just like any other parameter. The pointer to the object is passed as value. Thus, method manipulation will alter the objects, since the references point to the original object but will not initialize the new object. Consider the example:

	```
public void tricky(Point arg1, Point arg2) {
	arg1.x = 100;
	arg1.y = 100;
	Point temp = arg1;
	arg1 = arg2;
	arg2 = temp;
}
public static void main(String[] args) {
	Point point1 = new Point(0, 0);
	Point point2 = new Point(0, 0);
	System.out.println("X: " + point1.x + " Y: " + point1.y);
	System.out.println("X: " + point2.x + " Y: " + point2.y);
	tricky(point1, point2);
	System.out.println("X: " + point1.x + " Y: " + point1.y);
	System.out.println("X: " + point2.x + " Y: " + point2.y);	
}
	```
	
	```
Output:
X: 0 Y: 0
X: 0 Y: 0
X: 100 Y: 100
X: 0 Y: 0
	```
	
	The method successfully alters the value of point1, even though it is passed by value; however, a swap of point1 and point2 fails! This is the major source of confusion. In the main() method, point1 and point2 are nothing more than object references. When you pass point1 and point2 to the tricky() method, Java passes the references by value just like any other parameter. This means the references passed to the method are actually copies of the original references.
	

* **What is memory leak?**  
A memory leak is where an unreferenced object that will never be used again still hangs around in memory and doesn't get garbage collected.


* **What is the difference between == and .equals()?**  

	| == | .equals() |
	|:--:|:---------:|
	| To compare the references of the objects | Used to compare the values of two objects |


### [](id:Basics)Basics of Java

* **JVM**  
Java Virtual Machine (JVM) is an abstract machine which provides the runtime environment in which Java byte code can be executed. JVMs are available for many hardware and software platforms (so JVM is platform dependent).  


* **JRE**  
Java Runtime Environment (JRE) is the implementation of JVM and physically exists.


* **JDK**  
Java Development Kit (JDK) contains JRE + development tools and physically exists.


* **How many types of memory areas are allocated by JVM?**
	* **Class (Method) Area**  
		Stores per-class structures such as the runtime constant pool, field, and method data, the code for methods.
	* **Heap**  
		Runtime data area in which objects are allocated.
	* **Stack**  
		Stores frames. It holds local variables and partial results, and plays a part in method invocation and return. Each thread has a private JVM stack, created at the same time as thread. A new frame is created each time a method is invoked. A frame is destroyed when its method invocation completes.
	* **Program Counter (PC) Register**  
		Contains the address of the JVM instruction currently being executed.
	* **Native Method Stack**  
		Contains all the native methods used in the application.
		

* **What is JIT compiler?**  
Just-In-Time (JIT) compiler is used to improve the performance. JIT compiles parts of the byte code that have similar functionality at the same time, and hence reduces the amount of time needed for compilation. Here the term "compiler" refers to a translator from the instruction set of a JVM to the instruction set of a specific CPU.


* **What is platform?**  
The hardware or software environment in which a program runs. There are two types of platforms software-based and hardware-based. Java provides software-based platform.


* **What is the main difference between Java platform and other platforms?**  
Differs from most other platforms in the sense that it's a software-based platform that runs on top of other hardware-based platforms. It has two components:
	* Runtime Environment
	* API (Application Programming Interface)
	

* **What gives Java its 'write once and run anywhere' nature?**  
The byte code. Java is compiled to be a byte code which is the intermediate language between source code and machine code. This byte code is not platform speific and hence can be fed to any platform.


* **What is classoader?**  
A subsystem of JVM that is used to load classes and interfaces. Some of them are: Bootstrap classloader, Extension classloader, System classloader, Plugin classloader.


* **Is Empty .java file name a valid source file name?**  
Yes. Save your java file by .java only, compile it by javac .java and run by java yourclassname. Example:

	```
// save by .java only
class A {
	public static void main(String[] args) {
		System.out.println("Hello java");
	}
}
	```
	
	```
javac .java // compile
java A // run
	```
	
	
* **Is delete, next, main, exit or null keyword in Java?**  
No.


* **If I don't provide any arguments on the command line, then the String array of Main method will be empty or null?**  
It is empty but not null.


* **What if I write `static public void` instead of `public static void`?**  
Program compiles and runs properly,


* **What is the default value of the local variables?**  
The local variables are not initialized to any default value, neither primitive nor object references.


### Object Oriented Programming

* **What is the difference between object oriented programming language and object based programming language?**  
Object based programming language follows all the features of OOPs except Inheritance. Examples of Object based programming languages are JavaScript, VBScript.


* **What will be the initial value of an object reference which is defined as an instance variable?**  
The object references are all initialized to null in Java.


* **What is constructor?**  
Just like a method that is used to initialize the state of an object. It is invoked at the time of object creation.  
Rules for constructors:  
	&nbsp;&nbsp;&nbsp;&nbsp;Name must be the same as its class name.  
	&nbsp;&nbsp;&nbsp;&nbsp;Must have no explicit return type.
	
	
* **What is the purpose of default constructor?**  
Provides the default values to the objects. The Java compiler creates a default constructor only if there is no constructor in the class.


* **Does constructor return any value?**  
Yes, that is current instance. (You cannot use return type yet it returns a value)


* **Is constructor inherited?**  
No, it is not inherited.


* **Can you make a constructor final?**  
No, constructor can't be final.


* **What is static variable?**  
	* Used to refer the common property of all objects (that is not unique for each object).
	* Gets memory only once in class area at the time of class loading.
	

* **What is static method?**  
	* Belongs to the class rather than object of a class.
	* Can be invoked without the need for creating an instance of a class.
	* Can access static data member and can change the value of it.
	

* **Why is main method static?**  
Because object is not required to call a static method.


* **What is static block?**  
	* Used to initialize the static data member.
	* Executed before main method at the time of class loading.
	
	
* **Can we execute a program without main() method?**  
Yes, one of the way is using static block but in previous version of JDK not in JDK 1.7.

	```
class A3 {
	static {
		System.out.println("static block is invoked");
		System.exit(0);
	}
}
	```
	
	```
Output:
static block is invoked (if not JDK7)
Error: Main method not found in class A3, please define the main method.
	```
	
	
* **What if the static modifier is removed from the signature of the main method?**  
Program compiles but a runtime throws an error "NoSuchMethodError".


* **What is the difference between static (class) and instance method?**  

	| static or class method | instance method |
	|:----------------------:|:---------------:|
	| A method declared as static | A method not declared as static |
	| Object is not required to call method | Object is required to call method |
	| Cannot access non-static members | Can access non-static members |


* **What is `this` in Java?**  
It is a keyword that refers to the current object.
	* Can be used to refer current class instance variable.
	* `this()` can be used to invade current class constructor.
	* can be used to invoke current class method (implicitly).
	* can be passed as an argument in the method call.
	* can be passed as argument in the constructor call.
	* can also be used to return the current class instance.
	
	
* **What is inheritance?**  
A mechanism in which one object acquires all the properties and behavior of another object of another class. It represents IS-A relationship. It is used for Code Reusability and Method Overriding.


* **Which class is the superclass of every class?**  
Object class.


* **Why multiple inheritance is not supported in Java?**  
To reduce complexity and simplify the language.


* **What is composition?**  
Holding the reference of other class within some other class.

	
* **What is the difference between aggregation and composition?**  
Aggregation represents weak relationship whereas composition represents strong relationship. Example: bike has an indicator (aggregation) but bike has an engine (composition).


* **Why Java does not support pointers?**  
Pointer is a variable that refers to the memory address. They are not used in Java because they are unsafe (unsecured) and complex to understand.


* **What is super in java?**  
Keyword that refers to the immediate parent class object.


* **Can you use this() and super() both in a constructor?**  
No. Because super() or this() must be the first statement.


* **What is object cloning?**  
Used to create the exact copy of an object. Saves the extra processing task for creating the exact copy of an object.


* **Why method overloading is not possible by changing the return type in Java?**  
Because of ambiguity.


* **Can we overload main() method?**  
Yes, you can have many main() methods in a class by overloading the main method.


* **Can we override static method?**  
No, you can't override the static method because they are part of class not object.


* **Why we cannot override static method?**  
Because the static method is part of the class and it is bound with class whereas instance method is bound with object and static gets memory in class are and instance gets memory in heap.


* **Can we override the overloaded method?**  
Yes.


* **Difference between overloading and overridng?**  

	| Overloading | Overriding |
	|:-----------:|:----------:|
	| Increases readability of the program | Provides specific implementation of method that is already provided in super class |
	| Occurs within the class | Occurs in two classes |
	| Parameter must be different | Parameter must be the same |
	
	
* **Can you have virtual functions in Java?**  
Yes, all functions in Java are virtual by default.


* **What is covariant return type?**  
Now, since java5, it is possible to override any method by changing the return type if the return type of the subclass overriding method is subclass type. It is known as covariant return type.


* **What is Runtime Polymorphism?**  
Dynamic method dispatch is a process in which a call to an overridden method is resolved at runtime rather than at compile-time.  
In this process, an override method is called through the reference variable of a super class. The determination of the method to be called is based on the object being referred to by the reference variable.


* **Can you achieve Runtime polymorphism by data members?**  
No.


* **What is the difference between static binding and dynamic binding?**  
Static binding: The object is determined at compile time.  
Dynamic binding: The object is determined at run time.


* **What is abstraction?**  
Process of hiding the implementation details and showing only functionality to the user. It lets you focus on what the object does instead of how it does it.


* **What is the difference between abstraction and encapsulation?**  
Abstraction hides the implementation details whereas encapsulation wraps code and data in a single unit.


* **What is abstract class?**  
A class that is declared abstract. Needs to be extended and its method implemented. It cannot be instantiated.


* **Can there be any abstract method without abstract class?**  
No, if there is any abstract method in a class, that class must be abstract.


* **Can you use abstract and final both with a method?**  
No, because abstract method needs to be override whereas you cannot override final methods.


* **Is it possible to instantiate the abstract class?**  
No, abstract class can never be instantiated.


* **What is interface?**  
A blueprint of a class that have static constants and abstract methods. It can be used to achieve fully abstraction and multiple inheritance.
	
	
* **Can you declare an interface method static?**  
No, because methods of an interface is abstract by default, and static and abstract keywords can't be used together.


* **Can an interface be final?**  
No, because its implementation is provided by another class.


* **What is marker interface?**  
An interface that have no data member and method is known as a marker interface. For example, Serializable, Cloneable.


* **What is the difference between abstract class and interface?**  

	| Abstract class | Interface |
	|:--------------:|:---------:|
	| Can have non-abstract methods | Can only have abstract methods |
	| Can have instance variables | Cannot have instance variables |
	| Can have a constructor | Cannot have a constructor |
	| Can have static methods | Cannot have static methods |
	| Can extend one abstract class | Can implement multiple interfaces |
	
	
* **Can we define private and protected modifiers for variables in interfaces?**  
No, they are implicitly public.


* **When can an object reference be cast to an interface reference?**  
When the object implements the referenced interface.


* **What is package?**  
Group of similar type of classes interfaces and sub-packages. It provides access protection and removes naming collision.


* **Do I need to import java.lang package any time? Why?**  
No. It is by default loaded internally by the JVM.


* **Can I import same package/class twice? Will the JVM load the package twice at runtime?**  
Yes, can import multiple times. Neither compiler nor JVM companies about it. But the JVM will internally load the class only once no matter how many times you import the same class.


* **What is static import?**  
By static import, we can access the static members of a class directly, there is not to qualify it with the class name.


* **What is Exception Handling?**  
A mechanism to handle runtime errors. It is mainly used to handle checked exceptions.


* **What is the difference between Checked Exception and Unchecked Exception?**  
**Checked Exception:**  
The classes that extend Throwable class except RuntimeException and Error are known as checked exceptions e.g.IOException, SQLException etc. Checked exceptions are checked at compile-time.  
**Unchecked Exception:**  
The classes that extend RuntimeException are known as unchecked exceptions e.g. ArithmeticException, NullPointerException etc. Unchecked exceptions are not checked at compile-time.


* **What is the base class for Error and Exception?**  
Throwable.


* **Is it necessary that each try block must be followed by a catch block?**  
It should be followed by either a catch block OR a finally block. And whatever exceptions are likely to be thrown should be declared in the throws clause of the method.


* **What is finally block?**  
finally block is a block that is always executed.


* **Can finally block be used without catch?**  
Yes, by try block. finally must be followed by either try or catch.


* **Is there any case when finally will not be executed?**  
finally block will not be executed if program exits(either by calling System.exit() or by causing a fatal error that causes the process to abort).


* **Difference between throw and throws?**  

	| throw | throws |
	|:-----:|:------:|
	| Used to explicitly throw an exception | Used to declare an exception |
	| Checked exceptions cannot be propagated with throw only | Can be propagated with throws |
	| Is followed by an instance | Is followed by class |
	| Used within the method | Used with the method signature |
	| Cannot throw multiple exception | Can declare multiple exception |
	
	
* **Can an exception be rethrown?**  
Yes.


* **Can subclass overriding method declare an exception if parent class method doesn't throw an exception?**  
Yes but only unchecked exception.


* **What is exception propagation?**  
Forwarding the exception object to the invoking method.


* **What is the meaning of immutable in terms of String?**  
Unmodifiable or unchangeable. Once string object has been created, its value can't be changed.


* **Why string objects are immutable in Java?**  
Because java uses the concept of string literal. Suppose there are 5 reference variables, all refers to one object "sachin".If one reference variable changes the value of the object, it will be affected to all the reference variables. That is why string objects are immutable in java.


* **How many ways we can create the string object?**  
There are two ways to create the string object, by string literal and by new keyword.


* **How many objects will be created in the following code?**  
	
	```
String s1 = "Welcome";
String s2 = "Welcome";
String s3 = "Welcome";
	```
	
	Only one object.
	
	
* **Why Java uses the concept of string literal?**  
To make Java more memory efficient (because no new objects are created if it exists already in string constant pool).


* **How many objects will be created in the following code?**  

	```
String s = new String("Welcome");
	```
	
	Two objects, one in string constant pool and other in non-pool (heap).
	
	
* **What is the basic difference between String and StringBuffer object?**  
String is an immutable object. StringBuffer is a mutable object.


* **What is the difference between StringBuffer and StringBuilder?**  
StringBuffer is synchronized but StringBuilder is not synchronized.


* **How can we create immutable class in Java?**  
By defining final class that have final data members.


* **What is the purpose of toString() method in Java?**  
The toString() method returns the string representation of any object. If you print any object, java compiler internally invokes the toString() method on the object. So overriding the toString() method, returns the desired output, it can be the state of an object etc. depends on your implementation.


* **What is nested class?**  
A class which is declared inside another class is known as nested class.  
There are 4 types of nested class member:  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;inner class  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;local inner class  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;anonymous inner class  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;static nested class
	
	
* **Is there any difference between nested class and inner classes?**  
Yes, inner classes are non-static nested classes. I.e. inner classes are the part of nested classes.


* **Can we access the non-final local variable, inside the local inner class?**  
No, local variable must be constant if you want to access it in local inner class.


* **What is nested interface?**  
Any interface declared inside the interface or class. It is static by default.


* **Can a class have an interface?**  
Yes, nested interface.


* **Can an interface have a class?**  
Yes, they are static implicitly.


* **What is Garbage Collection?**  
A process of reclaiming the runtime unused objects. It is performed for memory management.


* **What is gc()?**  
gc() is a daemon thread.gc() method is defined in System class that is used to send request to JVM to perform garbage collection.


* **What is the purpose of finalize() method?**  
finalize() method is invoked just before the object is garbage collected. It is used to perform cleanup processing.


* **Can unreferenced objects be referenced again?**  
Yes.


* **What kind of thread is the Garbage collector thread?**  
Daemon thread.


* **What is the difference between final, finally, and finalize()?**  
**final:**  
Can be used for variable, method or class.  
**finally:**  
Used in exception handling and the block is always executed.  
**finalize():**  
Used in garbage collection. It is invoked just before the object is garbage collected. Can be used to perform any cleanup processing.


* **What is the purpose of the Runtime class?**  
To provide access to the Java runtime system.


* **How will you invoke any external process in Java?**  
By Runtime.getRuntime().exec(?) method.


* **Difference between the Reader/Writer class hierarchy and the InputStream/OutputStream class hierarchy.**  
Reader/Writer class hierarchy is character-oriented.  
InputStream/OutputStream class hierarchy is byte-oriented.


* **What is an I/O filter?**  
An I/O filter is an object that reads from one stream and writes to another, usually altering the data in some way as it is passed from one stream to another.


* **What is serialization?**  
Serialization is a process of writing the state of an object into a byte stream. It is mainly used to travel object's state on the network.


* **What is Deserialization?**  
Deserialization is the process of reconstructing the object from the serialized state.It is the reverse operation of serialization.


* **What is transient keyword?**  
If you define any data member as transient, it will not be serialized.


* **What is Externalizable?**  
Externalizable interface is used to write the state of an object into a byte stream in compressed format. It is not a marker interface.


* **What is the difference between Serializable and Externalizable interface?**  
Serializable is a marker interface but Externalizable is not a marker interface.When you use Serializable interface, your class is serialized automatically by default. But you can override writeObject() and readObject() two methods to control more complex object serailization process. When you use Externalizable interface, you have a complete control over your class's serialization process.


* **How do I convert a number IP address like 192.18.97.39 into a hostname like java.sun.com?**  
By InetAddress.getByName("192.18.97.39").getHostName() where 192.18.97.39 is the IP address.


* **What is reflection?**  
Reflection is the process of examining or modifying the runtime behaviour of a class at runtime. It is used in:  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IDE (Integrated Development Environment). (Eclipse, NetBeans, etc)  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Debugger.  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Test Tools
	
	
* **Can you access the private method from outside the class?**  
Yes, by changing the runtime behavior of a class if the class is not secured.


* **What are wrapper classes?**  
Classes that allow primitive types to be accessed as objects.


* **What is a native method?**  
A method that is implemented in a language other than Java.


* **What is the purpose of the System class?**  
To provide access to system resources.


* **What comes to mind when someone mentions a shallow copy in Java?**  
Object cloning.


* **What is singleton class?**  
Singleton class means that any given time only one instance of the class is present, in one JVM.


* **What is an applet?**  
A small java program that runs inside the browser and generates dynamic contents.

* **Can you write a Java class that could be used both as an applet as well as an application?**  
Yes, add a main() method to the applet.


* **What is Locale?**  
A Locale object represents a specific geographical, political, or cultural region.


* **How will you load a specific locale?**  
By ResourceBundle.getBundle(?) method.


* **What is a JavaBean?**  
Reusable software components written in the Java programming language, designed to be manipulated visually by a software development environment, like JBuilder or VisualAge for Java.


### [](id:Multithreading)Multithreading Interview Questions

* **What is multithreading?**  
Multithreading is a process of executing multiple threads simultaneously. Its main advantage is:  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Threads share the same address space.  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Thread is lightweight.  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Cost of communication between process is low.
	
	
* **What is a thread?**  
A thread is a lightweight subprocess. It is a separate path of execution. It is called separate path of execution because each thread runs in a separate stack frame.


* **What is the difference between preemptive scheduling and time slicing?**  
**Preemptive scheduling:**  
The highest priority task executes until it enters the waiting or dead states or a higher priority task comes into existence.  
**Time slicing:**  
A task executes for a predefined slice of time and then reenters the pool of ready tasks. The scheduler then determines which task should execute next, based on priority and other factors.


* **What does join() method do?**  
The join() method waits for a thread to die. In other words, it causes the currently running threads to stop executing until the thread it joins with completes its task.


* **What is the difference between wait() and sleep() method?**  

	| wait() | sleep() |
	|:------:|:-------:|
	| Is defined in Object class | Is defined in Thread class |
	| Releases the lock | Doesn't release the lock |
	
	
* **Is it possible to start a thread twice?**  
No, there is no possibility to start a thread twice. If it does, it throws an exception.


* **What about the daemon threads?**  
The daemon threads are basically the low priority threads that provides the background support to the user threads. It provides services to the user threads.


* **Can we make the user thread as daemon thread if thread is started?**  
No, if you do so, it will throw IllegalThreadStateException.


* **What is shutdown hook?**  
The shutdown hook is basically a thread invoked implicitly before JVM shuts down. So we can use it perform clean up resource.


* **When should we interrupt a thread?**  
We should interrupt a thread if we want to break out the sleep or wait state of a thread.


* **What is synchronization?**  
Synchronization is the capability to control the access of multiple threads to any shared resource. It is used:  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;To prevent thread interference.
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;To prevent consistency problem.
	
	
* **What is the purpose of Synchronized block?**  
It is used to lock an object for any shared resource. Scope of synchronized block is smaller than the method.


* **Can Java object be locked down for exclusive use by a given thread?**  
Yes. You can lock an object by putting it in a "synchronized" block. The locked object is inaccessible to any thread other than the one that explicitly claimed it.


* **What is static synchronization?**  
If you make any static method as synchronized, the lock will be on the class not on object.


* **What is the difference between notify() and notifyAll()?**  
The notify() is used to unblock one waiting thread whereas notifyAll() method is used to unblock all the threads in waiting state.


* **What is deadlock?**  
Deadlock is a situation when two threads are waiting on each other to release a resource. Each thread waiting for a resource which is held by the other waiting thread.


### [](id:Collections)Java Collections Interview Questions

* **Difference between ArrayList and Vector**  

	| ArrayList | Vector |
	|:---------:|:------:|
	| Not synchronized | Synchronized |
	| Not a legacy class | Is a legacy class |
	| Increases its size by 50% of the array size | Increases its size by doubling the array size |
	
	
* **Difference between ArrayList and LinkedList.**  

	| ArrayList | LinkedList |
	|:---------:|:----------:|
	| Uses dynamic array | Uses doubly linked list |
	| Is not efficient for manipulation because of shifting | Efficient for manipulation |
	| Better to store and fetch data | Better to manipulate data |
	
	
* **Difference between Iterator and ListIterator?**  

	| Iterator | ListIterator |
	|:--------:|:------------:|
	| Traverses the elements in forward direction only | Traverses the elements in backward and forward directions both. |
	| Can be used in List, Set and Queue | Can be used in List only |
	
	
* **Difference between Iterator and Enumeration.**  

	| Iterator | Enumeration |
	|:--------:|:-----------:|
	| Can traverse legacy and non-legacy elements | Can traverse only legacy elements |
	| Is fail-fast | Is not fail-fast |
	| Is slower than Enumeration | Is faster than Iterator |
	
	
* **What is the difference between List and Set?**  
List can contain duplicate elements whereas Set contains only unique elements.


* **What is the difference between HashSet and TreeSet?**  
HashSet maintains **no order** whereas TreeSet maintains **ascending order**.


* **What is the difference between Set and Map?**  
Set contains values only whereas Map contains keys and values both.


* **What is the difference between HashSet and HashMap?**  
HashSet contains only values whereas HashMap contains entry(key,value). HashSet can be iterated but HashMap need to convert into Set to be iterated.


* **What is the difference between HashMap and TreeMap?**  
HashMap maintains **no order** but TreeMap maintains **ascending order**.


* **What is the difference between HashMap and Hashtable?**  

	| HashMap | Hashtable |
	|:-------:|:---------:|
	| Not synchronized | Synchronized |
	| Can contain one null key and multiple null values | Cannot contain any null key or null value |
	
	
* **What is the difference between Collection and Collections?**  
Collection is an interface whereas Collections is a class. Collection interface provides normal functionality of data structure to List, Set and Queue. But, Collections class is to sort and synchronize collection elements.


* **What is the difference between Comparable and Comparator?**  

	| Comparable | Comparator |
	|:----------:|:----------:|
	| Provides only one sort of sequence | Provides multiple sort of sequence |
	| Provides one method named compareTo() | Provides one method named compare() |
	| Is found in java.lang.package | Is found in java.util.package |
	| Actual class is modified | Actual class is not modified |
	
	
* **What is the advantage of Properties file?**  
If you change the value in properties file, you don't need to recompile the java class. So, it makes the application easy to manage.


* **What does hashCode() method do?**  
	* Returns a hash code value (an integer number).
	* Returns the same integer number, if two keys (by calling equals() method) are same.
	* But it is possible that two hash code numbers can have different or same keys.
	
	
* **Why do we override equals() method?**  
The equals method is used to check whether two objects are same or not. It needs to be overridden if we want to check the objects based on property.  

	For example, Employee is a class that has 3 data members: id, name and salary. But, we want to check the equality of employee object on the basis of salary. Then, we need to override the equals() method.
	
	
* **How to synchronize List, Set, and Map elements?**  

	```
public static List synchronizedList(List l) { }
public static Set synchronizedSet(Set s) { }
public static SortedSet synchronizedSortedSet(SortedSet s) { }
public static Map synchronizedMap(Map m) { }
public static SortedMap synchronizedSortedMap(SortedMap m) { }
	```
	
	
* **What is the advantage of generic collection?**  
If we use generic class, we don't need typecasting. It is typesafe and checked at compile time.


* **What is hash-collision in Hashtable and how it is handled in Java?**  
Two different keys with the same hash value is known as hash-collision. Two different entries will be kept in a single hash bucket to avoid the collision.


* **What is the Dictionary class?**  
The Dictionary class provides the capability to store key-value pairs.


* **What is the default size of load factor in hashing based collection?**  
The default size of load factor is 0.75. The default capacity is computed as initial capacity * load factor. For example, 16 * 0.75 = 12. So, 12 is the default capacity of Map.








	