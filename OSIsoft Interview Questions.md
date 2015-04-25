<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## OSIsoft Interview Questions

* **What is programming?**  
	Creative process done by programmers to instruct a computer on how to do a task.


* **What is the difference between heap and stack?**

	| Heap | Stack |
	|:----:|:-----:|
	| Dynamic memory allocation | Static memory allocation |
	| Stored in the computer's RAM | Stored in the computer's RAM |
	| Accessing this memory is a bit slower | Accessing this memory is very fast |
	| Elements have no dependencies with each other and can always be accessed randomly at any time | LIFO order, the most recently reserved block is always next block to be freed |
	| Complex to keep track of which parts of the heap are allocated or free at any given time | Easy to keep track of the stack, freeing a block from the stack is nothing more than adjusting one pointer |


* **What is the advantages of C++ over C?**
	* **Stronger Type Checking**  
		The use of classes, inheritance, automatic type conversions.  
	* **Type safe linkage**  
		You can't accidentally call a routine from another module with the wrong type and/or number of arguments - even if your header files get out of date.  
	* **Complex data type is provided**  
		Includes all the standard arithmetic operations, implemented as operators, not function calls.  
	* User-defined operators and function overloading are supported


* **In OOP, you are required to design a mouse to interact with computer.**

* **Check if an integer is a palindrome.**

```
public class CheckIntegerPalindrome {
	public static boolean isPalindrome(int x) {
		if (x < 0)
			x = -x;
		
		int div = 1;
		
		while (x / div >= 10) {
			div *= 10;
		}
		
		while (x != 0) {
			int left = x / div;
			int right = x % 10;
			
			if (left != right)
				return false;
			
			x = (x % div) / 10;
			div /= 100;
		}
		
		return true;
	}
	
	public static void main(String[] args) {
		System.out.println(isPalindrome(-121));
	}
}
```


* **What is a smart pointer?**  
	A smart pointer is a class that wraps a "bare" C++ pointer, to manage the lifetime of the object being pointed to so we don't have to worry about destroying it.


* **List 3 reasons why OSIsoft should hire you?**


* **What is a program, explain how a program can run on a computer.**  
	A program is like a recipe. It contains a list of ingredients (called variables) and a list of directions (called statements) that tell the computer what to do with the variables.  
	A program is translated into a machine language that the computer can understand. This translation is performed by compilers, interpreters, and assemblers.


* **Does a program multitask truly?**  
	No, unless it's using multi core processors.

	
* **What components does a program use?**


* **What's a blue screen?**  
	Blue screen of death (BSOD) is when Microsoft Windows encounters a critical error it can't recover from, requiring a reboot and possibly resulting in lost work. It is the result of low-level software crashing or faulty hardware.


* **What information will be there in the memory dump for a blue screen of death?**  
	It provides you with information about the cause of the system crash.


* **What's Object Oriented Programming?**  
	It's programming concept in which programmers define not only the data type of a data structure, but also the types of operations that can be applied to the data structure. In this way, the data structure becomes an object that includes both data and functions. In addition to that, we can also create relationships between one object and another.


* **What is polymorphism?**  
	Is the ability to present the same interface for differing underlying forms (data types).
	

* **What is Heap/Stack?**  
	Stack is the memory set aside as scratch space for a thread execution. When a function is called, a block is reserved on the top of the stack for local variables and some bookkeeping data. When that function returns, the block becomes unused and can be used the next time a function is called. The stack is always reserved in a LIFO order making it really simple to keep track of the stack.
	
	Heap is the memory set aside for dynamic allocation. Unlike the stack there's no enforced pattern to the allocation and deallocation of blocks from the heap; you can allocate a block at any time and free it at any time. This makes it much more complex to keep track of which parts of the heap are allocated or free at any given time.
	

* **Why do programs crash?**  
	Run out of memory. Error accessing resources. Runtime, compiletime, silent errors.
	
	
* **What is procedural programming?**  
	Uses a list of instructions to tell the computer what to do step-by-step. It relies on procedures, also known as routines or subroutines. A procedure contains a series of computational steps to be carried out.

* **What is the difference between C++ and Java?**  
	
	| C++ | Java |
	|:---:|:----:|
	| Possible to write non-OOP code | Not possible to write non-OOP code |
	| Does not have garbage collector to free unused resources | Has a garbage collector to free unused resources |
	| Compiled binaries run natively on OS level | Compiled bytecode class files run inside a virtual machine |
	| Has pointer arithmetics | Does not have pointer arithmetics |


* **Write the strcmp function. Then given the password check is using this function, what security issue do you have? How to crack this system?**


* **What's the difference between class and instance?**  
	A blueprint for a house design is like a class description. All the houses build from that blueprint are objects of that class. A given house is an instance.  
	Class variables only have one copy that is shared by all the different objects of a class, whereas every object has it's own personal copy of an instance variable.  
	So, instance variables across different objects can have different values whereas class variables across different objects can have only one value.


* **How to find a perfect number?**

```
public class PerfectNumber {
	public static boolean isPerfectNumber(int num) {
		int temp = 0;
		
		for (int i = 1; i <= num / 2; i++) {
			if (num % i == 0)
				temp += i;
		}
		
		if (temp == num)
			return true;
		else
			return false;
	}
	
	public static void main(String[] args) {
		System.out.println(isPerfectNumber(28));
	}
}
```


* **32-bit VS 64-bit processor.**  
	* More bits means that data can be processed in larger chunks which also means more accurately.
	* More bits means our system can point to or address a larger number of locations in physical memory.
	

* **Threads vs Processes.**
	
	| Threads | Processes |
	|:-------:|:---------:|
	| A path of execution within a process | An executing instance of an application |
	| Used for small tasks (lightweight process) | Used for execution of applications (heavyweight process) |
	| Threads within the same process share the same address space | Different processes do not share the same address space |
	| Easier to create | Much harder to create |


* **Pointers: Will it make your program faster or slower? Why?**
	Faster. A variable does not have to live in main memory. Depending on the circumstances, the compiler can store it in a register for all or part of its life, and accessing a register is much faster than accessing RAM.


* **What is heap data structure?**

* **Arrays vs List.**

	| Arrays | List |
	|:------:|:----:|
	| Size is fixed | Dynamic size |
	| Inserting is expensive | Ease of insertion and deletion |
	| Random access is allowed | Random access is not allowed |


* **Write a program that creates a new vector that contains all the integers in the given vector with no duplicates.**

```
public class RemoveDuplicatesInArray {
	public static int[] removeDuplicates(int[] array) {
		Arrays.sort(array);
		int duplicateCount = 0;
		
		for (int i = 0; i < array.length; i++) {
			if (i + 1 < array.length && array[i] == array[i + 1])
				duplicateCount++;
		}
		
		int[] arrayNoDuplicates = new int[array.length - duplicateCount];
		int index = 0;
		
		for (int i = 0; i < array.length; i++)  {
			if (i + 1 < array.length && array[i] == array[i + 1]) {
				continue;
			} else {
				arrayNoDuplicates[index] = array[i];
				index++;
			}
		}
		
		return arrayNoDuplicates;
	}

	public static void main(String[] args) {
		int[] array = { 3, 1, 1, 4, 1, 4, 5 };
		System.out.println(Arrays.toString(removeDuplicates(array)));
	}
}
```


* **What is active directory?**  
  
	Active directory is a special purpose database; it is not a registry replacement. The directory is designed to handle a large number of read and search operations and a significantly smaller number of changes and updates.

* **How do you troubleshoot programs that freeze?**