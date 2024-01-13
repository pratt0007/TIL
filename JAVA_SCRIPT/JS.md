# JAVA SCRIPT
 - JavaScript is an object-based scripting language which is lightweight and cross-platform.
 - JavaScript is not a compiled language, but it is a translated language. The JavaScript Translator (embedded in the browser) is responsible for translating the JavaScript code for the web browser.
 - Case sensitive.
## Features of JavaScript
There are following features of JavaScript:

- All popular web browsers support JavaScript as they provide built-in execution environments.
- JavaScript follows the syntax and structure of the C programming language. Thus, it is a structured programming language.
- JavaScript is a weakly typed language, where certain types are implicitly cast (depending on the operation).
- JavaScript is an object-oriented programming language that uses prototypes rather than using classes for inheritance.
- It is a light-weighted and interpreted language.
- It is a case-sensitive language.\
- JavaScript is supportable in several operating systems including, Windows, macOS, etc.
- It provides good control to the users over the web browsers.

### 3 Places to put JavaScript code
- Between the body tag of html
- Between the head tag of html
- In .js file (external javaScript)

#### 1.JavaScript Example : code between the body tag
- In the above example, we have displayed the dynamic content using JavaScript. Let’s see the simple example of JavaScript that displays alert dialog box.
```
<script type="text/javascript">  
 alert("Hello Javatpoint");  
</script>
```
#### 2. JavaScript Example : code between the head tag
- Let’s see the same example of displaying alert dialog box of JavaScript that is contained inside the head tag.

- In this example, we are creating a function msg(). To create function in JavaScript, you need to write function with function_name as given below.

- To call function, you need to work on event. Here we are using onclick event to call msg() function.
```
<html>  
<head>  
<script type="text/javascript">  
function msg(){  
 alert("Hello Javatpoint");  
}  
</script>  
</head>  
<body>  
<p>Welcome to JavaScript</p>  
<form>  
<input type="button" value="click" onclick="msg()"/>  
</form>  
</body>  
</html>
```
#### External JavaScript file
- We can create external JavaScript file and embed it in many html page.
- It provides code re usability because single JavaScript file can be used in several html pages.
- An external JavaScript file must be saved by .js extension. It is recommended to embed all JavaScript files into a single file. It increases the speed of the webpage.
- Message.js file
```
function msg(){  
 alert("Hello Javatpoint");  
}
```
HTML FILE
```
<html>  
<head>  
<script type="text/javascript" src="message.js"></script>  
</head>  
<body>  
<p>Welcome to JavaScript</p>  
<form>  
<input type="button" value="click" onclick="msg()"/>  
</form>  
</body>  
</html>
```
## Datatypes
- JavaScript is a dynamic type language, means you don't need to specify type of the variable because it is dynamically used by JavaScript engine. You need to use var here to specify the data type. It can hold any type of values such as numbers, strings etc.
- JavaScript provides different data types to hold different types of values. There are two types of data types in JavaScript.
     - Primitive data type
     - Non-primitive (reference) data type
 ![image](https://github.com/pratt0007/TIL/assets/100209212/2b28a27f-308a-4345-845b-03dd56ef0b64)
#### Undefined VS Null
![image](https://github.com/pratt0007/TIL/assets/100209212/d02041b5-4793-4111-8b70-5d8c1bfd2c80)
- Here if the datatype of the variable is not defined then if we print the variable it will give Undefined.
- But when we but var a = Null; then it will give value as NULL.
- document write(typeof(b)); TO get the type of data if not known!

### JavaScript Dialog , Boxes Alert, Prompt, Confirmation.
- Prompt Box. A prompt box is often used if you want the user to input a value before entering a page.
- When a prompt box pops up, the user will have to click either "0K" or "Cancel" to proceed after  entering an input value.
### A confirmation dialog
- box is mostly used to take user's permission on any option. It displays a dialog box with two buttons: Okk and Cancel.


### String Datatype
- Normally, JavaScript strings are primitive values, created from literals:
```
var firstName1 = "John";
```
- But strings can also be defined as objects with the keyword new:
```
var firstName2 = new String("John'");
```
- Now typeof(firstName1) = String
- And typeof(firstName2) = object---> Both are string but one is string and other os string object.
- When using the == operator equal strings are equal.
- When using the === operator, equal strings are not equal, because the === operator expects equality in both type and value.
## DOM Structure in JS(Document Object Model)
- TAG ->HTML closing and opening tags eg Head body all are tags
- Element-> Combination of tag open and close and data between it is called element.
- Attribute ->They are those which define the properties of the tag used.
```
<script type="text/javascript">  
function printvalue(){  
var name=document.form1.name.value;  
alert("Welcome: "+name);  
}  
</script>  
  
<form name="form1">  
Enter Name:<input type="text" name="name"/>  
<input type="button" onclick="printvalue()" value="print name"/>  
</form>
```
- Here Script = TAG
- Type == ATTRIBUTE
- whole combination == ELEMENT
### What is DOM structure
- JavaScript interacts with the DOM to dynamically update the content, structure, and style of a web page.
- When a web page is loaded, the browser creates a Document Object Model of the page.Acc. to w3c everything is a Node.
- Window is a global object and by writing it on console we get everything of the page.
- Document Object: The top-level object that represents the entire HTML or XML document. In a browser environment, you can access it using the document object. The whole page is document.
- Elements: Represent the HTML or XML tags in a document. Elements are organized in a tree structure, with the root being the html element. Elements can have attributes and content.
- 
![image](https://github.com/pratt0007/TIL/assets/100209212/da89008e-e01b-4db1-887d-794faa0870a8)
```HTML
<p id="hi"> Hello Word </p>
<script type = "text/javascript">
    var a = document.getElementById("hi").innerHTML;
    document.write(a);
</script>
```
- Here the content of that ID is stored in innerHTML.
```
<p class="hello"> Hello Word </p>
<p class="hello"> Hello Agian </p>
<script type = "text/javascript">
    var a = document.getElementByClassName("hello")[INDEX_VALUE].innerHTML;
    document.write(a);
</script>
```
- Since the class can be used multiple times hence it is takes as an array and to get something on the screen or print it we need to get its index value.
- 

