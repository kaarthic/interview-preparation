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
* [**Implement an online class registration system**](#ClassRegistration)


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

* [](id:ClassRegistration)**Implement an online Class Registration System**

Your goal is to build an online class registration system for a local school.  
Schools have classes and students. A class has an ID (int), a maximum capacity (int), and a time (int).  
Students have their own IDs, as well as a maximum number of classes that they can take along with an interval time in which they can take classes.  
Although two students may not share the same ID, a student and a class may share the same ID. Time is given as integers; they map to periods in a school schedule (so a time 1 comes before 2, which comes before 3, etc.)

In terms of implementing these operations, you will be given a list of commands to process in order. You will return a list of the same size with the return values of each of the commands. Each command is guaranteed to follow one of the formats listed below.

**In designing this online class registration system, we would like to implement the following operations:**

**Add a class:**  
You will be given a class ID, a capacity, and a time period ID. If there is already a class with the given ID, report that a class with that ID already exists. Otherwise, add a class and report that the class was successfully added.

**Remove a class:**  
You will be given a class ID. If there is a class with that ID, unenroll all enrolled students from that class, remove the class, and state that the removal was successful. If there is no class with that ID, report that the given class does not exist.

**Print info on class:**  
You will be given a class ID. If there is no class with that ID, report that the class does not exist. Otherwise, return a sorted list of student IDs corresponding to students enrolled in the class.

**Add a student:**  
You will be given a student ID, a capacity, and the start and end times in which he/she can take classes. The start and end times are inclusive. If there is already a student with the given ID, report an error. Otherwise, add a student and report that the student was successfully added.

**Remove a student:**  
You will be given an ID. If there is a student with that ID, unenroll that student from all of his/her enrolled classes, remove the student, and state that the removal was successful. If there is no class with that ID, report an error.

**Print info on student:**  
You will be given an ID. If there is no student with that ID, report that the student does not exist. Otherwise, return a sorted list of class IDs corresponding to the classes that the student is enrolled in.

**Enroll student in class:**  
You will be given a student ID and a class ID. Attempt to enroll the student in the class. Report an error if enrollment was not successful. Otherwise, return the number of open spots left in the class. The student can only be enrolled in the class if the following conditions are met:  

* The student ID corresponds to a student.
* The class ID corresponds to a class.
* The student is not already enrolled in the class.
* The student has capacity to take the given class.
* The class has capacity for the student.
* The time of the class is inside the interval given for the student.
* The student is not already taking a class at the given time.

**Unenroll student in class:**  
You will be given a student ID and a class ID. Attempt to unenroll the student in the class - this can only happen if there is a student corresponding to the student ID and a class corresponding to the class ID and the student is already enrolled in the class. Report any error if the student could not be enrolled in the class. Otherwise, return the number of open spots left in the class.

**Input and output messaging are given in comments in each stub below.**

**Sample cases:**

Keep in mind for all of these that the quotation marks are used to denote strings - neither the input nor the expected output will have quotation marks.

Input:

```
commands = [
"ADDCLASS 1 1 1",
"ADDCLASS 1 2 2",
"INFOCLASS 1",
"INFOCLASS 2",
"REMOVECLASS 1",
"REMOVECLASS 2"
]
```

Expected Output:

```
[
"Successfully added class 1",
"Error adding class 1",
"Class 1 is empty",
"Class 2 does not exist",
"Successfully removed class 1",
"Error removing class 2"
]
```

Input:

```
commands = [
"ADDSTUDENT 1 1 1 1",
"ADDCLASS 1 2 2",
"INFOSTUDENT 1",
"INFOSTUDENT 2",
"REMOVESTUDENT 1",
"REMOVESTUDENT 1"
]
```

Output:

```
[
"Successfully added student 1",
"Successfully added class 1",
"Student 1 is not taking any classes",
"Student 2 does not exist",
"Successfully removed student 1",
"Error removing student 1"
]
```

Input:

```
commands = [
"ADDSTUDENT 1 4 1 3",
"ADDCLASS 1 1 1",
"ADDCLASS 2 1 2",
"ADDCLASS 3 1 3",
"ADDCLASS 4 1 4",
"ENROLLSTUDENT 1 1",
"INFOSTUDENT 1",
"ENROLLSTUDENT 1 2",
"INFOSTUDENT 1",
"ENROLLSTUDENT 1 3",
"INFOSTUDENT 1",
"ENROLLSTUDENT 1 4",
"INFOSTUDENT 1",
"UNENROLLSTUDENT 1 1",
"INFOSTUDENT 1",
"UNENROLLSTUDENT 1 2",
"INFOSTUDENT 1",
"UNENROLLSTUDENT 1 3",
"INFOSTUDENT 1",
"UNENROLLSTUDENT 1 4",
"INFOSTUDENT 1"
]
```

Expected Output:

```
[
"Successfully added student 1",
"Successfully added class 1",
"Successfully added class 2",
"Successfully added class 3",
"Successfully added class 4",
"Number of free spots left in class 1: 0",
"Student 1 is taking the following classes: 1",
"Number of free spots left in class 2: 0",
"Student 1 is taking the following classes: 1,2",
"Number of free spots left in class 3: 0",
"Student 1 is taking the following classes: 1,2,3",
"Enrollment of student 1 in class 4 failed",
"Student 1 is taking the following classes: 1,2,3",
"Number of free spots left in class 1: 1",
"Student 1 is taking the following classes: 2,3",
"Number of free spots left in class 2: 1",
"Student 1 is taking the following classes: 3",
"Number of free spots left in class 3: 1",
"Student 1 is not taking any classes",
"Unenrollment of student 1 in class 4 failed",
"Student 1 is not taking any classes"
]
```

Input:

```
commands = [
"ADDSTUDENT 1 1 1 1",
"ADDCLASS 1 1 1",
"ENROLLSTUDENT 1 1",
"INFOSTUDENT 1",
"REMOVECLASS 1"
"INFOSTUDENT 1",
"ADDCLASS 1 1 1",
"ENROLLSTUDENT 1 1",
"INFOCLASS 1",
"REMOVESTUDENT 1",
"INFOCLASS 1"
]
```

Expected Output:

```
[
"Successfully added student 1",
"Successfully added class 1",
"Number of free spots left in class 1: 0",
"Student 1 is taking the following classes: 1",
"Successfully removed class 1",
"Student 1 is not taking any classes",
"Successfully added class 1",
"Number of free spots left in class 1: 0",
"Class 1 has the following students: 1",
"Successfully removed student 1",
"Class 1 is empty"
]
```


**My Solution:**

```
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {

}
```


