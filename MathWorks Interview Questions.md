<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## MathWorks Interview Questions

### __Math__

* **What is autocorrelation?**

* **Given a graph, how many edges are possible for both directed and undirected graph.**

* **Plot the derivative of the function.**

* **Find the partial fraction of the given expression.**

* **Find the gradient of the given function.**

* **Find the inverse of a 3x3 matrix.**

* **Find the orthogonal vector to A = i + 2j + k; B = j + 2k**

* **Find the acceleration from velocity.**

* **What is PSD and what is its relationship with autocorrelation?**

* **Given a differential equation and asked for degree and order.**

* **Given a matrix and asked for eigenvalue and eigenvector.**

* **Four colored problem.**

* **Finding nth term in a sequence.**

* **If total number of students are 40 and students taking German are 22 and students taking both english and german are 12. How many students are taking English? We know that every student has to take at least one language.**

* **What's the probability of 2 people in a room sharing a birthday, if we have 400 people in a room?**

* **What is the sum of first n integers?**

* **Can you please derive the equation for sum of first n integers?**

* **Expand (A U B) n C.**

* **Definite integral and indefinite integral?**

* **Calculate eigenvalues of matrix [3, -1, 1, 5].**

* **Given a function, calculate left limit and right limit, whether the limit exists.**

* **How do you derive a sum on N natural numbers (Math Induction).**

* **A U (B n C) = ?**

* **lim(x) -> 0 sin(x) / x**

* **What is eigen values and eigen vectors?**

* **Calculate a vector perpendicular to vector A and B.**

* **What is an integral? What is a derivative? Relation between the two.**

* **What is differentiation? What is integration?**

* **What is the difference between definite and indefinite integral? If the limits are -inf to inf, is it a definite integral or an indefinite? (Ans: Definite)**

* **What is a linear differential equation?**

* **What is a partial differential equation?**

* **Do a dot product of given two 3-D vectors.**

* **What is a singular matrix?**

* **What is a symmetric matrix?**

* **What is the probability that you get 2 aces when you are dealt two cards?**

* **Inverse / transpose of matrix.**

* **Find the largest rectangle under a curve symmetric about the y-axis. The equation of the curve was given.**

* **Find the gradient of a scalar function.**

* **What is a metric?**

* **Given a summation to infinity of a GP series and asked for the sum.**

* **Why do the car tyre looks to be turning backward before it comes to a stop?**
	
	Aliasing is what is happening.

* **What is pigeonhole principle?**

* **What is the rank of a matrix?**

* **What is the matrix space?**

* **What is a null space of a vector on another vector?**

* **Cross product of vectors: a = i, b = j + k, what is a*b?**

* **a = i + 3j - 4k, b = 1 - 2j + 3k, the mapping of b on a?**

* **Integral of x*cos(x) over x?**

* **What is symmetric/identity/singular matrix?**

* **How to calculate the singular matrix of a given 2*2 matrix [3 2; 2 1]?**

* **Find observability of a given state space system.**

* **What is asymptotic stability?**

* **What is the maximum area of the rectangle that can be drawn under the curve y = 12 - x^2.**

* **Draw the differential of a given curve.**

* **How does 2nd order response look like when zeta is 1? How does critically damped response look like?**

* **Check whether a string is a palindrome or not.**

* **How do you find the gain and phase margins from a Bode plot?**


### Programming Concepts

* **Given a random array of numbers, how do you sort them? Select any sorting algorithm and write the pseudo code.**

* **Implement Merge Sort with merge subroutine.**

* **Given inheritance hierarchy, which of the following is valid?**
          <br>A<br>
         / \ <br>
        B   C<br>
       / <br>
      D
     
     ```
     void alpha(B *arg)
     	A* Aptr = new A;
     	B* Bptr = new B; // valid
     	C* Cptr = new C;
     	D* Dptr = new D; // valid
     ```

* **What does the following line of code do?**
	
	```
	char *c = "Hello";
	char d[6];
	while (*c++ = *d++); 
	```

* **Singleton concept.**

* **IPC in Linux, What is mutual exclusion, critical section, locks.**

* **What's the maximum size of a signed integer?**

* **Dreaded diamond inheritance problem.**

* **Why is dynamic array preferred over LinkedList.**

* **What is OOPS? Why is OOP required?**

* **Explain/write a recursive function.**

* **How does a system handle recursion calls?**

* **What is max flow min cut algo?**

* **If two functions of O(n) complexity were multiplied/added what is the complexity of the resultant function.**

* **What is a SAN? What is a NAS? What is multipathing?**

	SAN - direct attached storage presented at the bit level.<br>
	NAS - network connected and presented via a network protocol (NFS, CIFS) and is file level.<br>
	Multipathing - the ability to have redundant paths to the same storage resource. This provides redundancy in the event of a failure.

* **Complexity of converting from nfa to dfa.**

* **Difference between deterministic and non-deterministic state machines.**

* **What is local scope and global scope?**

* **Is binary tree and directed graph the same thing?**

* **How many different kinds of sorting algorithms are there in programming? Write bubble sort program.**

### Java

* **Difference between path and classpath.**

* **What are applets in Java?**

* **What is JVM?**

* **How is Java platform independent?**

* **What are JDK and JRE?**

* **What is a package?**

* **What are generics?**

* **What are Java Beans?**

* **What are wrapper classes and what are the advantages?**

* **Can you force garbage collection in Java? How?**

* **Is Java pass by value or reference? Why? How do you pass objects?**

* **final, finally, finalize.**

* **When does finally does not work in Java.**

* **Exit condition for the Fibonacci Series.**

* **Difference between String and StringBuffer.**

* **What is overloading, overriding?**

* **What is the use of destructor?**

* **What is the difference between static and dynamic memory allocation?**

* **What is a static variable?**

* **Use of abstract.**

* **If a default constructor is made private, would the implementation change and how?**

* **Primitive data type like int, float, and object data type difference.**

* **How to implement queue using stacks?**

* **What is mutex?**

* **What is critical section?**

* **Implement depth first search.**

* **Difference between a directed acyclic graph and binary search tree.**

* **What is postorder, preorder, and inorder?**

* **String manipulation question in which a string containing one or more * was given as input and I have to develop an algorithm for removing the * character and a character succeeding and preceding the * character.**

* **Difference between .equals and ==.**

* **What is public static void main(String[] args) in Java?**

* **Time complexity of matrix multiplication.**

* **Design a class structure for your department in college. What kind of methods will you have to extract specific information.**

* **If you were writing a function in a calculator to compute sine/cosine/tangent, and all you had was basic math operations (+, -, *, /) how would you do it? You cannot use lookup tables.**

* **What is util, swing..?**

* **Why Java runs slower than C?**

* **Why Java have hashmap, but C does not?**

* **Difference between dot product and cross product.**

* **Implement a fraction class with add multiplication subtraction functionalities.**


### JavaScript

* **Difference between document.ready() and window.onload().**

* **What is cache?**

* **What is SOAP?**

* **What is REST?**

* **Difference between HTML and XML?**

### C++

* **What is polymorphism?**

* **What is a pointer?**

* **What is a void pointer?**

* **What is a smart pointer?**

* **What's the significance of a null pointer?**

	C language does not specify an implicit initialization for objects for automatic storage duration. To ensure that the address to which pointer points is valid its 	explicitly initialized to the null pointer.

* **What is the default property for a variable and a function defined in a class (public, private or protected)?**

* **What is virtual constructor?**

* **What is virtual function?**

* **Can you define a function in c++ structure?**

* **How do you concatenate two strings?**

* **Invocation order of constructors and destructors in C++ inheritance.**

* **Exception handling.**

* **Advantages of OOP programming over procedure programming.**

* **How to have an instance of a class if the constructor is private?**

* **If class foo has private data types and private methods only, class bar inherits from class foo. How can you access the data types?**

* **Explain these pieces of code.**

	```
	int arr[] = {1, 2, 3, 4};
	for (int i = 0; i < 4; i++) {
		cout << *(arr + i) << " ";
	}
	```

	```
  	main() {
  		const float pi = 3.14;
  		pi = 5.40;
  		printf('%f', &pi);
  	}
  	```
  	
  	```
  	int main(void) {
  		int a = 5;
  		float b = a / 2;
  		printf("b=%f", b);
  		return 0;
  	}
  	```
  	
  	```
  	#include <iostream>
  	using namespace std;
  	
  	int main() {
  		int arr[5] = {11, 22, 33, 44, 55};
  		int i;
  		
  		for (int i = 0; i < 5; i++) {
  			cout << *(arr + i);
  			cout << *(arr++);
  		}
  		
  		return 0;
  	}
  	```

* **Difference between #define and constant.**

* **Difference between structures and classes?**

* **Can we declare functions inside a structure?**

* **How do you append a string in C++?**

* **Purpose of private constructor in C++?**

* **What is an abstract class and its significance.**

* **Runtime polymorphism.**

* **Static keyword.**

* **What data structure would you use and how would you implement a sparse matrix?**

* **What is #include?**

* **What is the significance of angular brackets <>?**

* **Can you perform arithmetic operations on void pointers?**

### C

* **What is private function?**

* **What is hf = gca;**

* **What is event function call back?**

* **How to access data members of a structure?**

* **What are cell arrays?**

* **C1 = {}, C2 = {}. What is C1()? What is C1{}?**

* **What is the code doing?**

	```
	mystruct = struct('field1', {1, 2, 3} ... 'field2', {4, 5, 6s});
	```

* **File operations in C.**

* **Null Pointer.**

* **Auto variable and register variable?**

* **How do you find whether a number is even or odd?**

* **If you are using a mod operator, what are the advantages and disadvantages of it? Elaborate. Is there any other approach?**

* **Why do we use constants in C?**

* **What is malloc and calloc? What's the difference?**

* **Difference between <> and " ".**

* **What is the procedure to find an even number, other than the mod operator.**

* **What is the limitation of mod operator in C.**

* **What is a UNION datatype.**

* **Volatile keyword.**

* **Reentrant code.**

* **typedef vs #define.**

* **typecasting.**

* **What precautions one must take while using pointers.**

* **Code to draw circle in C?**

* **What is the difference between malloc and new?**

	Malloc returns a void pointer.<br>
	New returns a pointer to the type of object you allocated space for.

* **What is pure virtual function?**

* **Difference between using #include and <stdio.h> and "stdio.h".**

* **What is the difference between CRect c; and CRect c(), when CRect is a class?**

* **Virtual constructor and virtual destructors. Why virtual constructor is wrong and virtual destructor is necessary?**

* **How to optimize the following code:**

	```
	a[i] = b[c[i]];
	```

* **Write a program to reverse a string in C.**

### Matlab

* **Plot scattered point with given properties.**

* **What is primary function and subfunction?**

* **What is the difference between nested function and subfunction?**

* **Difference between A.' and A'**

* **MatLab code to clear workspace variable?**

* **There are 100 variables in the workspace. How to delete all variables except 2?**

* **MatLab code for matrix concatenation?**

* **What does '@' symbol mean in MatLab and where do we use it?**

* **Difference between cell array and structure in MatLab?**

* **Meaning of @, %, ~.**

* **Difference between A^2, A.^2.**

* **A = 1:1:100; find every third elements.**

* **A = 1:1:100; find all elements divisible by 5.**

* **What's path meaning? Used for?**

* **What is the exclamation mark in MatLab?**

* **Difference between function and scripts.**

* **How to concatenate matrices, finding an element in a matrix.**

* **Where are the help documents stored in MatLab?**

* **Removing elements divisible by 5 in a vector in MatLab?**

* **Operators in MatLab?**

* **Cross product of two vectors?**

* **Delete a column of a matrix.**

* **How would you reload workspace variables on MatLab startup (check out startup.m and finish.m online).**

* **Suppressing warnings in MatLab, private functions.**

* **Write a program to draw an arc starting at some point on the y-axis. Radius is given and from the given information it was also possible to find the angle of the arc with the origin, starting from a point on the y-axis and drawn clockwise.**

* **Defining variables in functions and trying to access them from MatLab command prompt as though they were workspace variables.**

* **How do you define your own function in MatLab and save it in the list of predefined functions.**

* **How do you determine a variable type in MatLab?**

* **How will you pull out the first rows of a 3x3 matrix?**

	A = B(1:2,:)

* **What are mex functions?**

* **Where are global and persistent variables stored?**

* **Give 2 different ways to access an element in a matrix.**

* **What command would you use to get 2 different axes on the same figure?**

	A(2, 1) and A(4).

* **Is MatLab column specific or row specific?**

* **How do you preserve MatLab settings across sessions?**

* **What does A' do? How do you take transpose of a matrix in MatLab?**

* **What is the difference between * and .*?**

* **How do you take inverse of a matrix in MatLab?**

* **How to plot two curves on different on coordinate systems in the same figure using MatLab?**

* **What will be the output of A(3) = 1?**

* **Output of A(:), when A is a matrix?**

* **What is the output if a matrix is printed like A = [1 2 3; 2 3 4; 1 4]**

### Control Systems

* **Explain lead and lag compensators.**

* **Linearize the system.**

* **Find the Transfer function from the state space equation.**

* **Given x1 and x2 dot, find the Lyapunov equation.**

### Operating System

* **What is RTOS?**

* **Soft vs Hard RTOS?**

* **Scheduling? Examples of scheduling?**

* **Priority inversion?**

* **Embedded communication method examples?**

* **What are presses?**

* **What is the difference between process and thread?**

* **What is virtual memory?**

### Digital Signal Processing

* **Difference between discrete and continuous delta function.**

* **FIR vs IIR**

* **The sampling frequency for 3cos(600*pi*t) + 2cos(1800*pi*t)**

* **Nyquist Frequency Theorem.**

* **Sampling Theorem.**

* **Z-Transforms**

* **h[n] = [1, 2, 3, 4, 5] i/p frequency = 100HZ, system is LTI. What is the o/p frequency?**

* **Same i/p frequency, now h[n] = [1, 4, 9, 16, 25]. What is the o/p frequency?**

* **What is the relationship between bandwidth and time duration?**

* **Given a signal spectrum that is valid in range of -pi/2 to pi/2. What is the range of frequency when the signal is oversampled by a factor of 4?**

* **What is the relationship between Discrete Fourier Transform and Z-Transform?**

* **y[n] = x[n^2]. y(n) = x(n^3). System Stable? Casual? Linear?**

* **Impulse response h[n] = 9*n*u(n), system stable?**

* **h[n] = [4, 0, 1, 0, 2], arrow on second element, casual?**

* **What is convolution? Difference between convolution and correlation?**

* **Difference between DFT and DTFT? Which one is suitable for computers?**

* **Difference between DFT and FFT?**

* **Aliasing, given an example of wheel with pokes.**

* **Connection between DTFT and Z-Transform, the expect z = e^(jw)**

* **ROC of Z-Transform.**

* **Determine if a system is time-invariant or invariant.**

* **Given x(n) and y(n), determine if it's FFR or IIR.**

* **Stable system, casual system.**

* **What is f0 in Nequist Theory?**

* **What is continuous time system? What is Discrete time system? How do you convert one to the other**

* **What is an LTI system? What is causality?**

* **What are random processes?**

* **What is PSD? What does PSD of white noise look like?**










