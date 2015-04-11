<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>

## Dropbox Interview Questions

* [**Make a program that can print out the text form of numbers.**](#NumberWords)
* [**Create a square root function.**](#SquareRoot)
* [**Print the nodes in an n-ary tree level by level, one printed line per level.**](#NaryTree)
* [**Given a string such as "123" or "67", write a function to output the number represented by the string without using casting.**](#StringToInt)
* [**Convert phone numbers to words. Print all the possibilities**](#PhoneNumberWords)


* [](id:NumberWords)**Make a program that can print out the text form of numbers.**

```
public class NumberWords {
	private static final String[] bigs = {"", "thousand", "million", "billion", "trillion", "quadrillion", "quintillion"};
	
	private static final String[] tens = {"ten", "twenty", "thirty", "forty", "fifty", "sixty", "seventy", "eighty", "ninety"};
	
	private static final String[] teens = {"eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"};
	
	private static final String[] digits = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine"};
	
	public static String numToString(int number) {
		if (number == 0) {
			return "zero";
		}
		
		if (number < 0) {
			return "negative " + numToString(-1 * number);
		}
		
		int count = 0;
		String str = "";
		
		while (number > 0) {
			if (number % 1000 != 0) {
				str = numString100(number % 1000) + bigs[count] + " " + str;
			}
			
			number /= 1000;
			count++;
		}
		
		return str;
	}
	
	public static String numString100(int number) {
		String str = "";
		
		if (number >= 100) {
			str += digits[number / 100 - 1] + " hundred ";
			number %= 100;
		}
		
		if (number >= 11 && number <= 19) {
			return str + teens[number - 11] + " ";
		} else if (number == 10 || number >= 20) {
			str += tens[number / 10 - 1] + " ";
			number %= 10;
		}
		
		if (number >= 1 && number <= 9) {
			str += digits[number - 1] + " ";
		}
		
		return str;
	}
	
	public static void main(String[] args) {
		System.out.println(numToString(123456789));
	}
}
```

* [](id:SquareRoot)**Create a square root function.**

```
public class SquareRoot {
	public static void squareRoot(double num) {
		boolean isPositive = true;
		
		if (num == 0) {
			System.out.println(0);
		} else if (num < 0) {
			num = -num;
			isPositive = false;
		}
		
		double g1;
		double squareRoot = num / 2;
		
		do {
			g1 = squareRoot;
			squareRoot = (g1 + num / g1) /2;
		} while (g1 - squareRoot != 0);
		
		if (isPositive) {
			System.out.println("+" + squareRoot);
			System.out.println("-" + squareRoot);
		} else {
			System.out.println("+" + squareRoot + "i");
			System.out.println("-" + squareRoot + "i");
		}
	}
	
	public static void main(String[] args) {
		squareRoot(-36);
	}
}
```

* [](id:NaryTree)**Print the nodes in an n-ary tree level by level, one printed line per level.**

```
import CtCILibrary.*;

import java.util.Iterator;
import java.util.LinkedList;
import java.util.Queue;

public class NaryTree {
	public static void printTree(TreeNode root) {
		Queue<TreeNode> currentLevel = new LinkedList<TreeNode>();
		Queue<TreeNode> nextLevel = new LinkedList<TreeNode>();
		
		currentLevel.add(root);
		
		while (!currentLevel.isEmpty()) {
			Iterator<TreeNode> iter = currentLevel.iterator();
			
			while (iter.hasNext()) {
				TreeNode currentNode = iter.next();
				
				if (currentNode.left != null) {
					nextLevel.add(currentNode.left);
				}
				
				if (currentNode.right != null) {
					nextLevel.add(currentNode.right);
				}
				
				System.out.print(currentNode.data + " ");
			}
			
			System.out.println();
			
			currentLevel = nextLevel;
			nextLevel = new LinkedList<TreeNode>();
		}
	}
	
	public static void main(String[] args) {
		int[] nodes_flattened = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
		TreeNode root = AssortedMethods.createTreeFromArray(nodes_flattened);
		printTree(root);
	}
}
```

* [](id:StringToInt)**Given a string such as "123" or "67", write a function to output the number represented by the string without using casting.**

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

* [](id:PhoneNumberWords)**Convert phone numbers to words. Print all the possibilities**

```
public class PhoneNumberWords {
	static String[] allLeters = new String[] {
			"0",
			"1",
			"ABC",
			"DEF",
			"GHI",
			"JKL",
			"MNO",
			"PQRS",
			"TUV",
			"WXYZ"
	};
	
	public static void convert(String phoneNumber) {
		convertSubstring(phoneNumber, "");
	}
	
	private static void convertSubstring(String phoneNumber, String convertedLetters) {
		int digit = Integer.parseInt(phoneNumber.substring(0, 1));
		String letters = allLeters[digit];
		String remainingString = phoneNumber.substring(1);
		
		for (int i = 0; i < letters.length(); i++) {
			char letter = letters.charAt(i);
			String result = convertedLetters + letter;
			
			if (remainingString.length() == 0) {
				System.out.println(result);
			} else {
				convertSubstring(remainingString, result);
			}
		}
	}
	
	public static void main(String[] args) {
		convert("234");
	}
}
```




