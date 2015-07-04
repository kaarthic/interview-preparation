Web Developer Interview Questions
==============================

## <a name='toc'>Table of Contents</a>

  1. [HTML Questions](#html)
  1. [CSS Questions](#css)

####[[↑]](#toc) <a name='html'>HTML Questions:</a>

1. **How do you optimize a website's assets?**  
	* Decrease Download Sizes  
		* Have all the assets as lightweight as possible.
		* Create lean HTML code using better semantic markup, which also overlaps with the SEO (search engine optimization) efforts that are a necessary part of the site creation process.
		* A good markup only describes the content, not the presentation of the page.
	* Make Fewer HTTP Requests
		* Combine scripts and style sheets.
		* Use image sprites.
		* Avoid redirects.
		* Avoid frames.
	* Use a Content Delivery Network
		* CDN is a network of servers in different geographical locations. Each server has a copy of a site's files.
	* Host Assets on Different Domains but Reduce DNS Lookups
		* Using 2 - 4 domains is an optimal number. (1 for HTML and 2 other for assets)
	* Place Assets on a Cookie-free Domain
	* Split the Assets Among Domains
	* Configure DNS Lookups on Forums and Blogs
	* Use the `Expires` Header
	
1. **What are three ways to reduce page load time?**
	* Optimize Images
		* Reduce the size of the images.
	* Minify CSS & JavaScript Code
		* Helps by removing unneeded whitespace and optimizing your code.
		* Minify when you are ready to launch a site.
	* Avoid using `@import`
		* file loaded through `@import` cannot be downloaded at the same time as the main stylesheet.
		* Copy the CSS from the external file into main stylesheet or use multiple `<link>` tags.
	* Reduce The Number of HTTP Requests
		* Combine files (scripts and stylesheets).
		* Use CSS sprites.
	* Leverage Browser Caching
		* Instruct the browser to cache a copy of files that don't change very often.
		* Configure web server to serve up resources with `Expire` headers.
		* Easiest way to update server configuration is to use a `.htaccess` file.
		
1. **What kind of things must you be wary of when design or developing for multilingual sites?**
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

1. **What is HTML?**  
HTML stands for **H**yper**T**ext **M**arkup **L**anguage. It is the dominant markup language for creating websites and anything that can be viewed in a web browser.

1. **What is the difference between HTML elements and tags?**  
HTML elements communicate to the browser how to render text. When surrounded by angular brackets <> they form HTML tags. For the most part, tags come in pairs and surround text.

1. **What is "Semantic HTML"?**  
Semantic HTML is a coding style where the tags embody what the text is meant to convey.  In Semantic HTML, tags like `<b></b>` for bold, and `<i></i>` for italic should not be used, reason being they just represent formatting, and provide no indication of meaning or structure. The semantically correct thing to do is use `<strong></strong>` and `<em></em>`. These tags will have the same bold and italic effects, while demonstrating meaning and structure (emphasis in this case).

1. **What does `DOCTYPE` mean?**  
The term `DOCTYPE` tells the browser which type of HTML is used on a webpage. In turn, the browsers use `DOCTYPE` to determine how to render a page. Failing to use `DOCTYPE` or using a wrong `DOCTYPE` may load your page in Quirks Mode.

1. **What's the difference between standards mode and quirks mode?**  
Quirks Mode is a default compatibility mode and may be different from browser to browser, which may result to a lack of consistency in appearance from browser to browser.

1. **What are the limitations when serving XHTML pages?**  
The biggest issue is the poor browser support for XHTML currently enjoys. IE and a number of other user agents cannot parse XHTML as XML. Thus, it is not the extensible language it was promised to be.

1. **How many HTML tags should be used for the most simple of web pages?**  
8 total. 4 pairs of tags.

	```
<html>
	<head>
		<title>Simplest page ever!</title>
	</head>
	<body>
		Doesn't get simpler than this.
	</body>
</html>
	```
	
1. **How do you make comments without text being picked up by the browser?**  

	```
	<!-- Insert comment here. -->
	```
	
1. **What is the difference between linking to an image, a website, and an email address?**  

	| Image | Website | Email |
	|:-----:|:-------:|:-----:|
	| `<img>` tags | `<a>` tags | `<a>` tags |
	| Specify source using `src` attribute | Specify link in the `href` attribute | Specify email in the `href` attribute |
	
	```
<img src=”HTMLrocks.jpg”></img>
<a href=”skilprelaunch2.wpengine.com”>Skilledup</a>
<a href=”brad@skilledup.com”>Email Me</a>
	```
	
1. **My hyperlink or image is not displaying correctly, what is wrong with it?**  
It could be any number of things, but the most common mistakes are leaving out a tag bracket or quote missing for href, src, or alt text may be the issue. You should also verify the link itself.

1. **What is the syntax difference between bulleted list and numbered list?**  
	* Bulleted list : `<ul>` (unordered list)
	* Numbered list : `<ol>` (ordered list)
	
1. **What is the difference between `<div>` and `<frame>`?**  
A `<div>` is a generic container element for grouping and styling, whereas a `<frame>` creates divisions within a web page and should be used within the `<frameset>` tag. The use of `<frame>` and `<frameset>` are no longer popular and are now being replaced with the more flexible `<iframe>`, which has become popular for embedding foreign elements (ie. Youtube videos) into a page.

1. **What is the difference between the application model of HTML and HTML5?**  
Trick question, there is no difference. HTML5 is a continuum of HTML and just a souped up version of the original HTML. There has been no major paradigm shift.

1. **What's the real difference between HTML and HTML5?**  
HTML was a simple language for laying out text and images on a webpage, whereas HTML5 can be viewed as an application development platform that does what HTML does that and more, including better support for audio, video, and interactive graphics. It has a number of new elements, supports offline data storage for applications, and has more robust exchange protocols. Thus, proprietary plug-in technologies like Adobe Flash, Microsoft Silverlight, Apache Pivot, and Sun JavaFX are no longer needed, because browsers can now process these elements without additional requirements.

1. **What is the new `DOCTYPE`?**  
Instead of typing out a ridiculously long `DOCTYPE` statement to tell the browser how to render your webpage, this long line of code has been truncated to `<!doctype html>`.

1. **What are some new HTML5 markup elements?**  
`<article>`, `<aside>`, `<bdi>`, `<command>`, `<details>`, `<figure>`, `<figcaption>`, `<summary>`, `<header>`, `<footer>`, `<hgroup>`, `<mark>`, `<meter>`, `<nav>`, `<progress>`, `<ruby>`, `<rt>`, `<section>`, `<time>`, and `<wpr>`.

1. **What elements have disappeared?**  
As mentioned above, `<frame>` and `<frameset>` have been eliminated. Other elements that are no longer supported include: `<noframe>`, `<applet>`, `<bigcenter>` and `<basefront>`.

1. **What are the new media-related elements in HTML5?**  
HTML5 has strong support for media. There are now special `<audio>` and `<video>` tags. There are additional A/V support tags as well: `<embed>` is a container for 3rd party applications. `<track>` is for adding text tracks to media. `<source>` is useful for A/V media from multiple sources.

1. **What are the new image elements in HTML5?**  
Canvas and WebGL. `<Canvas>` is a new element that acts as a container for graphical elements like images and graphics. Coupled with JavaScript, it supports 2D graphics. WebGL stands for Web Graphics Language, a free cross-platform API that is used for generating 3D graphics in web browsers.

1. **What's the difference between SVG and `<Canvas>`?**  
`<Canvas>` is an element that manipulates two-dimensional (2D) pixels while Scalable Vector Graphics works in 2D and three-dimensional (3D) vectors. Essentially, `<Canvas>` is to SVG as Photoshop is to Illustrator.

1. **What are some new input attributes in HTML5?**  
There are many new form elements including: datalist, datetime, output, keygen, date, month, week, time, number, range, email, and url.

1. **What are data- attributes good for?**  
The HTML5 data- attribute is a new addition that assigns custom data to an element. It was built to store sensitive or private data that is exclusive to a page or application, for which there are no other matching attributes or elements.

1. **What is the difference between HTML5 interaction in Sencha and Twitter/Bootstrap?**  
Sencha and Twitter/Bootstrap are both HTML development frameworks that integrate HTML5, CSS3, and JavaScript. The major difference is that in Sencha, the three languages are all comingled together in code, whereas in Bootstrap, HTML and CSS and decoupled.

1. **What purpose do Work Workers serve and what are some of their benefits?**  
Web Workers are background scripts that do not interfere with the user interface or user interactions on a webpage, allowing HTML to render uninterrupted while JavaScript works in the background.

1. **What are some of the major new API's that come standard with HTML5?**  
Media API, Text Track API, Application Cache API, User Interaction, Data Transfer API, Command API, Constraint Validation API, and the History API.

1. **What is the difference in caching between HTML5 and the old HTML?**  
An important feature of HTML5 is the Application Cache. It creates an offline version of a web application. and stores website files such as HTML files, CSS, images, and JavaScript, locally. It is a feature that speeds up site performance.


####[[↑]](#toc) <a name='css'>CSS Questions:</a>

1. 















