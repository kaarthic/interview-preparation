Front-End Developer Interview Questions
=======================================

## <a name='toc'>Table of Contents</a>

  1. [General Questions](#general)
  1. [HTML Questions](#html)
  1. [CSS Questions](#css)
  1. [JavaScript Questions](#javascript)


####[[↑]](#toc) <a name='general'>General Questions:</a>

1. **What did you learn yesterday/this week?**

1. **What excites or interests you about coding?**

1. **What is a recent technical challenge you experienced and how did you solve it?**

1. **What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?**

1. **Talk about your preferred development environment.**

1. **Which version control systems are you familiar with?**  
Git, Rational ClearCase

1. **Can you describe your workflow when you create a web page?**

1. **If you have 5 different stylesheets, how would you best integrate them into a site?**

1. **Can you describe the difference between progressive enhancement and graceful degradation?**

1. **How would you optimize a website's assets/resources?**

1. **How many resource will a browser download from a given domain at a time? What are the exceptions?**

1. **Name 3 ways to decrease page load (perceived or actual load time).**

1. **If you jumped on a project and they used tabs and you used spaces, what would you do?**

1. **Describe how you would create a simple slideshow page.**

1. **What tools do you use to test your code's performance?**

1. **If you could master one technology this year, what would it be?**

1. **Explain the importance of standards and standards bodies.**

1. **What is Flash of Unstyled Content? How do you avoid FOUC?**

1. **Explain what ARIA and screen readers are, and how to make a website accessible.**

1. **Explain some of the pros and cons for CSS animations versus JavaScript animations.**
	* Lack of independent scale/rotation/position control.
	* Performance.
	* Runtime controls and events.
	* Workflow.
		* Relative values.
		* Nesting.
		* Progress reporting.
		* Targeted kills.
		* Concise code.
	* Limited effects.
	* Compatibility.


####[[↑]](#toc) <a name='html'>HTML Questions:</a>

1. **What does doctype do?**  
The doctype is an instruction to the web browser about what version of the markup language the page is written in.

1. **What's the difference between standards mode and quirks mode?**
     
1. **What's the difference between HTML and XHTML?**

	| Comparison | HTML | XHTML |
	|:----------:|:----:|:-----:|
	| Start Tag | Start tags are not required for every element. | All elements must have a start tag. |
	| End Tags | End tags are not required for every element. | Non-void elements with a start tag must have an end tag (p and li, for example). |
	| Self-closed | Only void elements such as br, img, and link may be "self-closed" with />. | Any element may be "self-closed" using />. |
	| Case Sensitivity | Tags and attributes are case-insensitive. | Tags and attributes are case-sensitive, typically lowercase. |
	| Attributes | Attributes do not need to be quoted. | Attributes value must be enclosed in quotes. |
	| Empty Attributes | Some attributes may be empty (such as checked and disabled). | Empty attributes are forbidden (checked must instead be checked="checked" or checked="true"). |
	| Special Character Escape | Special characters, or entities, do not have to escaped. | Special characters must be escaped using character entities. |

1. **Are there any problems with serving pages as application/xhtml+xml?**
     
1. **How do you serve a page with content in multiple languages?**
	* Language codes
		* Set the primary language.
	* Multiple languages
		* Use `lang` attribute to change languages within a page.
		* Provide links to the other language versions of your site.
	* Google and language recognition
	* Language direction
		* Specify the direction of the language using `dir` attribute for pages written using right-to-left direction.
	* Character encoding
		* A key to decipher an encrypted collection of letters and symbols used in a writing system. It also helps computers understand your information.
	* Font sizes
		* Use the CSS `lang` pseudo class to set different font sizes and font families depending on the value of the `lang` attribute.
		* Use classes on the body element for each language required.
	* Length of words

1. **What kind of things must you be wary of when designing or developing for multilingual sites?**
	* Properly sorting strings based on Locale.
	* Formatting data based on Locale.
	* Always showing time in the user's time zone.
	* Showing distance measurements for the user's locale (ex: Miles vs Kilometers).
	* Laying out the website right-to-left for languages like Arabic.
	* Think about how to lay out the web pages when the length of the text may vary wildly.

1. **What are data- attributes good for?**  
data-* attributes allow us to store extra information on standard, semantic HTML elements without other hacks such as classList, non-standard attributes, extra properties on DOM, or setUserData.

1. **Consider HTML5 as an open web platform. What are building blocks of HTML5?**
     
1. **Describe the difference between a cookie, sessionStorage, and localStorage.**
     
     | Cookie | sessionStorage | localStorage |
     |:------:|:--------------:|:------------:|
     | Stores name/value pairs per domain. | Non-persistent and scoped only to the current window. | Persistent and scoped to the domain. |
     | Can only store strings. | Can store JavaScript primitives but not Objects or Arrays. | Can store JavaScript primitives but not Object or Arrays. |

1. **Describe the difference between `<script>`, `<script async>` and `<script defer>`.**

	| `<script>` | `<script async>` | `<script defer>` |
	|:----------:|:----------------:|:----------------:|
	| Parsing of the HTML code pauses while the script is executing. | HTML parsing may continue and the script will be executed as soon as it's ready. | Delaying script execution until the HTML parser has finished. |
	| If the script is small and is relied upon by an async script then use an inline script with no attributes placed above the async scripts. | If the script is modular and does not rely on any scripts then use async. | If the script relies upon or is relied upon another script then use defer. |

1. **Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?**  
	* Pages appear to be loading faster because putting stylesheets in the HEAD allows the page to render progressively.
	* JS at bottom because they block parallel downloads.

     Exception:
	* If the script uses document.write to insert part of the page's content, it can't be moved lower in the page. There might also be scoping issues.

1. **What is progressive rendering?**  
Display whatever content it has as soon as possible.


####[[↑]](#toc) <a name='css'>CSS Questions:</a>

1. **What is the difference between classes and ID's in CSS?**

	| ID | Classes |
	|:--:|:-------:|
	| Each element can have only one ID. | Can use the same class on multiple elements. |
	| Each page can have only one element with that ID. | Can use multiple classes on the same element. |

1. **What is the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?**
	* Normalize.css preserves useful defaults rather than "unstyling" everything.
		* Example : elements like sup or sub "just work" after including normalize.css (and are actually made more robust) whereas they are visually indistinguishable from normal text after including reset.css.
	* Normalize.css corrects some common bugs that are out of scope for reset.css.
		* It has wider scope than reset.css, and also provides bug fixes for common problems like: display settings for HTML5 elements, the lack of font inheritance by form elements, correcting font-size rendering pre, SVG overflow in IE9, and the button styling bug in iOS.
	* Normalize.css doesn't clutter your dev tools.
		* A common irritation when using reset.css is the large inheritance chain that is displayed in browser CSS debugging tools. This is not such an issue with normalize.css because of the targeted stylings.
	* Normalize.css is more modular.
		* The project is broken down into relatively independent sections, making it easy for you to potentially remove sections (like the form normalizations) if you know they will never be needed by your website.
	* Normalize.css has better documentation.
		* The normalize.css code is documented inline as well as more comprehensively in the GitHub Wiki. This means you can find out each line of code is doing, why it was included, what the differences are between browsers, and more easily run your own tests.

1. **Describe Floats and how they work.**  
Floats are used to push an element to the left or right, allowing other elements to wrap around it.

1. **Describe z-index and how stacking context is formed.**  
Group elements with a common parent that move forward or backward together in the stacking order make up what is known as a stacking context.
	* When an element is the root element of a document(the <html> element.
	* When an element has a position value other than static and a z-index value other than auto.
	* When an element has an opacity value less than 1.

1. **What are the various clearing techniques and which is appropriate for what context?**
	* The empty div method.
		* It has no browser default styling.
	* The overflow method.
		* Setting the overflow CSS property on a parent element.
	* The easy clearing method.
		* Uses a clever CSS pseudo selector (:after).

1. **Explain CSS sprites, and how would you implement them on a page or a site.**

1. **What are your favorite image replacement techniques and which do you use when?**

Technique
HTML
CSS
1. Fahrner Image Replacement (FIR)
Use a span to wrap the text inside the header and use the sand to hide the text.
It works, but using display:none will hide the  text from screen readers (and presumably search bots, not good).

<h1 id=“technique-one”>
  <span>CSS-Tricks</span>
</h1>
h1#technique-one {
  width: 250px;
  height: 25px;
  background-image: url(logo.gif);
}

h1#technique-one {
  display: none;
}
2. Radu Darvas
Creates a giant box that goes way off the screen to the left. The text, being left-justified, cannot be seen. The image is placed in the top left of this box.
It works, but it has the common problem of failing with CSS ON/Images OFF. Requires giant box, less efficient than others.

<h1 id=“technique-two”>
  CSS-Tricks
</h1>
h1.technique-two {
  width: 2350px; height: 75px;
 background: url(“images/header-image.jpg”) top right;
  margin: 0 0 0 -2000px;
}
3. Phark Method
Replace block with background image, kick text off page with indent.
Effective. A variation of this technique to use negative letter spacing instead, which purpose is to resolve problems with triggering huge unwanted scrollbars in some browsers.

<h1 id=“technique-three”>
  CSS-Tricks
</h1>
h1.technique-three {
  width: 350px;
  height: 75px;
  background: url(“images/header-image.jpg”);
  text-indent: -9999px;
}
4. Extension of Phark Method
An extension of this technique would be to include regular web text inside the anchor link as well. Both the text and image would get bumped off the page with the text-indent and it would alleviate the SEO concerns, but then you’d get “double text” with both images OFF and CSS OFF.

<h1 class=“technique-four”>
  <a href=“#”>
    <img src=“images/header-image.jpg” alt=“CSS-Tricks” />
  </a>
</h1>
h1.technique-four {
  width: 350px; height: 75px;
  background: url(“images/header-image.jpg”);
  text-indent: -9999px;
}
5. Radu Darvas
Including a single-pixel transparent GIF image to the markup, you can restore ALT text with images turned off.
Very effective, but adding the shim GIF is quite the blow to semantics.
<h1 class=“technique-five”>
  <img src=“images/blank.gif” alt=“CSS-Tricks” />
  <span>CSS-Tricks</span>
</h1>
h1.technique-five {
  width: 350px; height: 75px;
  background: url(“images/header-image.jpg”);
}

h1.technique-five span {
  display: none;
}
6. Seamus Leahy & Stuart Langridge
Creates a box which will render with a height generated solely by top padding. By setting overflow to hidden, text will automatically be hidden but the box will be properly sized for a background image.
Accessibility-friendly and fairly effective but requires a box model hack for older version of IE.
<h1 class=“technique-six”>
  CSS-Tricks
</h1>
h1.technique-six {
  width: 350px;
  padding: 75px 0 0 0;
  height: 0;
  background: url(“images/header-image.jpg”) no-repeat;
  overflow: hidden;
}
7. Leon Dwyer
Able to hide the text by putting it inside a box 0px wide and 0px tall with hidden overflow. Because it doesn’t use the display attribute to hide the text, it’s safe for screen readers.
<h1 class=“technique-seven”>
  <span>CSS-Tricks</span>
</h1>
h1.technique-seven {
  width: 350px; height: 75px;
  background: url(“images/header-image.jpg”) no-repeat;
}

h1.technique-seven span {
  display: block;
  width: 0;
  height: 0;
  overflow: hidden;
}
8. Levin Alexander
The background image just sits on top of the text.
<h1 class=“technique-eight”>
  <span></span>CSS-Tricks
</h1>
h1.technique-eight {
  width: 350px; height: 75px;
  position: relative;
}

h1.technique-eight span {
  background: url(“images/header-image.jpg”);
  position: absolute;
  width: 100%;
  height: 100%;
}
9. Russ Weakley
Setting the text to an ultra-tiny 1px size and matching it’s color to the background color of the image, you don’t event have to hide it.
<h1 class=“technique-nine”>
  CSS-Tricks
</h1>
h1.technique-nine {
  width: 350px; height: 75px;
  background: url(“images/header-image.jpg”) no-repeat;
  font-size: 1px;
  color: white;
}

1. **How would you approach fixing browser-specific styling issues?**

1. **How do you serve your pages for feature-constrained browsers? What techniques/processes do you use?**

1. **What are the different ways to visually hide content (and make it available only for screen readers)?**

1. **Have you ever used a grid system, and if so, what do you prefer?**

1. **Have you used or implemented media queries or mobile specific layouts/CSS?**

1. **Any familiarity with styling SVG?**

1. **How do you optimize your webpages for print?**

1. **What are some of the "gotchas" for writing efficient CSS?**

1. **What are the advantages/disadvantages of using CSS preprocessors? Describe what you like and dislike about the CSS preprocessors you have used.**

1. **How would you implement a web design comp that uses non-standard fonts?**

1. **Explain how a browser determines what elements match a CSS selector.**

1. **Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models?**

1. **What does * { box-sizing: border-box; } do? What are its advantages?**

1. **List as many values for the display property that you can remember.**

	| Property | Description |
	|:--------:|:-----------:|
	| inline | Default value. Displays an element as an inline element (like <span>). |
	| block | Displays an element as a block element (like <p>). |
	| flex | Displays an element as an block-level flex container. |
	| inline-block | Displays an element as an inline-level block container. The inside of this block is formatted as block-level box, and the element itself is formatted as an inline-level box. |
	| inline-flex | Displays an element as an inline-level flex container. |
	| inline-table | The element is displayed as an inline-level table. |
	| list-item | Let the element behave like a <li> element. |
	| run-in | Displays an element as either block or inline, depending on context. |
	| none | The element will not be displayed at all (has no effect on layout). |
	| initial | Sets this property to its default value. |
	| inherit | Inherits this property from its parent element. |

1. **What's the difference between inline and inline-block?**

	| Inline | Inline Block | Block |
	|:------:|:------------:|:-----:|
	| The default value for elements. An inline element will accept margin and padding, but the element still sits inline. Margin and padding will only push other elements horizontally away, not vertically. | Very similar to inline in that it will set inline with the natural flow of text (on the “baseline”). The difference is that you are able to set a width and height which will be respected. | Block level elements do not sit inline but break past them. By default (without setting width) they take up as much horizontal space as they can |

1. **What's the difference between a relative, fixed, absolute and statically positioned element?**

1. **The 'C' in CSS stands for Cascading. How is priority determined in assigning styles (a few examples)? How can you use this system to your advantage?**

1. **What existing CSS frameworks have you used locally, or in production? How would you change/improve them?**

1. **Have you played around with the new CSS Flexbox or Grid specs?**

1. **How is responsive design different from adaptive design?**
	
	| Responsive Design | Adaptive Design |
	|:-----------------:|:---------------:|
	| Works on the principle of flexibility. | Modern definition of progressive enhancement. |
	| Single fluid design based upon media queries, flexible grids, and responsive images can be used to create a user experience that flexes and changes based on a multitude of factors. | Detects the device and other features, and then provides the appropriate feature and layout based on a predefined set of viewport sizes and other characteristics. |
	| Each user experiences a consistent design. | Lack of consistency across platforms and devices. |
	| Slower load time. | Faster load time. |
	| Harder to make. | Easier to make. |
	| More flexible. | Less flexible. |

1. **Have you ever worked with retina graphics? If so, when and what techniques did you use?**

1. **Is there any reason you'd want to use translate() instead of absolute positioning, or vice-versa? And why?**


####[[↑]](#toc) <a name='javascript'>JavaScript Questions:</a>

1. **What data types are supported in JavaScript?**
	* Boolean
		* Booleans are true and false.
	* Null
		* Null is a variable that is defined to have a null value.
	* Undefined
		* Something is undefined when it hasn't been defined yet.
	* Number
		* The number data type covers integers and floats. That is, the number type can handle normal numbers but also negative numbers and decimal places.
	* String
		* Grouping of characters.
	* Symbol
		* Symbols allow for private(ish) properties on objects.
	* Object

1. **Explain event delegation.**  
Event delegation allows us to avoid adding event listeners to specific nodes; instead, the event listener is added to one parent. The event listener analyzes bubbled events to find a match on child elements.

1. **Explain how this works in JavaScript.**  

	| this | Example |
	|:----:|:-------:|
	| this refers to the window. By default, this refers to the global object. | call this in the console directly and get window. |
	| this refers to the object it's being called from. | function currentYear() {
  return 2014;
}
var person = { birthYear: 1977,
               getAge: function() {
                 return currentYear() - this.birthYear;
               }
             };
person.getAge(); // returns 37 |
	| this refers to the element the event is bound to. | $('a').on('click', function(event) {
  console.log(event.target === this); // logs true
}); |


this refers to the context that was explicitly set. When a function is called using call or apply, this refers to the first argument passed to call or apply. If the first argument is null or not an object, this refers to the global object.
function greeter() {
  return 'Hello ' + this.name + '!';
}

var passableContext = { name: 'world' };
greeter.call(passableContext); // returns 'Hello world!'

1. **Explain how prototypal inheritance works.**  
In JavaScript, the inheritance is prototype-based. That means that there are no classes. Instead, an object inherits from another object. A prototype is an internal object from which other objects inherit properties. Its main purpose is to allow multiple instances of an object to share a common property. Thus, object properties which are defined using the prototype object are inherited by all instances which reference it.

1. **How do you go about testing your JavaScript.**

1. **What do you think of AMD vs CommonJS?**

	| AMD (Asynchronous Module Definition) | CommonJS |
	|:------------------------------------:|:--------:|
	| AMD is a browser-first approach. | CJSM is a server-first approach. |
	| Prefers async. | Assumes sync. |
	| Non-module resources (no File I/O). | Clean slate, no global baggage. |
	| Simplifies backward-compatibility. | Forward looking. |

	Approach:
	* Write packages that could execute in a server environment in CJSM format.
	* Write packages that could benefit from AMD's browser-friendly features in AMD format.
	* Write AMD modules in the AMD hybrid format unless they use plugins.

1. **Explain why the following doesn't work as an IIFE: function foo(){ }();? What needs to be changed to properly make it and IIFE?**  
IIFE - Immediately Invoked Function Expressions
	* IIFE is an anonymous function that is created and then immediately invoked. It’s not called from anywhere else (anonymous), but runs just after being created.

Usage of IIFE
Example
Used to guard against unintended effects of hoisting.

1. helperFunction(v) gets called with the current value of v, which is 1.
2. helperFunction gets executed, with the param x set to 1.
3. The anonymous function returned by helperFunction gets created, still with x set to 1.
5. getValue is set to the result of helperFunction.
var v = 1;
var getValue = (function(x) {
  return function() { return x; };
}(v));
v = 2;

getValue(); // returns 1

Helper :

var v = 1;
function helperFunction(x) {
  return function() {
    return x;
  };
}
var getValue = helperFunction(v); // returns an anonymous function
v = 2;
getValue(); // invokes that function
Used to enforce private variables and methods.

1. Call to counter.get() looks at the get function defined in helperFunction.
2. The get function look for it’s local scope, which is helperFunction.
3. In helperFunction is a definition of i.
4. So get returns 0.

var counter = (function() {
  var i = 0;
  return {
    get: function() {
      return i;
    },
    set: function(val) {
      i = val;
    }
  };
}());

counter.get(); // returns 0;
counter.set(3);
counter.get(); // returns 3;
counter.i; // returns undefined

Rewrite :

function helperFunction() {
  var i = 0;
  return {
    get: function() {
      return i;
    },
    set: function(val) {
      i = val;
    }
  };
};
var counter = helperFunction();
counter.get(); // returns 0;
counter.set(3);
counter.get(); // returns 3;
counter.i; // returns undefined

     So function foo(){ }(); doesn’t work as an IIFE because it is a function definition, it defines foo. But it’s not a function expression that is, it’s not understood by the JS Parser to actually call a function.
     So to work, wrap in ():
          (function foo(){ }());

1. **What's the difference between a variable that is: null, undefined or undeclared? How would you go about checking for any of these states?**

	| Undeclared | Undefined | Null |
	|:----------:|:---------:|:----:|
	| A variable is undeclared when it does not use the var keyword. | Something is undefined when it hasn't been defined yet. | null is a variable that is defined to have a null value. |
	| undeclared variables don't even exist. | undefined variable exist, but don't have anything assigned to them. | null variables exist and have null assigned to them. |	
	
	Example Undeclared:

	```
var declaredVariable = 1;
function scoppedVariables() {
	undeclaredVariable = 1;
	var declaredVariable = 2;
}
scoppedVariables();
undeclaredVariable; // 1
declaredVariable; // 1
	```

	Test Undefined:
	
	```
if (typeof(variable) !== "undefined") {
	console.log('variable is not undefined');
} else {
	console.log('variable is undefined');
}
	```
		
	Test Null:
	
	```
if (variable == null) {
	console.log('variable is null');
} else {
	console.log('variable is not null');
}
	```

1. **What is a closure, and how/why would you use one?**  
A closure is how a function "closes over" its variables and creates a different scope for them out of the way of the global scope.

	Example:
	
	```
function aClosure() {
  var longLivedVariable = "I'm here for a long time";
  var innerFunction = function inner() {
    return longLivedVariable;
  }
  return innerFunction;
}
var closure = aClosure(); // returns a reference to innerFunction
closure(); // returns the string in the variable
	```
	
	Why?
	* Closures can be used to save state since they keep access to the variables. Things that save state are like objects.
	* Hiding the function's private variables (this comes by default when declaring variables with the 'var' keyword in functions), and exposing public variables.
	
	```
function cat(name) {
  return {
    sayName: function() {
      return name;
    }
  }
}
var fluffy = cat('Mr. Fluffy');
fluffy.name // returns undefined
fluffy.sayName() // returns 'Mr. Fluffy'
var whiskers = cat('Whiskers');
whiskers.sayName() // returns 'Whiskers'
	```

1. **What's a typical use case for anonymous functions?**  
Anonymous functions are typically used as callbacks.

     Example:
     
	```
function takesACallback(callback) {
	return "The callback says: " + callback();
}
takesACallback(function() {
	return "I'm the callback!";
}); // returns "The callback says: I'm the callback!"
	```
	
1. **How do you organize your code? (module pattern, classical inheritance?)**

1. **What's the difference between host objects and native objects?**

	| Native Object | Host Object | User Object |
	|:-------------:|:-----------:|:-----------:|
	| Object in an ECMAScript implementation whose semantics are fully defined by this specification rather than by the host environment. | Object supplied by the host environment to complete the execution environment of ECMAScript. | |
	| Native objects are inherent to JS - they are available to you as long as you're using JS. | Everything that environment gives you. For the browser, this includes objects like window. Host objects can differ by environment (or host), so that Node wouldn't have access to window (which makes sense since there's no DOM for Node), but could have it's own host objects like NodeLists. | User objects are anything that the user defines. When you create a new object that is not directly a native object, you've made a user object. |
	| Examples: Object (constructor), Date, Math, parseInt, eval, string methods like indexOf and replace, array methods. | Examples: window, document, location, history, XMLHttpRequest, setTimeout, getElementsByTagName, querySelectorAll. | Example: If you create a new string ("Hello World") you created a native object, but if you create an instance of an object you've defined ("new Cat()") then it's a user object. |

1. **Difference between: function Person(){}, var person = Person(), and var person = new Person()?**

1. **What's the difference between .call and .apply?**  
Both methods allow us to invoke a function and pass parameters through.
               
	```
function printer(message) {
	console.log(message);
}
printer.call("hello"); // logs "hello"
printer.apply("world!"); // logs "world!"
	```

	| .call | .apply |
	|:-----:|:------:|
	| Pass the parameters comma separated (call -> comma). | Pass the parameters in an array (apply -> array). |
	| Use if we know how many arguments needed. | Use if we don't know how many arguments needed. |

	.call Example:

	```
function Person(name) {
  this.name = name;
  this.introduceSelf = function(greeting) {
    console.log(greeting + ", my name is " + this.name);
  }
}
var alice = new Person('Alice');
alice.introduceSelf.call({name: "Bob"}, 'Bonjour');
	```
	
	.apply Example:
	
	```
function Person(name) {
  this.name = name;
  this.introduceSelf = function(greeting) {
    console.log(greeting + ", my name is " + this.name);
  }
}
var alice = new Person('Alice');
alice.introduceSelf.apply({name: "Casey"}, ['Hola']);
	```
	
1. **Explain Function.prototype.bind.**  
Cache Example :

Bind

Allows you to set which object is treated as this within the function call.
Example:

function Person(name) {
  this.name = name;
  this.distractedGreeting = function() {
    var self = this; // cache
    setTimeout(function() {
      console.log("Hello, my name is " + self.name); // use cache
    }, 500);
  }
}

var alice = new Person('Alice');
alice.distractedGreeting(); // logs the string
Example:

function Person(name) {
  this.name = name;
  this.distractedGreeting = function() {
    setTimeout(function() {
      console.log("Hello, my name is " + this.name);
    }.bind(this), 500); // bind
  }
}

var alice = new Person('Alice');
alice.distractedGreeting(); // logs the string
Better example:

function Person(name) {
  this.name = name;
  this.distractedGreeting = function() {
    var self = this; // cache
    setTimeout(function() {
      console.log("Hello, my name is " + self.name); // use cache
      console.log(this.location.origin);
    }, 500); // no bind
  }
}


Warning example:

function Person(name) {
  this.name = name;
  this.distractedGreeting = function() {
    setTimeout(function() {
      console.log("Hello, my name is " + this.name);
      console.log(this.location.origin); // error
    }.bind(this), 500); // bind
  }
}

Note: this refers to the Person object, not the context of setTimeout.

1. **When would you use document.write()?**  
document.write() writes to the document (web page). It takes the content you want to write as a parameter. An invocation could look like this :

	```
document.write("<h1>JS is awesome!</h1>");
	```

	When to use?
	* For third party code to be included (such as ads or Google Analytics). Since document.write() is always available (mostly) it is a good choice for third party vendors to use it to add their scripts. They don't know what environment you're using, if jQuery is or isn't available, or what your onload events are. And with document.write() they don't have to.

1. **What's the difference between feature detection, feature inference, and using the UA string?**

Feature Detection
Feature Inference
UA String
Feature detection is when you check if a certain feature exists.
Feature inference is when we make an assumption that because one feature is present (or not) another one will be present (or not).
"UA" stands for user agent, which means the browser. Shows you version of browsers.
Good practice as we try to cover all of our bases with different browser implementations.
Bad practice as we're not checking for the feature we're using we're more likely to have inconsistencies.
Bad practice but slightly better practice than feature inference.
var text;
if(typeof(Text) === "function") {
  text = new Text('Hello World!');
} else {
  text = 'Hello World!';
}
if(typeof applyElement != 'undefined') {
  // now I know I'm not on IE, assume text is available
  text = new Text('Hello World!');
}
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2272.118 Safari/537.36

1. **Explain AJAX in as much detail as possible.**  
AJAX - Asynchronous JavaScript and XML
	* After loading, the client uses JavaScript to fire off a request to the server and listens to the response asynchronously. The response that comes back can be XML, but is often other formats, most often JSON.
	* The bit that makes AJAX so powerful is that it can update the page after it has finished loading. Before AJAX, any new content required an entire page refresh, even if it was a small change. This meant that users had to redownload a page for very little update content. Using AJAX meant that the front end could change without a full page refresh, thus giving a much faster respone time.
	* Originally, AJAX mostly returned HTML/XML snippets and the DOM would get updated with this new code when the AJAX returned. Now, however, it's more common for AJAX to get data and update the DOM as needed rather than doing a swap.

1. **Explain how JSONP works (and how it's not really AJAX).**  
JSONP - JavaScript Object Notation with Padding
	* Create a function in the global space to handle the JSON returned from the API.
               
	```
function myCallbackFunction(data) {
	console.log(data);
}
	```
	
	* Add a script tag to your page which calls the API and passes it an additional parameter (callback function).

	```	
<script src="http://cool-stuff.com/api.json?callback=myCallbackFunction"></script>
	```
	
	* The response is the JSON wrapped (Padded) with the name of the callback.
	
	```
myCallbackFunction({'awesome': 'data'});
	```
	Few things to note:
	
	* Generally, we don't write the script tag. Use jQuery.
	
	```
$.ajax({
	url: 'http://cool-stuff.com/api.json',
	dataType: 'jsonp',
	success: function(data) {
		console.log(data);
	}
});
	```

	* Safety First. Use good data validation, even if the data is "safe".
	* Can only use JSONP for get requests.

Have you ever used JavaScript templating? If so, what libraries have you used?

Explain "hoisting".
     Hoisting is when a JS declaration is lifted (“hoisted”) to the top of it’s scope by the JS interpreter.
     In JavaScript scopes are defined at function level. Many other languages define scope at a block level (as in an if block or for loop).

Variable Hoisting
Function Hoisting
Example:

var hoistedVariable = 1;

function scopingFunction() {
  if (!hoistedVariable) {
    var hoistedVariable = 10;
  }
  return hoistedVariable;
}

scopingFunction(); // returns 10
Example:

function containingFunction() {
  var hoisted = “I’m the variable”;
  function hoisted() {
    return “I’m the function";
  }
  return hoisted(); // results in a TypeError
}

containingFunction();
JS interpreter:

var hoistedVariable = 1;

function scopingFunction() {
  var hoistedVariable; // this line here
  if (!hoistedVariable) { // undefined
    hoistedVariable = 10;
  }
}

scopingFunction(); // returns 10
JS interpreter:

function containingFunction() {
  // hoisted section
  var hoisted;
  function hoisted() {
    return “I’m the function";
  }

  // rest of the code
  hoisted = “I’m the variable”;
  return hoisted();
}
containingFunction(); // results in a TypeError


Describe event bubbling.
Occurs when a user interacts with a nested element and the event propagates up ("bubbles") through all of the ancestor elements.

HTML
JavaScript
<div class="ancestor">
  <div class="parent">
    <button> Click me! </button>
  </div>
</div>
$( "button" ).click(function(event) {
  console.log( "button was clicked!" );
});

$( ".parent" ).click(function(event) {
  console.log( "child element was clicked!" );
});

$( ".ancestor" ).click(function(event) {
  console.log( "descendant element was clicked!" );
});

     Stopping event bubbling:
          $( "button" ).click(function(event) {
               event.stopPropagation(); // this line here!
               console.log( "button was clicked!" );
          });

What's the difference between and "attribute" and a "property"?

Property
Attribute
Properties are like instance variables for the particular element. Can have different types (boolean, string, etc.).
Attributes are in the HTML itself, rather than in the DOM.
<a href='page2.html'>Hi</a>

$('#linkID').prop('href', 'page1.html');
$('#linkID').prop('href'); // returns page1.html
<input type="checkbox" checked=true />

$('input').prop('checked'); // returns true
$('input').attr('checked'); // returns checked
Can also use custom properties (bad practice).
Useful when we want to set a custom attribute, that is, when there is no property associated.
<input type="text" />

$('input').prop('customAttribute', 'something custom');
$('input').prop('customAttribute'); // returns "something custom"
$('input').attr('customAttribute'); // returns undefined
<input type="text" />

$('input').attr('customAttribute', 'something custom');
$('input').attr('customAttribute'); // returns "something custom"
$('input').prop('customAttribute'); // returns undefined


Why is extending built in JavaScript objects not a good idea?
Extending object is when you add functionality to an object using the prototype.
               Array.prototype.first = function() {
                    return this[0];
               }

               var temp = [1, 2, 3];
               temp.first(); // returns 1

     Why bad?
If in the future, a browser decides to implement it's own version of your method, your method might get overridden (silently) and the browser's implementation would take over. So not extending in the first place is future proofing our code.
If we decide to overwrite the browsers definition, any future developer working on our code won't know about the change. They'll have a hard time getting up to speed.

     Safer:
Move our particular changes into a library (as with underscore.js). Particular methods are clearly marked and there's no chance of conflict.
Might be a good idea to add an extension for functionality that became available in later versions, but is not guaranteed to be available in our particular browser.

Difference between document load event and document ready event?

Document Load Event
Document Ready Event
Notation: window.onload
Notation: $(document).ready()
Fires when all of the content (images, scripts, CSS, and everything) has finished loading.
Fires when the HTML has finished loading.
Slow; try not to keep too much here.
Is just for jQuery; downside if not planning to include all of jQuery on the site.
Useful if we need to work with images of unknown size.
Can't interact with the DOM before HTML has finished loading, so we keep all our JS interactions wrapped up in the ready handler.


What is the difference between == and ===?

== (Equality)
=== (Strict Equality)
Converts the operands if they are not of the same type, then applies strict comparison.
Returns true if the operands are strictly equal with no type conversion.
Example:
1 == 1 // true
"1" == 1 // true
1 == '1' // true
0 == false // true
Example:
3 === 3 // true
3 === '3' // false

Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
Two numbers are strictly equal when they are numerically equal (have the same number value). NaN is not equal to anything, including NaN. Positive and negative zeros are equal to one another.
Two Boolean operands are strictly equal if both are true or both are false.
Two objects are strictly equal if they refer to the same Object.
Null and Undefined types are == (but not ===).

Explain the same-origin policy with regards to JavaScript.
Helps prevent malicious attacks (Cross Site Scripting) attacks by stopping code from another site executing on our site.
"origin" is the same if 3 things are the same:
the protocol (http vs. https).
the domain (subdomain.yoursite.com vs. yoursite.com vs.google.com)
the port (:80 vs. :4567).

Make this work:
     duplicate([1, 2, 3, 4, 5]); // [1, 2, 3, 4, 5, 1, 2, 3, 4, 5]

Why is it called Ternary expression, what does the word "Ternary" indicate?
    Ternary comes from the n-ary word setup. n-ary are operands. The prefix lists how many inputs the operand accepts.
unary: accepts 1 parameter, e.g. -1, where - is the operand, and 1 is the parameter.
binary: accepts 2 parameters, e.g. 2 + 3, where + is the operand, and 2 and 3 are the parameters.
ternary: accepts 3 parameters (rewrite of an if statement).

          if (conditional) { // one
               truethy_block; // two
          } else {
               falsey_block // three
          }

          is the same as

          conditional ? truethy_block : falsey_block; // operand is ?:

What is "use strict";? What are the advantages and disadvantages of using it?
JS is evaluated in strict mode if we put "use strict"; at the top of our code.
Strict mode throws more errors and disable some features in an effort to make your code more robust, readable, and accurate.

Advantages
Disadvantages
It catches some common coding bloopers, throwing exceptions.
Confusion of normal mode and strict mode.

Example: A user who is used to working in normal mode might call some actions on the library that wouldn't work as expected. Since normal mode don't have the advantages of extra errors being thrown, so the error might fail silently.
It prevents, or throws errors, when relatively "unsafe" actions are taken (such as gaining access to the global object).
Some developers don't like the constraint and want to use all the features of the language.
It disables features that are confusing or poorly thought out.



Create a for loop that iterates up to 100 while outputting "fizz" at multiple of 3, "buzz" at multiples of 5 and "fizzbuzz" at multiples of 3 and 5.
     
     for (var i = 1; i <= 100; i++)
          console.log((i % 3 == 0) ? (i % 5 == 0) ? "FizzBuzz" : "Fizz" : (i % 5 == 0) ? "Buzz" : i);

Why is it, in general a good idea to leave the global scope of a website as-s and never touch it?
     JS defaults all variables to the global scope unless they are explicitly defined elsewhere.

          function badlyScoped() {
               globalVariable = "I'm a global variable";
          }

          badlyScoped();
          console.log(globalVariable); // logs "I'm a global variable"

     Why global variables are bad?
It's harder to read the code and reason about it when variables seem to appear out of thin air.
Anyone can update a global variable from any point in the program at any time (and from any thread if there's more than one going).
General code smell.
It's probable that you'll encounter global variable name clashes since there's only one namespace.

Why would you use something like the load event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?

Explain what a single page app is and how to make one SEO-friendly.

What is the extent of your experience with Promises and/or their polyfills?


Network Questions
Traditionally, why has it been better to serve site assets from multiple domains?

Do your best to describe the process from the time you type in a website's URL to finish loading on your screen.
Browser checks cache; if requested object is in cache and is fresh, skip to #9.
Browser asks OS for server’s IP address.
OS makes a DNS lookup and replies the IP address to the browser.
Browser opens a TCP connection to server.
Browser sends the HTTP request through TCP connection.
Browser receives HTTP response and may close the TCP connection, or reuse it for another request.
Browser checks if the response is a redirect (3xx result status codes), authorization request (401), error (4xx and 5xx), etc. These are handled differently from normal responses (2xx).
If cacheable, response is stored in cache.
Browser decodes response (e.g. if it’s gzipped).
Browser determines what to do with the response.
Browser renders response, or offers a download dialog for unrecognized types.

What are the differences between Long-Polling, Websockets and Server-Sent Events?

Long-Polling
WebSockets
Server-Sent Events (SSE)
Client requests a webpage from  a server using regular http.
The requested webpage executes JavaScript which requests a file from the server.
Client requests a webpage from a server using regular http.
The requested webpage executes JavaScript which opens a connection to the server.
Client requests a webpage from a server using regular http.
The requested webpage executes JavaScript which opens a connection to the server.
Server does not immediately respond with the requested information but waits until there’s new information available. When there’s new information available, the server responds with the new information. The client receives the new information and immediately sends another request to the server, restarting the process.
Server and client can send each other messages when new data (on either side) is available.
Server sends an event to the client when there’s new information available.

Real-time traffic from the server to client and from client to server.
Real-time traffic from server to client

Use a server that has an event loop.
Use a server that has an event loop.

Possible to connect with a server from another domain.
Also possible to use a third party hosted web socket server.
Not possible to connect with a server from another domain.


Explain the following request and response headers:
Difference between Expires, Date, Age, and If-Modified-...
Do Not Track
Cache-Control
Transfer-Encoding
The transfer encodings the user agent is willing to accept: the same
ETag
X-Frame-Options

What are HTTP actions? List all HTTP actions that you know, and explain them.
GET
To retrieve information from the given server using a given UIR. Requests using GET should only retrieve data and should have no other effect on the data.
HEAD
Same as GET but transfer the status line and header section only.
POST
Used to send data to the server using HTML forms.
PUT
Replaces all current representations of the target resource with the uploaded content.
DELETE
Removes all current representations of the target resource given by a URI.
CONNECT
Establishes a tunnel to the server identified by a given URI.
OPTIONS
Describes the communication options for the target resource.
TRACE
Performs a message loop-back test along the path to the target resource.


Coding Questions
What is the value of foo?
     var foo = 10 + '20';

     Answer: 1020

How would you make this work?
     add(2, 5); // 7
     add(2)(5); // 7

What value is returned from the following statement?
    "i'm a lasagna hog".split("").reverse().join("");
     
     Answer: "goh angasal a m'i"

What is the value of window.foo?
    ( window.foo || (window.foo = "bar" ) );

     Answer: "bar"

What is the outcome of the two alerts below?
    var foo = "Hello";
     (function() {
          var bar = " World";
          alert(foo + bar);
     })();
     alert(foo + bar);

     Answer: 1st alert - "Hello World". 2nd alert - Error.

What is the value of foo.length?
    var foo = [];
     foo.push(1);
     foo.push(2);

     Answer: 2

