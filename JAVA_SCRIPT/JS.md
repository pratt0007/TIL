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
