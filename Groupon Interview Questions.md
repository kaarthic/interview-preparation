<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

### Groupon Interview Questions

* **How to know if a Linked List has a loop?**

```
public class LinkedListLoop {
	public static boolean detectLoop(LinkedListNode head) {
		LinkedListNode slow = head;
		LinkedListNode fast = head;
		
		while (fast != null && fast.next != null) {
			slow = slow.next;
			fast = fast.next.next;
			
			if (slow == fast) {
				return true;
			}
		}
		
		return false;
	}
}
```


* **How to find all permutations of an array?**

```
public class ArrayPermutations {
	public static ArrayList<ArrayList<Integer>> getPermutations(int[] num) {
		ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
		
		result.add(new ArrayList<Integer>());
		
		for (int i = 0; i < num.length; i++) {
			ArrayList<ArrayList<Integer>> current = new ArrayList<ArrayList<Integer>>();
			
			for (ArrayList<Integer> list : result) {
				for (int j = 0; j < list.size() + 1; j++) {					
					ArrayList<Integer> temp = new ArrayList<Integer>(list);
					temp.add(j, num[i]);
					current.add(temp);
				}
			}
			
			result  = current;
		}
		
		return result;
	}
	
	public static ArrayList<ArrayList<Integer>> permute(int[] num) {
		ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
		permute(num, 0, result);
		return result;
	}
	
	public static void permute(int[] num, int start, ArrayList<ArrayList<Integer>> result) {
		if (start >= num.length) {
			ArrayList<Integer> item = convertArrayToList(num);
			result.add(item);
		}
		
		for (int i = start; i <= num.length - 1; i++) {
			swap(num, start, i);
			permute(num, start + 1, result);
			swap(num, start, i);
		}
	}
	
	private static ArrayList<Integer> convertArrayToList(int[] num) {
		ArrayList<Integer> item = new ArrayList<Integer>();
		
		for (int i = 0; i < num.length; i++) {
			item.add(num[i]);
		}
		
		return item;
	}
	
	private static void swap(int[] a, int i, int j) {
		int temp = a[i];
		a[i] = a[j];
		a[j] = temp;
	}
	
	private static int permutation(int n) {
		int result = 1;
		
		for (int i = 1; i <= n; i++)
			result *= i;
		
		return result;
	}
	
	public static void main(String[] args) {
		int[] array = {1, 2, 3};
		int permutation = permutation(array.length);
		System.out.println(permutation);
		System.out.println(permutation == getPermutations(array).size());
		System.out.println(getPermutations(array));
		System.out.println(permute(array));
	}
}
```


* **Given two eggs and a 100 floored building, how can you try lowest amount of time to decide the highest floor it will break?**

* **Reimplement a hash class with arrays.**

```
public class HashTable<K, V> {
	private double LOAD_FACTOR = 0.75;
	private Entry[] table;
	private int elementCount;
	private final int DEFAULT_SIZE = 10;
	
	public class Entry {
		private K key;
		private V value;
		private Entry next;
		
		public Entry(K key, V value) {
			this.key = key;
			this.value = value;
		}
		
		public K getKey() {
			return key;
		}
		
		public V getValue() {
			return value;
		}
		
		public void setValue(V value) {
			this.value = value;
		}
		
		public Entry next() {
			return next;
		}
		
		public void setNext(Entry entry) {
			this.next = entry;
		}
	}
	
	public HashTable() {
		elementCount = 0;
		table = (Entry[]) Array.newInstance(Entry.class, DEFAULT_SIZE);
	}
	
	public HashTable(int size) {
		elementCount = 0;
		table = (Entry[]) Array.newInstance(Entry.class, size);
	}
	
	public static int hash(int h) {
		h ^= (h >>> 20) ^ (h >>> 12);
		return h ^ (h >>> 7) ^ (h >>> 4);
	}
	
	public void put(K key, V value) {
		if (elementCount > table.length * LOAD_FACTOR)
			resize();
		
		int index = hash(key.hashCode()) % table.length;
		
		if (table[index] == null) {
			table[index] = new Entry(key, value);
		} else {
			Entry current = table[index];
			
			while (true) {
				if (current.getKey().equals(key)) {
					current.setValue(value);
					break;
				}
				
				if (current.next == null)
					break;
				
				current = current.next();
			}
			
			current.setNext(new Entry(key, value));
			elementCount++;
		}
		
	}
	
	public boolean containsValue(V value) {
		Entry current = table[0];
		
		while (true) {
			if (current.getValue().equals(value)) {
				return true;
			}
			
			if (current.next == null) {
				return false;
			}
			
			current = current.next();
		}
	}
	
	public boolean containsKey(K key) {
		int index = hash(key.hashCode()) % table.length;
		
		if (table[index] != null)
			return true;
		
		return false;
	}
	
	public V get(K key) {
		int index = hash(key.hashCode()) % table.length;
		
		if (table[index] == null) {
			return null;
		} else {
			return table[index].getValue();
		}
	}
	
	public int size() {
		return elementCount;
	}
	
	public boolean isEmpty() {
		return elementCount == 0;
	}
	
	public void resize() {
		int newSize = (int) (table.length * 1.5);
		Entry[] newTable = (Entry[]) Array.newInstance(Entry.class, newSize);
		
		for (int i = 0; i < table.length; i++)
			newTable[i] = table[i];
		
		table = newTable;
	}
	
	public String toString() {
		String returnString = "{";
		
		for (int i = 0; i < table.length; i++) {
			if (table[i] != null)
				returnString += table[i].getKey() + "=" + table[i].getValue() + ", ";
		}
		
		return returnString.length() > 0 ? returnString.substring(0, returnString.length()-2) + "}" : "";
	}
}
```


* **Given a file with all user email addresses, design an algorithm that can automatically output random email address.**

* **Median of two sorted arrays.**

```
public class MedianTwoSortedArrays {
	public static int median(int[] array, int length) {
		if (length % 2 == 0)
			return (array[length / 2] + array[length / 2 - 1]) / 2;
		else
			return array[length / 2];
	}
	
	public static int max(int x, int y) {
		return x > y ? x : y;
	}
	
	public static int min(int x, int y) {
		return x > y ? y : x;
	}
	
	public static int getMedian(int[] arr1, int[] arr2, int n) {
		int m1;
		int m2;
		
		if (n <= 0)
			return -1;
		
		if (n == 1)
			return (arr1[0] + arr2[0]) / 2;
		
		if (n == 2)
			return (max(arr1[0], arr2[0]) + min(arr1[1], arr2[1])) / 2;
		
		m1 = median(arr1, n);
		m2 = median(arr2, n);
		
		if (m1 == m2)
			return m1;
		
		if (m1 < m2) {
			if (n % 2 == 0)
				return getMedian(Arrays.copyOfRange(arr1, n/2 - 1, arr1.length), arr2, n - n/2 + 1);
			else
				return getMedian(Arrays.copyOfRange(arr1, n/2, arr1.length), arr2, n - n/2);
		} else {
			if (n % 2 == 0)
				return getMedian(Arrays.copyOfRange(arr2, n/2 - 1, arr2.length), arr1, n - n/2 + 1);
			else
				return getMedian(Arrays.copyOfRange(arr2, n/2, arr2.length), arr1, n - n/2);
		}
	}
	
	public static int getMedian2(int[] arr1, int[] arr2, int n) {
		if (arr1[n-1] < arr2[0])
			return (arr1[n-1] + arr2[0]) / 2;
		
		if (arr2[n-1] < arr1[0])
			return (arr2[n-1] + arr1[0]) / 2;
		
		return getMedianRec(arr1, arr2, 0, n-1, n);
	}
	
	public static int getMedianRec(int[] arr1, int[] arr2, int left, int right, int n) {
		int i, j;
		
		if (left > right)
			return getMedianRec(arr2, arr1, 0, n-1, n);
		
		i = (left + right) / 2;
		j = n - i - 1;
		
		if (arr1[i] > arr2[j] && (j == n-1 || arr1[i] <= arr2[j+1])) {
			if (i == 0 || arr2[j] > arr1[i-1])
				return (arr1[i] + arr2[j]) / 2;
			else
				return (arr1[i] + arr1[i-1]) / 2;
		} else if (arr1[i] > arr2[j] && j != n-1 && arr1[i] > arr2[j+1]) {
			return getMedianRec(arr1, arr2, left, i-1, n);
		} else {
			return getMedianRec(arr1, arr2, i+1, right, n);
		}
			
	}
}
```


* **Write html to get pictures from web server and show them on the page.**

* **How to find the middle of a Linked List.**

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


* **What's the difference between HTML and HTML5?**
	
	* **Audio:**
		Audio is played without a plug-in.
	* **Video:**
		Video can be embedded in a Web page without plug-in.
	* **Motion:**
		Objects move on Web pages and react to the movements of a cursor.
	* **Storage:**
		Data can be stored on a user's computer or mobile device, so Web apps work without an internet connection.
	* **Type:**
		Web pages can have flashier type with more fonts, shadows, colors, and other effects.
	* **Games:**
		Interactive games can run with just a Web browser without installing other software or plug-ins.
	* **3D:**
		A technology called WebGL can create interactive 3-D effects using a computer's graphics processor.


* **Fibonacci Series.**

```
public class Fibonacci {
	public static int fibonacci(int i) {
		if (i == 0)
			return 0;
		
		if (i == 1)
			return 1;
		
		return fibonacci(i - 1) + fibonacci(i - 2);
	}
	
	public static int max = 100;
	public static int[] fib = new int[max];
	
	public static int fibonacciDP(int i) {
		if (i == 0)
			return 0;
		
		if (i == 1)
			return 1;
		
		if (fib[i] != 0)
			return fib[i];
		
		fib[i] = fibonacciDP(i - 1) + fibonacciDP(i - 2);
		return fib[i];
	}
}
```


* **Given x, find all the sets of four numbers adding up to x.**

```
public class FourElementsToSum {
	public static void findFourNumbers(int[] a, int n, int x) {
		int left, right;
		Arrays.sort(a);
		
		for (int i = 0; i < n - 3; i++) {
			for (int j = i + 1; j < n - 2; j++) {
				left = j + 1;
				right = n - 1;
				
				while (left < right) {
					if (a[i] + a[j] + a[left] + a[right] == x) {
						System.out.printf("%d, %d, %d, %d",a[i], a[j], a[left], a[right]);
						left++;
						right--;
					} else if (a[i] + a[j] + a[left] + a[right] < x) {
						left++;
					} else {
						right--;
					}
				}
			}
		}
	}
}
```

* **Remove white spaces in a string**

```
public class RemoveWhiteSpace {
	public static void removeWhiteSpace(String str) {
		str = str.replaceAll("\\s+", "");
	}
}
```


* **Puzzle on 25 horses.**

	Done


* **Design a system on a mobile device where it would return all local merchants shop location based on your location and the radius.**

* **2Sum problem. You have an unsorted array, and you are given a value S. Find all pairs of elements in the array that add up to value S.**

```
public class TwoSumProblem {
	public static ArrayList<ArrayList<Integer>> twoSumInefficient(int[] num, int sum) {
		ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
		
		for (int i = 0; i < num.length; i++) {
			for (int j = i; j < num.length; j++) {
				if (num[i] + num[j] == sum) {
					ArrayList<Integer> temp = new ArrayList<Integer>();
					temp.add(num[i]);
					temp.add(num[j]);
					result.add(temp);
				}
			}
		}
		
		return result;
	}
	
	public static ArrayList<ArrayList<Integer>> twoSumBetter(int[] num, int sum) {
		HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
		ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
		
		for (int i = 0; i < num.length; i++) {
			map.put(sum - num[i], i);
			
			if (map.containsKey(num[i])) {
				ArrayList<Integer> temp = new ArrayList<Integer>();
				temp.add(num[i]);
				temp.add(sum - num[i]);
				result.add(temp);
			}
		}
		
		return result;
	}
	
	public static ArrayList<ArrayList<Integer>> twoSumEfficient(int[] num, int sum) {
		ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
		Arrays.sort(num);
		
		int first = 0;
		int last = num.length - 1;
		
		while (first <= last) {
			int s = num[first] + num[last];
			
			if (s == sum) {
				ArrayList<Integer> temp = new ArrayList<Integer>();
				temp.add(num[first]);
				temp.add(num[last]);
				result.add(temp);
				
				++first;
				--last;
			} else {
				if (s < sum) {
					++first;
				} else {
					--last;
				}
			}
		}
		
		return result;
	}
	
	public static void main(String[] args) {
		int[] num = {9, 3, 6, 5, 7, -1, 13, 14, -2, 12, 0};
		ArrayList<ArrayList<Integer>> result = twoSumInefficient(num, 12);
		ArrayList<ArrayList<Integer>> result2 = twoSumBetter(num, 12);
		ArrayList<ArrayList<Integer>> result3 = twoSumEfficient(num, 12);
		
		System.out.println(result.toString());
		System.out.println(result2.toString());
		System.out.println(result3.toString());
	}
}
```


* **Maximum sub-array given an integer array.**

```
public class maxSubArray {
	public static int maxSubArray(int[] a) {
		int newSum = a[0];
		int max = a[0];
		
		for (int i = 1; i < a.length; i++) {
			newSum = Math.max(newSum + a[i], a[i]);
			max = Math.max(max, newSum);
		}
		
		return max;
	}
	
	public static int maxSubArrayDP(int[] a) {
		int max = a[0];
		int[] sum = new int[a.length];
		sum[0] = a[0];
		
		for (int i = 1; i < a.length; i++) {
			sum[i] = Math.max(a[i], sum[i - 1] + a[i]);
			max = Math.max(max, sum[i]);
		}
		
		return max;
	}
	
	public static void main(String[] args) {
		int[] array = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
		System.out.println(maxSubArrayDP(array));
		System.out.println(maxSubArray(array));
	}
}
```


* **Remove duplicates in an integer array.**

	Algorithm:  
	1. Loop through the array and count the number of duplicates.  
	2. Using the duplicate count, create a new integer array with the correct size (without duplicates).  
	3. Loop through the array again. If current index is same value as next index, continue. Else, add it to the new array. (Use different index for the two arrays)

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
}
```


* **Split input string with a given delimiter.**

```
public class SplitStringDelimiter {
	public static String[] split(String str, String delimiter) {
		String[] strArray;
		int occurrences = 0;
		int strIndex = 0;
		int delimiterIndex = 0;
		int strArrayIndex = 0;
		
		if (str == null) {
			throw new IllegalArgumentException("Input string cannot be null.");
		}
		
		if (str.startsWith(delimiter)) {
			str = str.substring(delimiter.length());
		}
		
		if (!str.endsWith(delimiter)) {
			str += delimiter;
		}
		
		while ((delimiterIndex = str.indexOf(delimiter, strIndex)) != -1) {
			occurrences++;
			strIndex = delimiterIndex + delimiter.length();
		}
		
		strArray = new String[occurrences];
		strIndex = 0;
		delimiterIndex = 0;
		
		while ((delimiterIndex = str.indexOf(delimiter, strIndex)) != -1) {
			strArray[strArrayIndex] = str.substring(strIndex, delimiterIndex);
			strIndex = delimiterIndex + delimiter.length();
			strArrayIndex++;
		}
		
		return strArray;
	}

	public static void main(String[] args) {
		String strTestString2 = "The /quic/k brown fo/x jumps ov/er /the lazy/ dog.";
		String[] arrString2 = split(strTestString2,"/");

		for (int i=0; i< arrString2.length; i++) {
			System.out.println("array element " + i + ": " + arrString2[i]);
		}
	}
}
```


* **Determine the second frequent number in an input array.**

* **Reverse a Linked List object.**

```
public class ReverseLinkedList {
	public static void reverseLinkedList(LinkedListNode head) {
		LinkedListNode previous = null;
		LinkedListNode current = head;
		
		while (current != null) {
			LinkedListNode next = current.next;
			current.next = previous;
			previous = current;
			current = next;
		}
		
		head = previous;
	}
}
```


* **Find all elements in a DOM with a specific attribute.**

* **Given a start word, an end word, and a list of valid words, implement an algorithm to return all words from start word to end word, where each step changes only one character at a time.  
	Example : Given "Cat", "Dog" and a list of valid words, return  
	cat -> bat -> bet -> bot -> bog -> dog**
	
* **Find whether a binary tree is a binary search tree.**

```
public class CheckBST {
	public static boolean isValidBST(TreeNode root) {
		return validate(root, Integer.MIN_VALUE, Integer.MAX_VALUE);
	}
	
	public static boolean validate(TreeNode root, int min, int max) {
		if (root == null)
			return true;
		
		if (root.data <= min || root.data >= max)
			return false;
		
		return validate(root.left, min, root.data) && validate(root.right, root.data, max);
	}
}
```


* **Print all combinations of balanced parentheses.**

```
public class CombinationParentheses {
	public static char[] parentheses;
	
	public static void printParentheses(int n) {
		if (n > 0) {
			parentheses = new char[n * 2];
			printParentheses(0, n, 0, 0);
		}
	}
	
	public static void printParentheses(int index, int n, int open, int close) {
		if (close == n) {
			System.out.println(String.valueOf(parentheses));
		} else {
			if (open > close) {
				parentheses[index] = '}';
				printParentheses(index + 1, n, open, close + 1);
			}
			
			if (open < n) {
				parentheses[index] = '{';
				printParentheses(index + 1, n, open + 1, close);
			}
		}
	}
	
	public static void main(String[] args) {
		printParentheses(6);
	}
}
```


* **Run length encoding.**

* **The most efficient algorithm to determine the closest deal to n customers if there are m deals.**

* **Suppose you have 4gb list of integers on disk. Find the kth largest element. (Use array)**

* **String, int and map were encrypted in some rules. Decrypt a string based on those rules and return a map. Should write helper functions and keep calling them as looping through the string.**

* **How to sample a number given a list of probabilities.**

* **How do you serialize and deserialize a list of strings?**

* **Difference between a String, StringBuilder, and StringBuffer.**

	|	| String | StringBuffer | StringBuilder |
	|:-:|:------:|:------------:|:-------------:|
	| Storage Area | Constant String Pool | Heap | Heap |
	| Modifiable | No (immutable) | Yes (mutable) | Yes (mutable) |
	| Thread Safe | Yes | Yes | No |
	| Performance | Fast | Very slow | Fast |


* **Code Dijkstra's algorithm.**

```
class Vertex implements Comparable<Vertex> {
	public final String name;
	public Edge[] adjacencies;
	public double minDistance = Double.POSITIVE_INFINITY;
	public Vertex previous;
	
	public Vertex(String name) {
		this.name = name;
	}
	
	public int compareTo(Vertex other) {
		return Double.compare(minDistance, other.minDistance);
	}
}

class Edge {
	public final Vertex target;
	public final double weight;
	
	public Edge(Vertex target, double weight) {
		this.target = target;
		this.weight = weight;
	}
}

public class Dijkstra {
	public static void computePaths(Vertex source) {
		source.minDistance = 0;
		PriorityQueue<Vertex> vertexQueue = new PriorityQueue<Vertex>();
		vertexQueue.add(source);
		
		while (!vertexQueue.isEmpty()) {
			Vertex u = vertexQueue.poll();
			
			for (Edge e : u.adjacencies) {
				Vertex v = e.target;
				double distance = u.minDistance + e.weight;
				
				if (distance < v.minDistance) {
					vertexQueue.remove(v);
					v.minDistance = distance;
					v.previous = u;
					vertexQueue.add(v);
				}
			}
		}
	}

	public static List<Vertex> getShortestPathTo(Vertex target) {
		List<Vertex> path = new ArrayList<Vertex>();
		
		for (Vertex vertex = target; vertex != null; vertex = vertex.previous) {
			path.add(vertex);
		}
		
		Collections.reverse(path);
		return path;
	}

	public static void main(String[] args) {
		Vertex v0 = new Vertex("A");
		Vertex v1 = new Vertex("B");
		Vertex v2 = new Vertex("C");
		Vertex v3 = new Vertex("D");
		Vertex v4 = new Vertex("E");

		v0.adjacencies = new Edge[]{ new Edge(v1, 5), new Edge(v2, 10), new Edge(v3, 8) };
		v1.adjacencies = new Edge[]{ new Edge(v0, 5), new Edge(v2, 3), new Edge(v4, 7) };
		v2.adjacencies = new Edge[]{ new Edge(v0, 10), new Edge(v1, 3) };
		v3.adjacencies = new Edge[]{ new Edge(v0, 8), new Edge(v4, 2) };
		v4.adjacencies = new Edge[]{ new Edge(v1, 7), new Edge(v3, 2) };
		
		Vertex[] vertices = { v0, v1, v2, v3, v4 };
		computePaths(v0);
		
		for (Vertex v : vertices) {
			System.out.println("Distance to " + v.name + ": " + v.minDistance);
			List<Vertex> path = getShortestPathTo(v);
			System.out.println("Path: " + path);
		}
	}
}
```

* **AVL Rotation.**

* **You need to create a queue, but you're not allowed to use stacks. How would you do it?**

```
public class QueueLinkedList<Item> {
	private Node head, tail;
	private int size;
	
	private class Node {
		Item item;
		Node next;
	}
	
	public QueueLinkedList() {
		head = null;
		tail = null;
		size = 0;
	}
	
	public boolean isEmpty() {
		return size == 0;
	}
	
	public int size() {
		return size;
	}
	
	public Item peek() {
		return head.item;
	}
	
	public void add(Item item) {
		Node oldTail = tail;
		tail = new Node();
		tail.item = item;
		tail.next = null;
		
		if (isEmpty()) {
			head = tail;
		} else {
			oldTail.next = tail;
		}
		
		size++;
	}
	
	public Item poll() {
		if (isEmpty()) {
			return null;
		}
		
		return delete();
	}
	
	public Item remove() {
		return delete();
	}
	
	private Item delete() {
		Item item = head.item;
		head = head.next;
		size--;
		
		if (isEmpty()) {
			tail = null;
		}
		
		return item;
	}
}
```


* **When designing an API between front-end/UI code and backend servers, what technologies would you choose and more importantly, why would you choose one over the other?**

* **Find the number of substrings which are palindrome.**

* **Given that integers are read from a data stream. Find median of elements read so far in efficient way.**

```
public class MedianStreamIntegers {
	public Queue<Integer> minHeap;
	public Queue<Integer> maxHeap;
	public int numberOfElements;
	
	public MedianStreamIntegers() {
		minHeap = new PriorityQueue<Integer>();
		maxHeap = new PriorityQueue<Integer>(10, new MaxHeapComparator());
		numberOfElements = 0;
	}
	
	public void insert(Integer num) {
		maxHeap.add(num);
		
		if (numberOfElements % 2 == 0) {
			if (minHeap.isEmpty()) {
				numberOfElements++;
				return;
			} else if (maxHeap.peek() > minHeap.peek()) {
				Integer maxHeapRoot = maxHeap.poll();
				Integer minHeapRoot = minHeap.poll();
				maxHeap.add(minHeapRoot);
				minHeap.add(maxHeapRoot);
			}
		} else {
			minHeap.add(maxHeap.poll());
		}
		
		numberOfElements++;
	}
	
	public Double getMedian() {
		if (numberOfElements % 2 != 0) {
			return new Double(maxHeap.peek());
		} else {
			return (maxHeap.peek() + minHeap.peek()) / 2.0;
		}
	}
	
	private class MaxHeapComparator implements Comparator<Integer> {
		public int compare(Integer o1, Integer o2) {
			return o2 - o1;
		}
	}
	
	public static void main(String[] args) {
		MedianStreamIntegers streamMedian = new MedianStreamIntegers();
		
		streamMedian.insert(1);
		System.out.println(streamMedian.getMedian());
		
		streamMedian.insert(5);
		streamMedian.insert(10);
		streamMedian.insert(12);
		streamMedian.insert(2);
		System.out.println(streamMedian.getMedian());
		
		streamMedian.insert(3);
		streamMedian.insert(8);
		streamMedian.insert(9);
		System.out.println(streamMedian.getMedian());
	}
}
```

* **Design an algorithm for a thermometer that shows the maximum and minimum temperature in the last 24 hours. The current temperature can be read in 5 seconds interval.**

* **Given R number of Red Cards, B number of Black Cards, K. Cards need to be placed in a circle. Start from a position and for every K moves remove that card and repeat the process until all the cards are eliminated. Question : Position the cards such that the red cards are completely eliminated before the black cards are selected for elimination.**

* **You are given a matrix. Starting from [0, 0], you have to move over the matrix in clockwise-spiral direction, i.e. we start from [0, 0], move up to [0, 4], and then move to [3, 4], then move to [3, 0], then move to [1, 0], then to [1, 3] and so on.  
Move this way and print all the elements.**

	```
	Input:
	1 2 3 4 5
	6 8 9 a b
	c d e f g
	h i j k l
	Output:
	1 2 3 4 5 b g l k j i h c 6 8 9 a f e d
	```
	
* **Design the File System for an OS.**

* **Search for an element in a rotated sorted array for e.g. sorted: {1, 2, 3, 4, 5, 6} rotated: {5, 6, 1, 2, 3, 4}.**

* **Find the top k items out of an array where items can have values [0 ... 100].**

* **Find the largest subarray with equal number of 0's and 1's.**

* **Given a BST, convert it into a new Data Structure that satisfies following conditions:**
	* **Every leaf node's left pointer points to tis parent and right pointer points to the next leaf.**
	* **Every non leaf node's left pointer points to its parent and right pointer is NULL.**
	* **Return the head and print the new Data Structure.**
	
	```
	Example:
	7
	/\
	5 9
	/\ \
	4 6 10
	Output:
	head -> 4 -> 5 -> 7
	|
	-> 6 -> 5 -> 7
	|
	-> 10 -> 9 -> 7
	```
	
* **Given an array, return true if it can be partitioned into two subarrays whose sum of elements are same, else return false.**

	```
	Example:
	Input: {5, 1, 5, 11}
	Output: true ({5, 1, 5} and {11})
	```
	
* **Find the most common "3 page path" on a website given a large data log.**

* **Find pairs of numbers that add up to a given number.**

* **input: "kitten%20pic.jpg"
	ouput: "kitten pic.jpg"  
	%20 -> ' '  
	%3A -> '?'  
	%3D -> ':'  
	Modify your input in place.  
	No String library functions**
	
* **Write in order traversal without using recursion.**

* **Add two integers which cannot be stored even in long long ing.**  
  
* **Given a BST and two values a and b, write a method which returns number of nodes in this tree such that a < node value < b.**  
  
* **Given a String, find the longest even palindrome (length of palindrome is even) from it.  
Example:  
Input: abcicbbcdefggfed  
Output: defggfed (length is 8)  
Available palindromes are:**  
	* **bcicb - has odd length**  
	* **cbbc - even length**  
	* **defggfed - longest palindrome with even length**  

* **You are given a graph and an algorithm that can find the shortest path between any two nodes. Now you have to find the second shortest path between same two nodes.**

* **In a grid, you are given a position, and every location has some value. Find the shortest length so that you can touch to any boundary of the grid.**

* **You have a binary tree on client machine, how will you send this info to server and how will you again maintain the ree over the server.**

* **You have a robot in a grid, it can move in forward direction and can change its facing towards north, south, east, and west and you are given a command sequence. So what will be the final position of the robot.  
Example:  
Grid(100 * 500)  
Robot position - (5, 3)  
Sequence - {N, S, M, M, E, W, E, S, M, S, M} North, East, West, South, Move Forward.**

* **Print a binary tree in vertical order using singly linked list. Complexity should be O(n).**

* **Print level order traversal of a binary tree in reverse way.**

	```
	Example:
		1
	   / \
	  2   3
	 / \ / \
	4  5 6  7
	Output:
	4 5 6 7 2 3 1
	```
	
* **Implement a circular queue of integers of user-specified size using a simple array. Povide routines to initialize(), enqueue(), and dequeue() the queue. Make it thread safe.**

* **Implement atoi function. Define your own function signature in the language of your choice.**











	























