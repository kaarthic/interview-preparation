JavaScript Interview Questions
==============================

## <a name='toc'>Table of Contents</a>

  1. [JavaScript Questions](#js)

####[[↑]](#toc) <a name='js'>JavaScript Questions:</a>

1. **What is JavaScript?**  
JavaScript is a client-side scripting language that can be inserted into HTML pages and is understood by web browsers.

2. **Enumerate the differences between Java and JavaScript?**  
Java is a complete programming language. In contrast, JavaScript is a coded program that can be introduced to HTML pages. These two languages are not at all inter-dependent and are designed for the different intent. Java is an object - oriented programming (OOPS) or structured programming language like C++ or C whereas JavaScript is a client-side scripting language and it is said to be unstructured programming.

3. **What are JavaScript types?**  
Following are the JavaScript types:
	* Number
	* String
	* Boolean
	* Function
	* Object
	* Null
	* Undefined

4. **What is the use of isNaN function?**  
isNan function returns true if the argument is not a number otherwise it is false.

5. **Between JavaScript and an ASP script, which is faster?**  
JavaScript is faster. JavaScript is a client-side language and thus it does not need the
assistance of the web server to execute. On the other hand, ASP is a server-side language and hence is always slower than JavaScript.

6. **What is negative infinity?**  
Negative Infinity is a number in JavaScript which can be derived by dividing negative number by zero.

7. **Is it possible to break JavaScript Code into several lines?**  
Breaking within a string statement can be done by the use of a backslash, `‘\’`, at the end of the first line

	Example:  
	
	```
document.write("This is \a program");
	```
	
	And if you change to a new line when not within a string statement, then javaScript ignores break in line.

	Example:  

	```
var x = 1, y = 2
z =
x + y;
	```
 
	The above code is perfectly fine, though not advisable as it hampers debugging.

8. **Which company developed JavaScript?**  
Netscape is the software company who developed JavaScript.

9. **What are undeclared and undefined variables?**  
Undeclared variables are those that do not exist in a program and are not declared. If the program tries to read the value of an undeclared variable, then a runtime error is encountered. Undefined variables are those that are declared in the program but have not been given any value. If the program tries to read the value of an undefined variable, an undefined value is returned.

10. **Write the code for adding new elements dynamically?**  

	```
<html>
<head> <title>t1</title>
script type="text/javascript"
	function addNode() {
		var newP = document.createElement("p");
		var textNode = document.createTextNode(" This is a new text node ");
		newP.appendChild(textNode);
		document.getElementById("firstP").appendChild(newP);
	}
/script
</head>
<body>
	<p id="firstP">firstP</>
</body>
</html>
	```

11. **What are global variables? How are these variable declared and what are the problems associated with using them?**  
Global variables are those that are available throughout the length of the code, that is, these have no scope. The var keyword is used to declare a local variable or object. If the var keyword is omitted, a global variable is declared.

	Example:  
	// Declare a global globalVariable = "Test";  
	The problems that are faced by using global variables are the clash of variable names of local and global scope. Also, it is difficult to debug and test the code that relies on global variables.
	
12. **What is a prompt box?**  
A prompt box is a box which allows the user to enter input by providing a text box. Label and box will be provided to enter the text or number.

13. **What is ‘this’ keyword in JavaScript?**  
‘This’ keyword is used to point at the current object in the code. For instance: If the code is presently at an object created by the help of the ‘new’ keyword, then ‘this’ keyword will point to the object being created.

14. **Explain the working of timers in JavaScript? Also elucidate the drawbacks of using
the timer, if any?**  
Timers are used to execute a piece of code at a set time or also to repeat the code in a given interval of time. This is done by using the functions `setTimeout`, `setInterval` and `clearInterval`.

	The `setTimeout(function, delay)` function is used to start a timer that calls a particular function after the mentioned delay.  
	The `setInterval(function, delay)` function is used to repeatedly execute the given function in the mentioned delay and only halts when cancelled.  
	The `clearInterval(id)` function instructs the timer to stop.

	Timers are operated within a single thread, and thus events might queue up, waiting to be executed.
	
15. **Which symbol is used for comments in Javascript?**  

	```
	// for Single line comments and
	/* Multi
	Line
	Comment
	*/
	```

16. **What is the difference between ViewState and SessionState?**  
`ViewState` is specific to a page in a session.  
`SessionState` is specific to user specific data that can be accessed across all pages in the web application.

17. **What is `===` operator?**  
`===` is called as strict equality operator which returns true when the two operands are having the same value without any type conversion.

18. **Explain how can you submit a form using JavaScript?**  
To submit a form using JavaScript use `document.form[0].submit();`

19. **Does JavaScript support automatic type conversion?**  
Yes JavaScript does support automatic type conversion, it is the common way of type
conversion used by JavaScript developers.

20. **How can the style/class of an element be changed?**  
It can be done in the following way:

	```
document.getElementById("myText").style.fontSize = "20";
	```
	
	or
	
	```
document.getElementById("myText").className = "anyclass";
	```

21. **Explain how to read and write a file using JavaScript?**  
There are two ways to read and write a file using JavaScript:
	* Using JavaScript extensions
	* Using a web page and Active X objects
	
22. **What are all the looping structures in JavaScript?**  
Following are looping structures in Javascript:
	* For
	* While
	* do-while loops
	
23. **What is called Variable typing in Javascript?**  
Variable typing is used to assign a number to a variable and the same variable can be assigned to a string.

	Example:  

	```
i = 10;
i = "string";
	```

	This is called variable typing.
	
24. **How can you convert the string of any base to integer in JavaScript?**  
The `parseInt()` function is used to convert numbers between different bases. `parseInt()` takes the string to be converted as its first parameter, and the second parameter is the base of the given string.

	In order to convert 4F (of base 16) to integer, the code used will be -  

	```
parseInt("4F", 16);
	```
	
25. **Explain the difference between `==` and `===`?**  
`==` checks only for equality in value whereas `===` is a stricter equality test and returns false if either the value or the type of the two variables are different.

26. **What would be the result of 3+2+"7"?**
Since 3 and 2 are integers, they will be added numerically. And since 7 is a string, its
concatenation will be done. So the result would be 57.

27. **Explain how to detect the operating system on the client machine?**  
In order to detect the operating system on the client machine, the navigator.appVersion string (property) should be used.

28. **What do mean by NULL in Javascript?**  
The NULL value is used to represent no value or no object. It implies no object or null string, no valid boolean value, no number and no array object.

29. **What is the function of delete operator?**  
The functionality of delete operator is used to delete all variables and objects in a program but it cannot delete variables declared with VAR keyword.

30. **What is an undefined value in JavaScript?**  
Undefined value means the:
	* Variable used in the code doesn’t exist
	* Variable is not assigned to any value
	* Property doesn’t exist
	
31. **What are all the types of Pop up boxes available in JavaScript?**  
	* Alert
	* Confirm
	* Prompt
	
32. **What is the use of `Void(0)`?**  
`Void(0)` is used to prevent the page from refreshing and parameter "zero" is passed while calling. `Void(0)` is used to call another method without refreshing the page.

33. **How can a page be forced to load another page in JavaScript?**  
The following code has to be inserted to achieve the desired effect:  

	```
script langauge="JavaScript" type="text/javascript"
	<!-- location.href="http://newhost/newpath/newfile.html"; //-->
/script
	```

34. **What is the data type of variables of in JavaScript?**  
All variables in the JavaScript are object data types.

35. **What is the difference between an alert box and a confirmation box?**  
An alert box displays only one button which is the OK button. But a Confirmation box displays two buttons namely OK and cancel.

36. **What are escape characters?**  
Escape characters (Backslash) is used when working with special characters like single quotes, double quotes, apostrophes and ampersands. Place backslash before the characters to make it display.

	Example:  

	```
document.write("I m a "good" boy);
document.write("I m a \"good\" boy");
	```
	
37. **What are JavaScript Cookies?**  
Cookies are the small test files stored in a computer and it gets created when the user visits the websites to store information that they need. Example could be User Name details and shopping cart information from the previous visits.

38. **Explain what is pop() method in JavaScript?**  
The `pop()` method is similar as the `shift()` method but the difference is that the Shift method works at the end of the array. Also the `pop()` method take the last element off of the given array and returns it. The array on which is called is then altered.

39. **Whether JavaScript has concept level scope?**  
No. JavaScript does not have concept level scope. The variable declared inside the function has scope inside the function.

40. **Mention what is the disadvantage of using innerHTML in JavaScript?**  
If you use innerHTML in JavaScript the disadvantage is:
	* Content is replaced everywhere
	* We cannot use like “appending to innerHTML”
	* Even if you use +=like “innerHTML = innerHTML + ‘html’” still the old content is replaced by html
	* The entire innerHTML content is re-parsed and build into elements, therefore its much slower
	* The innerHTML does not provide validation and therefore we can potentially insert valid and broken HTML in the document and break it
	
41. **What is break and continue statements?**  
Break statement exits from the current loop.  
Continue statement continues with next statement of the loop.

42. **What are the two basic groups of dataypes in JavaScript?**  
They are as:
	* Primitive
	* Reference types.
	
	Primitive types are number and Boolean data types. Reference types are more complex types like strings and dates.

43. **How generic objects can be created?**
Generic objects can be created as:

	```
var I = new object();
	```
	
44. **What is the use of type of operator?**  
`Typeof` is an operator which is used to return a string description of the type of a variable.

45. **Which keywords are used to handle exceptions?**  
Try… Catch—finally is used to handle exceptions in the JavaScript

	```
Try {
	Code
} Catch(exp) {
	Code to throw an exception
} Finally {
	Code runs either it finishes successfully or after catch
}
	```
	
46. **Which keyword is used to print the text in the screen?**  
`document.write(“Welcome”)` is used to print the text – Welcome in the screen.

47. **What is the use of blur function?**  
Blur function is used to remove the focus from the specified object.

48. **What is variable typing?**  
Variable typing is used to assign a number to a variable and then assign string to the same variable. Example is as follows:

	```
i= 8;
i=”john”;
	```

49. **How to find operating system in the client machine using JavaScript?**  
The ‘Navigator.appversion’ is used to find the name of the operating system in the client machine.

50. **What are the different types of errors in JavaScript?**  
There are three types of errors:
	* **Load time errors**: Errors which come up when loading a web page like improper syntax errors are known as Load time errors and it generates the errors dynamically.
	* **Run time errors**: Errors that come due to misuse of the command inside the HTML language.
	* **Logical Errors**: These are the errors that occur due to the bad logic performed on a function which is having different operation.
	
51. **What is the use of Push method in JavaScript?**  
The push method is used to add or append one or more elements to the end of an Array. Using this method, we can append multiple elements by passing multiple arguments

52. **What is unshift method in JavaScript?**  
Unshift method is like push method which works at the beginning of the array.  This method is used to prepend one or more elements to the beginning of the array.

53. **What is the difference between JavaScript and Jscript?**  
Both are almost similar. JavaScript is developed by Netscape and Jscript was developed by Microsoft .

54. **How are object properties assigned?**  
Properties are assigned to objects in the following way –

	```
obj["class"] = 12;
or
obj.class = 12;
	```

55. **What is the ‘Strict’ mode in JavaScript and how can it be enabled?**  
Strict Mode adds certain compulsions to JavaScript. Under the strict mode, JavaScript shows errors for a piece of codes, which did not show an error before, but might be problematic and potentially unsafe. Strict mode also solves some mistakes that hamper the JavaScript engines to work efficiently.

	Strict mode can be enabled by adding the string literal “use strict” above the file. This can be illustrated by the given example:

	```
function myfunction() {
	“use strict";
	var v = “This is a strict mode function";
}
	```

56. **What is the way to get the status of a CheckBox?**  
The status can be acquired as follows –

	```
alert(document.getElementById(‘checkbox1′).checked);
	```

	If the CheckBox will be checked, this alert will return TRUE.

57. **How can the OS of the client machine be detected?**  
The navigator.appVersion string can be used to detect the operating system on the client machine.

58. **Explain window.onload and onDocumentReady?**  
The onload function is not run until all the information on the page is loaded. This leads to a substantial delay before any code is executed.

	onDocumentReady loads the code just after the DOM is loaded. This allows early manipulation of the code.

59. **How will you explain closures in JavaScript? When are they used?**  
Closure is a locally declared variable related to a function which stays in memory when the function has returned.

	For example:

	```
function greet(message) {
	console.log(message);
}
function greeter(name, age) { 
	return name + " says howdy!! He is " + age + " years old";
}
// Generate the message
var message = greeter("James", 23);
// Pass it explicitly to greet
greet(message);
// This function can be better represented by using closures
function greeter(name, age) {
	var message = name + " says howdy!! He is " + age + " years old";
 	return function greet() {
 		console.log(message);
	};
}
// Generate the closure
var JamesGreeter = greeter("James", 23);
// Use the closure 
JamesGreeter();
	```

60. **How can a value be appended to an array?**  
A value can be appended to an array in the given manner –

	```
arr[arr.length] = value;
	```

61. **Explain the for-in loop?**  
The for-in loop is used to loop through the properties of an object. The syntax for the for-in loop is –

	```
for (variable name in object) {
	statement or block to execute
}
	```
	
	In each repetition, one property from the object is associated to the variable name, and the loop is continued till all the properties of the object are depleted.

62. **Describe the properties of an anonymous function in JavaScript?**  
A function that is declared without any named identifier is known as an anonymous function. In general, an anonymous function is inaccessible after its declaration.

	Anonymous function declaration –

	```
var anon = function() {
	alert('I am anonymous');
};
anon();
	```

63. **What is the difference between `.call()` and `.apply()`?**  
The function .call() and .apply() are very similar in their usage except a little difference. .call() is used when the number of the function’s arguments are known to the programmer, as they have to be mentioned as arguments in the call statement. On the other hand, .apply() is used when the number is not known. The function .apply() expects the argument to be an array.

	The basic difference between .call() and .apply() is in the way arguments are passed to the function. Their usage can be illustrated by the given example.

	```
var someObject = {
	myProperty : 'Foo',
	myMethod : function(prefix, postfix) {
		alert(prefix + this.myProperty + postfix);
	}
};
someObject.myMethod('<', '>'); // alerts '<Foo>'
var someOtherObject  = {
	myProperty : 'Bar'
};
someObject.myMethod.call(someOtherObject, '<', '>'); // alerts '<Bar>'
someObject.myMethod.apply(someOtherObject, ['<', '>']); // alerts '<Bar>'
	```

64. **Define event bubbling?**  
JavaScript allows DOM elements to be nested inside each other. In such a case, if the handler of the child is clicked, the handler of parent will also work as if it were clicked too.

65. **Is JavaScript case sensitive? Give an example?**  
Yes, JavaScript is case sensitive. For example, a function parseInt is not same as the function Parseint.

66. **What boolean operators can be used in JavaScript?**  
The ‘And’ Operator (&&), ‘Or’  Operator (||) and the ‘Not’ Operator (!) can be used in JavaScript.

	*Operators are without the parenthesis.

67. **How can a particular frame be targeted, from a hyperlink, in JavaScript?**  
This can be done by including the name of the required frame in the hyperlink using the ‘target’ attribute.

	```
<a href=”newpage.htm” target=”newframe”>New Page</a>
	```

68. **What is the role of break and continue statements?**  
	Break statement is used to come out of the current loop while the continue statement continues the current loop with a new recurrence.

69. **Write the point of difference between web-garden and a web-farm?**  
Both web-garden and web-farm are web hosting systems. The only difference is that web-garden is a setup that includes many processors in a single server while web-farm is a larger setup that uses more than one server.

70. **How are object properties assigned?**  
Assigning properties to objects is done in the same way as a value is assigned to a variable. For example, a form object’s action value is assigned as ‘submit’ in the following manner – Document.form.action=”submit”

71. **What is the method for reading and writing a file in JavaScript?**  
This can be done by Using JavaScript extensions (runs from JavaScript Editor), example for opening of a file –

	```
fh = fopen(getScriptPath(), 0);
	```

72. **How are DOM utilized in JavaScript?**  
DOM stands for Document Object Model and is responsible for how various objects in a document interact with each other. DOM is required for developing web pages, which includes objects like paragraph, links, etc. These objects can be operated to include actions like add or delete. DOM is also required to add extra capabilities to a web page. On top of that, the use of API gives an advantage over other existing models.

73. **How are event handlers utilized in JavaScript?**  
Events are the actions that result from activities, such as clicking a link or filling a form, by the user. An event handler is required to manage proper execution of all these events. Event handlers are an extra attribute of the object. This attribute includes event’s name and the action taken if the event takes place.

74. **Explain the role of deferred scripts in JavaScript?**  
By default, the parsing of the HTML code, during page loading, is paused until the script has not stopped executing. It means, if the server is slow or the script is particularly heavy, then the webpage is displayed with a delay. While using Deferred, scripts delays execution of the script till the time HTML parser is running. This reduces the loading time of web pages and they get displayed faster.

75. **What are the various functional components in JavaScript?**  
The different functional components in JavaScript are-

	First-class functions: Functions in JavaScript are utilized as first class objects. This usually means that these functions can be passed as arguments to other functions, returned as values from other functions, assigned to variables or can also be stored in data structures.

	Nested functions: The functions, which are defined inside other functions, are called Nested functions. They are called ‘everytime’ the main function is invoked.

76. **Write about the errors shown in JavaScript?**  
JavaScript gives a message if it encounters an error. The recognized errors are –

	* Load-time errors: The errors shown at the time of the page loading are counted under Load-time errors. These errors are encountered by the use of improper syntax, and thus are detected while the page is getting loaded.
	* Run-time errors: This is the error that comes up while the program is running. It is caused by illegal operations, for example, division of a number by zero, or trying to access a non-existent area of the memory.
	* Logic errors: It is caused by the use of syntactically correct code, which does not fulfill the required task. For example, an infinite loop.
	
77. **What are Screen objects?**  
Screen objects are used to read the information from the client’s screen. The properties of screen objects are –
	* AvalHeight: Gives the height of client’s screen
	* AvailWidth: Gives the width of client’s screen.
	* ColorDepth: Gives the bit depth of images on the client’s screen
	* Height: Gives the total height of the client’s screen, including the taskbar
	* Width: Gives the total width of the client’s screen, including the taskbar

78. **Explain the unshift() method?**  
This method is functional at the starting of the array, unlike the push(). It adds the desired number of elements to the top of an array. For example –

	```
var name = [ "john" ]; 
name.unshift( "charlie" );
name.unshift( "joseph", "Jane" );
console.log(name);
	```

	The output is shown below:

	```
[" Jane ", " joseph ", " charlie ", " john "]
	```
	
79. **Define unescape() and escape() functions?**  
The escape () function is responsible for coding a string so as to make the transfer of the information from one computer to the other, across a network.

	For Example:

	```
script
	document.write(escape(“Hello? How are you!”));
/script
	```

	Output: Hello? How are you!

	The unescape() function is very important as it decodes the coded string. It works in the following way. For example:

	```
script
	document.write(unescape(“Hello%3F%20How%20are%20you%21”));
/script
	```

	Output: Hello? How are you!

80. **What are the decodeURI() and encodeURI()?**  
EncodeURl() is used to convert URL into their hex coding. And DecodeURI() is used to convert the encoded URL back to normal.

	```
script
	var uri="my test.asp?name=ståle&car=saab";
	document.write(encodeURI(uri)+ "<br>");
	document.write(decodeURI(uri));
/script
	```

	Output –  
	my%20test.asp?name=st%C3%A5le&car=saab

	my test.asp?name=ståle&car=saab

81. **Why it is not advised to use innerHTML in JavaScript?**  
innerHTML content is refreshed every time and thus is slower. There is no scope for validation in innerHTML and, therefore, it is easier to insert rouge code in the document and, thus, make the web page unstable.

82. **What does the following statement declares?**  

	```
var myArray = [[[]]];
	``` 
	It declares a three dimensional array.

83. **How are JavaScript and ECMA Script related?**  
ECMAScript is nothing but another name for JavaScript. Precisely, ECMAScript is the formal name of JavaScript, when XML elements have to be accessed.

84. **What is namespacing in JavaScript and how is it used?**  
Namespacing is used for grouping the desired functions, variables etc. under a unique name. It is a name that has been attached to the desired functions, objects and properties. This improves modularity in the coding and enables code reuse.

85. **How can JavaScript codes be hidden from old browsers that don’t support JavaScript?** 
For hiding JavaScript codes from old browsers:

	Add “<!–” without the quotes in the code just after the <script> tag.

	Add “//–>” without the quotes in the code just before the <script> tag.

	Old browsers will now treat this JavaScript code as a long HTML comment. While, a browser that supports JavaScript, will take the “<!–” and “//–>” as one-line comments.

 
