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


* **Design a method to find the frequency of occurrences of any given word in a book**

```
public class FrequencyWord {
	public static Hashtable<String, Integer> setupDictionary(String[] book) {
		Hashtable<String, Integer> table = new Hashtable<String, Integer>();
		
		for (String word : book) {
			word = word.toLowerCase();
			
			if (word.trim() != "") {
				if (!table.contains(word)) {
					table.put(word, 0);
				}
				
				table.put(word, table.get(word) + 1);
			}
		}
		
		return table;
	}
	
	public static int getFrequency(Hashtable<String, Integer> table, String word) {
		if (table == null || word == null) {
			return -1;
		}
		
		word = word.toLowerCase();
		
		if (table.contains(word)) {
			return table.get(word);
		}
		
		return 0;
	}
	
	public static void main(String[] args) {
		String[] wordlist = AssortedMethods.getLongTextBlobAsStringList();
		Hashtable<String, Integer> dictionary = setupDictionary(wordlist);
		
		String[] words = {"the", "Lara", "and", "outcropping", "career", "it"};
		
		for (String word : words) {
			System.out.println(word + ": " + getFrequency(dictionary, word));
		}
	}
}
```


* **How to check if two Strings are anagram?**

```
public class AnagramCheck {
	public static boolean isAnagram(String word, String anagram) {
		if (word.length() != anagram.length())
			return false;
		
		char[] chars = word.toCharArray();
		
		for (char c : chars) {
			int index = anagram.indexOf(c);
			
			if (index != -1) {
				anagram = anagram.substring(0, index) + anagram.substring(index + 1, anagram.length());
			} else {
				return false;
			}
		}
		
		return anagram.isEmpty();
	}
	
	public static boolean checkAnagram(String word, String anagram) {
		if (word.length() != anagram.length())
			return false;
		
		char[] chars = word.toCharArray();
		StringBuilder sbAnagram = new StringBuilder(anagram);
		
		for (char c : chars) {
			int index = sbAnagram.indexOf("" + c);
			
			if (index != -1) {
				sbAnagram.deleteCharAt(index);
			} else {
				return false;
			}
		}
		
		return sbAnagram.length() == 0;
	}
}
```


* **How to convert numeric String to int in Java?**

```
public class StringToInt {
	public static int convertToInt(String numString) {
		int length = numString.length() - 1;
		int num = 0;
		
		for (int i = length; i >= 0; i--) {
			num += ((numString.codePointAt(i) - 48) * Math.pow(10, length - i));
		}
		
		return num;
	}
	
	public static void main(String[] args) {
		System.out.println(convertToInt("123"));
	}
}
```


* **Difference between String, StringBuilder, and StringBuffer in Java.**

* **Why String is final in Java?**

* **Why char array is preffered over String for storing password?**


### [](id:Array)Array Programming Questions

* **In an array 1-100 numbers are stored, one number is missing. How would you find it?**

```
public class MissingNumberInArray {
	public static int getMissingNumber(int[] numbers) {
		int totalCount = numbers.length + 1;
		int expectedSum = totalCount * (totalCount + 1) / 2;
		int actualSum = 0;
		
		for (int i : numbers) {
			actualSum += i;
		}
		
		return expectedSum - actualSum;
	}
	
	public static void printMissingNumbers(int[] numbers, int count) {
		int missingCount = count - numbers.length;
		BitSet bitSet = new BitSet(count);
		
		for (int number : numbers) {
			bitSet.set(number - 1);
		}
		
		int lastMissingIndex = 0;
		
		for (int i = 0; i < missingCount; i++) {
			lastMissingIndex = bitSet.nextClearBit(lastMissingIndex);
			System.out.println(++lastMissingIndex);
		}
	}
	
	public static void main(String[] args) {
		printMissingNumbers(new int[]{1, 2, 3, 4, 9, 8}, 10);
	}
}
```


* **In an array, how would you check if there are any duplicates?**

```
public class DuplicatesInArray {
	public static boolean checkDuplicates(String[] input) {
		Set<String> tempSet = new HashSet<String>();
		
		for (String str : input) {
			if (!tempSet.add(str))
				return true;
		}
		
		return false;
	}
	
	public static void main(String[] args) {
		String[] duplicates = new String[] {"one","two","three","one"};
		System.out.println(checkDuplicates(duplicates));
	}
}
```


* **How do you find second highest number in an integer array? Or find the top two maximum number in an array. (Cannot use any sorting function and can only iterate once)**

```
public class TopTwoMaximum {
	public static void  topTwo(int[] numbers) {
		int max1 = Integer.MIN_VALUE;
		int max2 = Integer.MIN_VALUE;
		
		for (int number : numbers) {
			if (number > max1) {
				max2 = max1;
				max1 = number;
			} else if (number > max2) {
				max2 = number;
			}
		}
		
		System.out.println(max2);
	}
	
	public static void main(String[] args) {
		topTwo(new int[]{20, 34, 21, 87, 92, Integer.MAX_VALUE});
        topTwo(new int[]{0, Integer.MIN_VALUE, -2});
        topTwo(new int[]{Integer.MAX_VALUE, 0, Integer.MAX_VALUE});
        topTwo(new int[]{1, 1, 0});
	}
}
```


* **How to find all pairs in array of integers whose sum is equal to given number?**

```
public class PairsInArrayToSum {
	public static void printPairsInefficient(int[] array, int sum) {
		for (int i = 0; i < array.length; i++) {
			int first = array[i];
			
			for (int j = i + 1; j < array.length; j++) {
				int second = array[j];
				
				if (first + second == sum)
					System.out.println(first + " " + second);
			}
		}
	}
	
	public static void printPairsSlightlyEfficient(int[] array, int sum) {
		if (array.length < 2)
			return;
		
		Set<Integer> set = new HashSet<Integer>();
		
		for (int number : array) {
			int target = sum - number;
			
			if (!set.contains(target))
				set.add(number);
			else
				System.out.println(number + " " + target);
		}
	}
	
	public static void printPairsEfficient(int[] array, int sum) {
		if (array.length < 2)
			return;
		
		Arrays.sort(array);
		
		int left = 0;
		int right = array.length - 1;
		
		while (left < right) {
			int pairSum = array[left] + array[right];
			
			if (sum == pairSum) {
				System.out.println(array[left] + " " + array[right]);
				left++;
				right--;
			} else if (pairSum < sum) {
				left++;
			} else if (pairSum > sum) {
				right--;
			}
		}
	}
	
	public static void main(String[] args) {
		printPairsInefficient(new int[]{12, 14, 17, 15, 19, 20, -11}, 9);
		printPairsSlightlyEfficient(new int[]{12, 14, 17, 15, 19, 20, -11}, 9);
		printPairsEfficient(new int[]{12, 14, 17, 15, 19, 20, -11}, 9);
	}
}
```


* **How to remove duplicate elements from array?**

```
public class RemoveDuplicatesInArray {
	public static int[] removeDuplicates(int[] array) {
		Arrays.sort(array);
		int count = 0;

		for (int i = 0; i < array.length; i++) {
			if (i + 1 < array.length && array[i] == array[i + 1])
				count++;
		}

		int[] arrayNoDuplicates = new int[array.length - count];
		int index = 0;

		for (int i = 0; i < array.length; i++) {
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


### [](id:LinkedList)LinkedList Programming Question

* **How do you find a middle element of a LinkedList in a single pass?**

```
public class FindMidOfLL {
	public static int findMid(LinkedListNode head) {
		LinkedListNode fast = head;
		LinkedListNode slow = head;
		int length = 0;
		
		while (fast.next != null) {
			length++;
			fast = fast.next.next;
			slow = slow.next;
		}
		
		if (length % 2 == 1) {
			slow = slow.next;
		}
		
		return slow.data;
	}
}
```


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































