<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## Yelp Interview Questions

1. [HR Questions](#HRQuestions)
2. [General Questions](#GeneralQuestions)
3. [Algorithm & Data Structures](#Algorithm)
4. [Front End](#FrontEnd)
5. [Database](#Database)
6. [Java](#Java)
7. [Operating System](#OS)
8. [Unix](#Unix)

### [](id:HRQuestions)HR Questions

* **Why Yelp?**

* **What is a bit?**  
	Smallest unit of data in a computer with single binary value, either 0 or 1.

* **What is a byte?**  
	A group of binary digits or bits operated as a unit.

* **How many bits in a short?**  
	16 bits.

* **What is the size of int?**  
	32 bit.

* **Number of bytes in a 64 bit machine.**

* **Number of bytes to code 64 bits?**

* **What is the value of the unsigned integer in a 32 bit machine?**  
	0 - 4,294,967,295

* **What is the value of the signed integer in a 32 bit machine?**  
	-2,147,483,648 - 2,147,483,648

* **How many bits are required to represent an octal digit?**  
	3

* **Number of digits needed to code an octet? What if we’re in base 8?**  
	3 digits in decimal (base 10)  
	3 digits in octal (base 8)

* **Where can you apply binary search - sorted array or linked list?**  
	Sorted array as you can do random access using index whereas you have to traverse through using linked list.

* **Time complexity of binary search.**  
	O(log n)

* **Time complexity of adding a node at the head of the linked list.**  
	O(1) or constant time.

* **What is the signal number for kill?**  
	9

* **How would you find a method in a file?**  
	grep myMethodName filename.c  
	ack myMethodName filename.c

* **How would you find whether a remote computer is online or not?**  
	ping (ip address)

* **How to select one row of a table in SQL?**

	```
	SELECT * FROM 'table_name'
    WHERE 'condition'
	```

* **Port number of HTTP and protocol used by HTTP.**  
	Port number of HTTP - 80.  
	Application layer protocol because it allows two applications to communicate over the network.

* **Full form of SSL and what does it do?**  
	Secure Sockets Layer is a security protocol. Standard security technology for establishing an encrypted link between a server and a client.


### [](id:GeneralQuestions)General

* **What’s a static variable?**  
	One that's associated with a class, not objects of that class.

* **Tuples and list Python.**

* **How would you automate the process of solving a bug that you had encountered in one of my programs.**

* **What is the largest integer in Java?**  
	2,147,483,648.

* **How to get all instances of a class.**

* **Mutable/immutable among tuples, dictionaries, lists.**

* **Memory management (implementation of a garbage collector).**

* **Compilation of Python code.**

* **Would it generally be better to run a binary search on a sorted array array, or a linked list? Explain the decision.**  
	Sorted array as you can do random access using index whereas you have to traverse through using linked list.

* **How does memory management in your strongest language?**  
[Memory Management](http://www.memorymanagement.org/mmref/begin.html)

* **What is the average disk access time?**  
	seek time + rotational delay + transfer time

* **Which operation is more expensive? Multiply, Divide, or Add.**  
	Divide.

* **How would you use all the data at our disposal?**

* **How does the domain name map to ip address?**

* **Building regular expressions to catch specific patterns.**

* **Run time of insert/lookup in hash table that uses lists.**  
	Best Case : O(1)  
	Worst Case : O(n)

* **What is Big O notation?**  
	Is a notation to describe the performance or complexity of an algorithm.

* **If memory is limited, which data structure is better: HashTable or binary tree?**  
	Binary tree because it will only allocated as much space as it needs.

### [](id:Algorithm)Algorithm & Data Structure

* **Given a corpus of a review, split it in terms sentences (Make sure to take care of ellipses, question marks and exclamation marks).**

	```
public class SplitToSentence {
	public static ArrayList<String> splitToSentence(String review) {
		Pattern re = Pattern.compile("[^.!?\\s][^.!?]*(?:[.!?](?!['\"]?\\s|$)[^.!?]*)*[.!?]?['\"]?(?=\\s|$)", Pattern.MULTILINE | Pattern.COMMENTS);
		Matcher reMatcher = re.matcher(review);
		ArrayList<String> sentences = new ArrayList<String>();
		
		while (reMatcher.find()) {
			sentences.add(reMatcher.group());
		}
		
		return sentences;
	}
	
	public static void main(String[] args) {
		String review = "This is how I tried to split a paragraph into a sentence! But, there is a problem. My paragraph includes dates like Jan.13, 2014 , words like U.S and numbers like 2.2? They all got splitted by the above code.";
		ArrayList<String> sentences = splitToSentence(review);
		
		for (String sentence : sentences) {
			System.out.println(sentence);
		}
	}
}
	```


* **Implement a Most Recently Used (MRU) Cache.**

	```
public class MRU<K, V> {
	private static final float hashTableLoadFactor = 0.75f;
	private LinkedHashMap<K, V> map;
	private int cacheSize;
	
	public MRU(int cacheSize) {
		this.cacheSize = cacheSize;
		int hashTableCapacity = (int) Math.ceil(cacheSize / hashTableLoadFactor) + 1;
		map = new LinkedHashMap<K, V>(hashTableCapacity, hashTableLoadFactor, false) {
			private static final long serialVersionUID = 1;
			
			protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
				return size() > MRU.this.cacheSize;
			}
		};
	}
	
	public synchronized V get(K key) {
		return map.get(key);
	}
	
	public synchronized void put(K key, V value) {
		map.put(key, value);
	}
	
	public synchronized void clear() {
		map.clear();
	}
	
	public synchronized int usedEntries() {
		return map.size();
	}
	
	public synchronized Collection<Map.Entry<K, V>> getAll() {
		return new ArrayList<Map.Entry<K, V>>(map.entrySet());
	}
}	
	```


* **Design a Least Recently Used Cache (LRU) Cache.**

	```
public class LRU<K, V> {
	private static final float hashTableLoadFactor = 0.75f;
	private LinkedHashMap<K, V> map;
	private int cacheSize;
	
	public LRU(int cacheSize) {
		this.cacheSize = cacheSize;
		int hashTableCapacity = (int) Math.ceil(cacheSize / hashTableLoadFactor) + 1;
		map = new LinkedHashMap<K, V>(hashTableCapacity, hashTableLoadFactor, true) {
			private static final long serialVersionUID = 1;
			
			protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
				return size() > LRU.this.cacheSize;
			}
		};
	}
	
	public synchronized V get(K key) {
		return map.get(key);
	}
	
	public synchronized void put(K key, V value) {
		map.put(key, value);
	}
	
	public synchronized void clear() {
		map.clear();
	}
	
	public synchronized int usedEntries() {
		return map.size();
	}
	
	public synchronized Collection<Map.Entry<K, V>> getAll() {
		return new ArrayList<Map.Entry<K, V>>(map.entrySet());
	}
}	
	```


* **Given an iterator interface for 1 word, extend to implement an iterator function for two words.**

* **Implement a trie. (Write the API and code for inserting into a trie)**

```
public class TrieNode {
	char content;
	boolean isEnd;
	int count;
	LinkedList<TrieNode> childList;
	
	public TrieNode(char c) {
		content = c;
		isEnd = false;
		count = 0;
		childList = new LinkedList<TrieNode>();
	}
	
	public TrieNode subNode(char c) {
		if (childList != null)
			for (TrieNode child : childList)
				if (child.content == c)
					return child;
		
		return null;
	}
}

public class Trie {
	private TrieNode root;
	
	public Trie() {
		root = new TrieNode(' ');
	}
	
	public void insert(String word) {
		if (search(word))
			return;
		
		TrieNode current = root;
		
		for (char c : word.toCharArray()) {
			TrieNode child = current.subNode(c);
			
			if (child != null)
				current = child;
			else {
				current.childList.add(new TrieNode(c));
				current = current.subNode(c);
			}
			
			current.count++;
		}
		
		current.isEnd = true;
	}
	
	public boolean search(String word) {
		TrieNode current = root;
		
		for (char c : word.toCharArray()) {
			if (current.subNode(c) == null)
				return false;
			else
				current = current.subNode(c);
		}
		
		if (current.isEnd)
			return true;
		
		return false;
	}
	
	public void remove(String word) {
		if (!search(word))
			return;
		
		TrieNode current = root;
		
		for (char c : word.toCharArray()) {
			TrieNode child = current.subNode(c);
			
			if (child.count == 1) {
				current.childList.remove(child);
				return;
			} else {
				child.count--;
				current = child;
			}
		}
		
		current.isEnd = false;
	}
}	
```


* **Given an array of Strings and return all groups of strings that are anagrams. Continue with a huge list of words that won’t fit in memory. Example input : [“art”, rat”, “bats”, “banana”, “stab”, “tar”]; output = [[“art”, “rat”, “tar”], [“bats”, “stab”], [“banana”]].**

* **Using random numbers to determine value of PI, and how to let it work in multi-computer environment.**

* **“tom” has “salad soup sandwich”, “rose” has “drink soup”. Input “salad sandwich” return “tom rose”.**

* **Given a software package depend list, like a->b, b->c, b->d, c->e, d->e, return installation sequence e, c, d b, a.**

* **Given two sparse Vectors, compute the Dot Product.  
    Input Format:  
	The first line will contain two numbers(k and n), which are the number of entries for the two vectors respectively.  
	The next k lines are the entries for the first vector, of the form: x y where x is the position and y is the value at that position in the vector.  
	The n lines are the entries of the second vector.  
	Any entries not specified indicate zero at that position.  
	Two vectors will always be of the same length.  
	Example input:  
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3 3  
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 4  
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4 2  
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5 3  
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 7  
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 6  
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5 1  
	Sample answer: Dot Product = 4 * 7 + 3 * 1 = 31 (only print 31)**

* **Given a company name and rank number, sort the companies by their number.**

* **You have a dataset in a plain text file, and you basically have to data-structure-ize it, and sort it.**

* **You have a user-submitted review (basically just a paragraph of fish sentences). Design and write an algorithm to break up the review into sentences, and put it in a list/array data structure.**

* **Find a target value from a 2d array in which each row and column are sorted.**

* **Implement a cache (had growing requirements, such as a limit on how many things could be stored in it, and should return the most recently placed record).**

* **How to check if a bunch of braces are balanced and how to make the check faster.**

* **Check if a string is a palindrome. Print true or false.**

* **Implement a function to take a collection of SET cards and identify a set if it exists or return a error status or something similar if it does not. This is according to the rules of the game “SET” which you should look up for context.**

* **Subtract two strings.**

* **Given a list of threads with a start time and finish time, determine all the threads with overlapping times.**

* **Create a cache for data on a webpage to avoid calling the server whenever possible.**

* **Stack vs Heap.**

* **How would you make a Spam detector for Yelp given all the data.**

* **Implement regex.**

* **Print Pascal Triangle for a number.**

* **Given a string, find the longest string with unique characters.**

* **Give a list of urls, find the top 10 most visited urls.**

* **Implement the ‘cd’ command. i.e. Given a function cd(‘a/b’, ‘c/../d/e/../f’), where 1st parameter is current directory and 2nd parameter is the sequence of operations, find the final directory that the user will be in when the cd command is executed.**

* **Find the sum of two integers represented as strings, return the sum as string, i.e “123” and “456” would return “579”.**

* **Find prime factors of a number.**

* **How to find the only different number in two unsorted arrays?**

* **How to design a request dispatcher for load balancing.**

* **Write code to generate all possible case combinations of a given lower-cased string. e.i “0ab” -> [“0ab”, “0aB”, “0Ab”, “0AB”])**

* **Find the maximum number of segments that could fit on a number line given a list of segments.**

* **Given a number of nodes and a number of edges, write a method to generate a random graph.**

* **Longest Palindrome substring on leetcode.**

* **Split shifted linked list into two sorted lists.**

* **Given a list of strings, write a function to calculate the longest common prefix (LCP) of all those strings.**

* **Given a URL, how do you find a phone number in it?**

* **Adding element to first of linked list. Complexity?**

* **What is a heap tree?**

* **How do you find and replace a phone number from huge list of files.**

* **How to design a MapReduce job for Yelp.**

* **Array vs LinkedList.**

* **Write a function that takes as input an array of words and returns a sorted array.**

* **How to resolve deadlock?**

* **Implement a lock.**

* **Given a big list of searches, how would you write a function that returns top 10 searches?**

* **Generate all permutations of an alphanumeric string.**

* **Get the least common ancestor of a binary tree.**

* **How to merge two arrays?**

* **How to determine if an Array of integers contains 3 numbers that sum to 0?**

### [](id:FrontEnd)Front End

* **What happens after sending an HTTP get request to yelp.com**

* **What might be the possible reasons of slow network connection?**

* **HTTP, HTTPS, IP, UDP, SSL, TCP, DNS.**  
	* **HTTP (Hypertext Transfer Protocol)** - the way a Web server communicates with browsers. Lets visitors view a site and send information back to the Web server.  
	* **HTTPS (Hypertext Transfer Protocol Secure)** - is HTTP through a secured connection. Communications through an HTTPS server are encrypted by a secure certificate 		known as an SSL.  
	* **SSL (Secure Sockets Layer)** - is a security protocol. Standard security technology for establishing an encrypted link between a server and a client.  
	* **TCP (Transmission Control Protocol)** - basic communication language or protocol of the Internet.  
	* **UDP (User Datagram Protocol)** - communications protocol that offers a limited amount of service when messages are exchanged between computers in a network that 		uses the Internet Protocol (IP)  
	* **IP (Internet Protocol)** - an address of a computer or other network device on a network using TCP/IP.  

* **Protocol underneath HTTP?**  
	Transmission Control Protocol (transport layer protocol).

* **What is the port for Telnet.**  
	23

* **Explain DNS resolution.**  
	Translation of a unique IP address in textual form to an actual IP address. The program contacts a DNS server that returns the translated IP address.

* **Threading practices, simple networking stuff, compression, encryption.**

* **Why are some websites slow?**

* **If a request takes too long, what could be the reason?**

* **Describe the different steps when a form is posted.**

* **What is the protocol used underneath FPT?**

* **Difference POST / GET?**

* **How do cookies work?**  
	**What?**  
	Cookies are simple text files that typically contain two pieces of information: a site name and unique user ID.

    **How?**  
	Cookie is downloaded onto PC when a user visits a site that uses cookies for the first time. Next visit, PC checks if it has a cookie that is relevant and sends the 	information contained in that cookie back to the site.

* **URL shortener script.**

* **What to do if URL is already int the DB.**

* **What to do to get analytics?**

* **How can you know from which website your user is coming?**

* **Write a function that outputs a string that shows pagination information for a website. The string must show the current page, lowest page index, highest page index, 	with some “padding” around the current page.  
	Example output:  
	‘1 … 4 5 (6) 7 8 … 30’ for a site with 30 pages where the user is on page 6.  
	‘1 (2) 3 4 … 30’ for a site with 30 pages where the user is on page 2.**

* **Given a telephone directory which is broken in number of files, how could you find a telephone number in it.**  
	Grep

* **How might you keep track of where users were coming from to get to your site?**


### [](id:Database)Database

* **Design database tables of Yelp.**

* **What is SQL?**  
	Structured Query Language is used to communicate with a database.

* **How to remove a row in SQL.**

	```
	DELETE FROM "table_name"
	WHERE "condition";
	```

* **Will adding more indexes to a database improve performance?**

* **Make an image slideshow form a bunch of URLs in a MySQL database.**

* **All the joins and indexing.**

* **What is the command to delete a table in MySQL.**

* **Inner join is what? A union B, A intersect B and A - B.**

* **What can be done to speed up a select query.**

* **You have a table with user information like name, age, and sex. Give a smart way to sort the entries based on age.**

### [](id:Java)Java

* **How does Java GC work, and how to implement GC.**

* **What is inline function?**  
	Inline functions are a lot like a placeholder. Once you define an inline function, using the 'inline' keyword, whenever you call that function the compiler will replace the function call with actual code from the function. The purpose of inline function is to reduce the function call overhead.
	
	```
#include <iostream>
using namespace std;
inline void hello() {
	cout << "hello";
}
int main() {
	hello(); // call it like a normal function
	cin.get();
}
	```

* **Describe why compiler does not perform inline in some circumstances.**
	1. If a function contains a loop. (for, while, do-while)
	2. If a function contains static variables.
	3. If a function is recursive.
	4. If a function return type is other than void, and the return statement doesn't exist in function body.
	5. If a function contains switch or goto statement.
	
	Advantages of inline?
	1. Function call overhead doesn't occur.
	2. It also saves the overhead of push/pop variables on the stack when function is called.
	3. It also saves overhead of a return call from a function.
	4. When you inline a function, you may enable compiler to perform context specific optimization on the body of function. Such optimizations are not possible for normal function calls. Other optimizations can be obtained by considering the flows of calling context and the called context.
	5. Inline function may be useful (if it is small) for embedded systems because inline can yield less code than the function call permeable and return.
	
	Why?
	1. The added variables from the inlined function consumes additional registers.
	2. If you use too many inline functions then the size of the binary executable file will be large, because of the duplication of some code.
	3. Too much inlining can also reduce your instruction cache hit rate, thus reducing the speed of instruction fetch from that of the cache memory to that of primary memory.
	4. Inline function may increase compile time overhead if someone changes the code inside the inline function then all the calling location has to be recompiled because compiler would require to replace all the code once again to reflect changes, otherwise it will continue with old functionality.
	5. Inline functions may not be useful for many embedded systems. Because in embedded systems code size is more important than speed.
	6. Inline functions might cause thrashing because inlining might increase size of the binary executable file. Thrashing in memory causes performance of computer to degrade.

### [](id:OS)Operating System

* **Describe about process and thread.**

* **How does process communicate with each other?**

* **What are the different synchronization mechanisms?**

* **Difference between semaphore and mutex.**

### [](id:Unix)Unix

* **What is the command in unix to find IP configuration information.**  
	ifconfig

* **Linux command to get the ip address from a hostname.**  
	nslookup <hostname>

* **Can you list the top 10 queries that you think we see the most for our (Yelp) search results?**  
	[Queries](http://www.unix.com/unix-dummies-questions-answers/42789-searching-displaying-most-commonly-used-words.html)

* **Wordcount**  
	wc <filename>

* **Finding out process information.**  
	ps

* **How to find hidden files in current directory?**  
	ls -lrta

* **How to find current running processes in unix server?**  
	ps -ef  
	ps -ef | grep -i <application> (if we want to find specific process we can use 'grep' with pipe)

* **How to find process which is taking maximum memory in server?**  
	top  
	top command tells us about cpu usage, process id and other details.

* **How to find Exception in log files available in current directory and how to find number of occurrence?**  
	grep <Exception> log1.txt | wc -l

* **Find all files in current and subdirectories which contains 'log' name?**  
	find . -name <log>

* **How to find remaining disk space in unix/linux server?**  
	df -kl

* **How to make any script file executable?**  
	chmod 755 *.sh

* **How to kill process in unix server?**  
	kill -9 #pid






