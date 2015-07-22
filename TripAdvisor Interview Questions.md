TripAdvisor Interview Questions
===============================

1. **Given an array of non negative integers, and a non negative sum, write a method that returns the total number of pairs of integers that add up to the sum. The array can contain repeated numbers.**  
TwoSumProblem

* **Given a list of coins and the total amount. Calculate the minimum number of coins can be used to reach the total amount.**  
CoinChange

* **Implement a function on a binary search that receives two nodes and returns its common ancestor.**  
LowestCommonAncestorBST

* **Code conway's game of life.**  
ConwaysGameOfLife

* **Verify if a binary tree is a binary search tree.**  
CheckBST

* **Implement a queue using stacks.**  
QueueStack

* **Convert an int to a string without casting.**  
Itoa

* **Write a tic tac toe game.**  
TicTacToe

* **Intersect two sorted list.**  
IntersectionOfTwoSortedArrays

* **Count number of islands of 1s in a 1/0 matrix.**  
NumberOfIslands (Not finished)

* **Given an array of positive integers, find how much water it would hold (twitter waterfall question).**  
TwitterWaterfall

* **Given a string, find the first char that only appears once. (both iterative & recursion way).**  
FirstNonRepeatedChar

* **Find number of pairwise elements in an array with difference k.**  
PairsWithDifferenceK

* **Write a method that counts the number of enabled bits in an integer.**  
CountSetBitsInteger

* **How to find the closest common ancestor of two nodes in a binary search tree.**  
LowestCommonAncestorBST

* **Convert user input to Roman Number.**  
IntegerToRoman

* **Sort an array of integers.**  
MergeSort, QuickSort

* **Find the merge point of two linked list.**  
IntersectionOfTwoLinkedList

* **Design a LRU Cache.**  
LRU

* **Detect if a string is a palindrome. What if there is whitespace in the string. Constraint : you can't trim the spaces out or pull anything out of the string. Must be checked in place.**  
PalindromeString

* **What is a hashtable? How to implement? Any advantages and disadvantages? What is the requirement of hash function?**  
HashTable is a data structure used to implement an associative array, a structure that can map keys to values. A hash table uses a hash function to compute an index into an array of buckets or slots, from which the correct value can be found.  
HashTable  

	**Advantages**  
	* Speed. Very efficient when the maximum number of entries can be predicted in advance, so that the bucket array can be allocated once with the optimum size and never resized.
	* Good hash function that is collision-free.
	
	**Disadvantages**
	* Effective hash function for a specific application is more an art than a science.
	* Are not very effective when the number of entries is very small.
	* For certain string processing applications, such as spell-checking, hashtables may be less efficient than tries, finite automata, or Judy arrays.
	* If the keys are not stored, there may be no easy way to enumerate the keys that are present in the table at any given moment.
	* Inefficient when there are many collisions.  
  
	**Requirements of hash function**
	* Uniformity - A good hash function should map the expected inputs as evenly as possible over its output range. That is, every hash value in the output range should be generated with roughly the same probability.
	* Determinism - It must be a function of the data to be hashed, in the mathematical sense of the term.
	* Non-invertible - It is not realistic to reconstruct the input datum x from its hash value h(x) alone without spending great amounts of computing time.
	* Data normalization - In some applications, the input data may contain features that are irrelevant for comparison purposes. For example, when looking up a personal name, it may be desirable to ignore the distinction between upper and lower case letters.

* **Level print binary tree (queue).**  
BinaryTree -> LevelOrderTraversal

* **Get number of 1's in the binary presentation of an integer.**  
CountSetBitsInteger

* **What's the difference between for and foreach?**  
If I use a linked list, use 'for' and 'a.get(index)' would take O(n^2) time complexity.

* **Write a function to reverse a linked list using recursion.**  
ReverseLinkedList

* **Insert an element in a linked list.**  
InsertElementSinglyLinkedList

* **Find the next larger node of a node in a binary search tree.**  
BinaryTree -> NextLargerNode

* **Count duplicates in a binary search tree.**  
BinaryTree -> CountDuplicatesBST

* **What is the difference between array and linked list.**

	| Array | Linked List |
	|:-----:|:-----------:|
	| Size is fixed | Dynamic size |
	| Inserting new element is expensive | Ease of insertion / deletion |
	| Random access is allowed | Random access is not allowed |
	| Better cache locality which affects performance | Extra memory space for a pointer for each element of the list |

* **What if you had the worst hash function ever. What is the complexity of lookup?**  
O(n)

* **Write a routine to print the numbers 1 to 100 and back to 1 again without using any loops.**  
PrintNumbersWithoutLoops

* **When is balanced tree is better than hashtable?**  
	* When there are too many collisions in the hashtable.
	* When you need the items in a sorted order.

* **What are properties of a good hash?**  
	* The hash value is fully determined by the data being hashed.
	* The hash function uses all the input data.
	* The hash function "uniformly" distributes the data across the entire set of possible hash values.
	* The hash function generates very different hash values for similar things.

* **Assume there are duplicate values in a BST containing integers. Please write countDups() and return an int for the count of duplicate values in the tree (the number of nodes to remove to make the tree contain unique values only).**  
BinaryTree -> CountDuplicatesBST

* **Write a function that raises a number to an exponent.**  
Exponent

* **Given two strings; boston and obtons how can you determine that they, and any other set of strings, are anagrams of each other. Try and make it as efficient as possible.**  
AnagramCheck

* **Other than an array, what data structure has O(1) insertion and O(1) search?**  
HashTable

* **Check if a tree is symmetric.**  
SymmetricTree

* **Write a web crawler to count number of pages in a website.**  
WebCrawler

* **You have a fixed list of words, construct a data structure to achieve efficient O(1) time complexity prefix lookup. Write code to implement the lookup. For example, the result of looking up "app" is {apple, applications, ..}.**

* **You have one billion numbers, implement getRandom() which returns a random number from them. Constraints : 1. No duplicate returning value. 2. getRandom() will at most be invoked 100 million times. Then optimize for space.**

* **How would you implement a bit vector data structure? Optimizing for memory?**

* **Given a flat text file that contains a range of IP addresses that map to a location (e.g. 192.168.0.0 - 192.168.0.255 = Boston, MA), come up with an algorithm that will find a city for a specific IP address if a mapping exists.**

* **Given a tree of world regions, locations, and specific destinations and attractions, find the most efficient ways to determine the common parent of two arbitrary nodes in terms of space and time.**

* **How can you tell efficiently how many consecutive zero's are in a number without looping through its digits.**

* **How many dates in the 1900's in the form mm/DD/yy are palindromes?**

* **Write a function to reverse a string in the most memory efficient way? What happens if have an odd length string? What is immutable and mutable strings?**

* **Implement insert() and findSumAtLevel(int n) for a binary search tree.**

* **Given a BST with leaf nodes having a numeric value, and nodes having the sum of values of its two children. Find an algorithm to find the maximum node within a tree.**

* **NP complete problem.**

* **If you can do unlimited pre-processing, how would you find the lowest common ancestor of any two nodes in a tree, in O(1) time?**

* **Find the kth largest number in 2 sorted arrays.**

* **Given a binary tree with key, value pairs, write a function that duplicates the tree and changes the value at one of the keys.**

* **Given a singly linked list of characters, remove all numeric values from the linked list and return it.**

* **Select the elements from a SQL table where an aggregate function meets a certain condition.**

* **Write code for a binary tree who find the lowest node and bubbles it up to the root.**

* **Given an array of values, how do you check if there is a combination of them that add up to an integer, n.**

* **Given an input stream of an indeterminate length, how do you return a random member of that stream (with equal probability for each), given that you're not allowed to store more than a constant number of inputs, and you can only go through the inputs once.**

* **Get a sub list of a linked list indexed by fibonacci numbers.**

* **Given a csv file containing all the hotel deals, find the best deal according to the check date and stay nights.**

* **Write a function to remove repeated spaces from a string.**

* **You have String 1 : "abcdefgh". Write a code to remove "ad" so that you are left with "bcefgh".**
