<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## Top 30 Programmig Questions

* [String Programming Questions](#String)
* [Array Programming Questions](#Array)
* [LinkedList Programming Questions](#LinkedList)
* [Binary Tree Programming Questions](#BinaryTree)
* [Searching and Sorting Programming Questions](#SearchingSorting)
* [Numbers Programming Questions](#Numbers)
* [General Programming Questions](#General)

### [](id:String)String Programming Questions

* **Write a code to check if a String is a palindrome or not.**

```
public class PalindromeString {
	public static boolean isPalindrome(String str) {
		if (str.isEmpty())
			return true;
		
		str = str.replaceAll("[^A-Za-z]", "").toLowerCase();
		
		String reverse = new StringBuilder(str).reverse().toString();
		
		if (str.equals(reverse))
			return true;
		else
			return false;
	}
	
	public static boolean isPalindrome2(String str) {
		if (str.isEmpty())
			return true;
		
		str = str.replaceAll("[^A-Za-z]", "").toLowerCase();
		
		int start = 0;
		int end = str.length() - 1;
		int mid = (start + end) / 2;
		
		for (int i = start; i <= mid; i++) {
			if (str.charAt(start) == str.charAt(end)) {
				start++;
				end--;
			} else {
				return false;
			}
		}
		
		return true;
	}
	
	public static void main(String[] args) {
		System.out.println(isPalindrome("A Toyota’s a Toyota."));
		System.out.println(isPalindrome2("A man, a plan, a canal: Panama."));
	}
}
```

* **Write a method which will remove any given character from a String.**

```
public class RemoveCharFromString {
	public static String removeChar(String str, char c) {
		if (str == null)
			return null;
		
		return str.replaceAll("(?i)" + Character.toString(c), "");
	}
	
	public static void main(String[] args) {
		System.out.println(removeChar("Rabbits raced really rapid.", 'r'));
	}
}
```


* **Print all permutation of String both iterative and Recursive way.**

```
public class PermutationOfString {
	public static void permutationRecursive(String str) {
		permutationRecursive("", str);
	}
	
	private static void permutationRecursive(String prefix, String str) {
		int N = str.length();
		
		if (N == 0) {
			System.out.println(prefix);
		} else {
			for (int i = 0; i < N; i++) {
				permutationRecursive(prefix + str.charAt(i), str.substring(0, i) + str.substring(i + 1, N));
			}
		}
	}
	
	public static void permutationIterative(String str) {
		System.out.println(str);
		char[] a = str.toCharArray();
		int N = a.length;
		int[] p = new int[N];
		int i = 1;
		
		while (i < N) {
			if (p[i] < i) {
				int j = ((i % 2) == 0) ? 0 : p[i];
				swap(a, i, j);
				System.out.println(join(a));
				p[i]++;
				i = 1;
			} else {
				p[i] = 0;
				i++;
			}
		}
	}
	
	private static String join(char[] a) {
		StringBuilder builder = new StringBuilder();
		builder.append(a);
		return builder.toString();
	}
	
	private static void swap(char[] a, int i, int j) {
		char temp = a[i];
		a[i] = a[j];
		a[j] = temp;
	}
	
	public static void main(String[] args) {
		permutationRecursive("cat");
		permutationIterative("cat");
	}
}
```

* **Given two strings, s1 and s2, write code to check if s2 is a rotation of s1 using only one call to subString.**

```
public class TwoStringPermutationCheck {
	public static boolean isSubstring(String s1, String s2) {
		if (s1.length() != s2.length())
			return false;
		
		String s1s1 = s1 + s1;
		
		if (s1s1.indexOf(s2) != -1)
			return true;
		
		return false;
	}
	
	public static void main(String[] args) {
		System.out.println(isSubstring("hello", "lohel"));
		System.out.println(isSubstring("camera", "macera"));
	}
}
```


* **Write a function fo find out the longest palindrome in a given String.**

* **How to find first non repeated character of a given String?**

```
public class FirstNonRepeatedChar {
	public static char firstNonRepeatedCharacterLinkedHashMap(String word) {
		Map<Character, Integer> counts = new LinkedHashMap<Character, Integer>();
		
		for (char c : word.toCharArray()) {
			counts.put(c, counts.containsKey(c) ? counts.get(c) + 1 : 1);
		}
		
		for (Entry<Character, Integer> entry : counts.entrySet()) {
			if (entry.getValue() == 1) {
				return entry.getKey();
			}
		}
		
		throw new RuntimeException("didn't find any non repeated Character");
	}
	
	public static char firstNonRepeatedCharacter(String word) {
		Set<Character> repeating = new HashSet<Character>();
		List<Character> nonRepeating = new ArrayList<Character>();
		
		for (int i = 0; i < word.length(); i++) {
			char c = word.charAt(i);
			
			if (repeating.contains(c)) {
				continue;
			}
			
			if (nonRepeating.contains(c)) {
				nonRepeating.remove((Character) c);
				repeating.add(c);
			} else {
				nonRepeating.add(c);
			}
		}
		
		return nonRepeating.get(0);
	}
	
	public static char firstNonRepeatedCharacterHashMap(String word) {
		HashMap<Character, Integer> map = new HashMap<Character, Integer>();
		
		for (int i = 0; i < word.length(); i++) {
			char c = word.charAt(i);
			
			if (map.containsKey(c)) {
				map.put(c, map.get(c) + 1);
			} else {
				map.put(c, 1);
			}
		}
		
		for (int i = 0; i < word.length(); i++) {
			char c = word.charAt(i);
			
			if (map.get(c) == 1) {
				return c;
			}
		}
		
		throw new RuntimeException("Undefined behaviour");
	}
}
```


* **How to count occurence of a given character in a String?**

* **How to check if two Strings are anagram?**

* **How to convert numeric String to int in Java?**

* **Difference between String, StringBuilder, and StringBuffer in Java.**

* **Why String is final in Java?**

* **How to split String in Java?**

* **Why char array is preffered over String for storing password?**


### [](id:Array)Array Programming Questions

* **In an array 1-100 numbers are stored, one number is missing. How would you find it?**

* **In an array 1-100, exactly one number has a duplicate. How would you find it?**

* **Given two arrays [1, 2, 3, 4, 5] and [2, 3, 1, 0, 5], find which number is not present in the second array.**

* **How do you find second highest number in an integer array?**

* **How to find all pairs in array of integers whose sum is equal to given number?**

* **How to remove duplicate elements from array in Java?**

* **How to find largest and smallest number in array?**

* **How to find top two-maximum number in array?**


### [](id:LinkedList)LinkedList Programming Question

* **How do you find a middle element of a LinkedList in a single pass?**

* **How do you find 3rd element from last in single pass?**

* **How do you find if there is any loop in a singly LinkedList? How do you find the start of the loop?**

* **How do you reverse a singly LinkedList?**

* **Difference between a LinkedList and Array data structure.**


### [](id:BinaryTree)Binary Tree Programming Questions

* **How do you find depth of a binary tree?**

* **Write code to print InOrder traversal of a tree.**

* **Print out all leaf node of a binary tree.**

* **Write a method to check if a tree is a binary search tree or not.**

* **How to check if a tree is balanced or not?**


### [](id:SearchingSorting)Searching and Sorting Programming Questions

* **Write a program to sort numbers in place using quick sort.**

* **Write a program to implement binary search algorithm.**

* **How do you sort Java objects using Comparator?**

* **Write code to implement Insertion Sort.**

* **Write code to implement Bubble Sort.**


### [](id:Numbers)Numbers Programming Question

* **Write code to check whether a number is power of two or not.**

* **Write a program to check whether a number is a palindrome or not.**

* **Write code to check whether an integer is an Armstrong number or not.**

* **Write a program to find all prime numbers up to a given number.**

* **Write a function to compute nth Fibonacci sequence. Both iterative and recursive.**

* **How to check if a number is binary?**

* **How to reverse an integer?**

* **How to count the number of set bits in given integer?**

* **How to find the sum of digits of a number using recursion?**

* **How to swap two numbers without using temp variable?**

* **How to find largest of three integers?**

* **Write a program to find prime factors of integer.**

* **How to add two integers without using arithmetic operator?**


### [](id:General)General Programming Questions

* **Write a program to find out if two rectangles R1 and R2 are overlapping.**

* **You need to write a function to climb n steps. You can climb either 1 step at a time or 2 steps at a time. Write a function to return the number of ways to climb a ladder with n step.**

* **Write code to Generate Random numbers in a range from min to max.**

* **Write a program for word-wrap which should work on any screen size.**

* **Design an algorithm to find the frequency of occurence of a word in an article.**

* **Write a program to implement blocking queue.**

* **Write a program for producer-consumer problem.**































