# Crispy Crunchy JavaScript

Crispy Crunchy JavaScript is a series of blog posts designed to help Javascript programmers to transition from basic to advance level.

#### Assumptions: 
1. Readers are expected to have some experience in programming with JavaScript. 
2. They are expected to be aware of general JavaScript syntax and basic HTML DOM manipulation.


## Part-1: Interpreted and Object based

### It is interpreted.

Unlike C and Java, JavaScript is an interpreted language. It is also categorised as a scripting language. In case of C and Java, source code is read and compiled to, either a CPU understandable or a CPU friendly intermediary format. Both the formats are not intended to be friendly to human readers. The result of the successful compilation is stored in an executable file, that can be fed to a compatible CPU to get the output of the original C or Java source code.

Major benefit of the compilation are:
1. Capture of many language syntax errors in the original source code.
3. Compilation also performs many language dependent optimization to improved reliability and efficiency of the original source code.  
2. CPU friendly format doesn't need any intermediary processing, thus such programs run faster.


JavaScript, being an interpreted language, does not have a manual compilation step. The source code is directly fed to an interpreter or an execution engine that reads it line by line, converts it into CPU instruction and runs it immediately on the CPU without any manual intervention. In case of any error it stops further interpretation and execution of code. So in short running of JavaScript code is very much similar to a shell script (.bat or .sh files).

All browsers have built-in JavaScript interpreters/engines. During the loading of an HTML page, when browser encounters any JavaScript code or file in script tag, it stops the loading of html, and JavaScript source is fed to the engine where it is immediately executed. Only upon successful or failed execution of JavaScript, html loading is continued.

Note: Placement of script tag in an html file does matter. Html manipulation code in JavaScript would work only if corresponding html elements are already read and parsed.   

We also have standalone JavaScript engine/interpreters like nodejs. They can run JavaScript file directly without it being loaded through a browser.

**Pros of being interpreted language**.
1. **Faster development**: Since there is no compilation step involved, modified code is directly executed and tested. It saves time and hassle of compilation. 
2. **Easy maintenance**: It allows programmers to embed human readable source code directly into the html or similar places. It results an easier management of entire source code. Imagine how hard it would be to understand and manage an illegible compiled code in the middle of an html file.

Both the benefits lead to faster turnaround of programs. It is a major factor in rapid business development.

**Cons of being interpreted language**.
1. Since there is no compilation, programmers have tremendous responsibility to supply error free code to the production application environments. Nowadays, IDEs like Eclipse, Idea and Rubymine are very effective in catching possible syntax errors and even logical bugs at the time of writing of the source code itself.

2. Interpreted code executes slower than the compiled code, because of its conversion to a machine understandable format at the time of execution itself. But with modern CPUs and kind of programs where JavaScript is used, impact on the user experience is negligible.

### It is Object based.

Unlike C or other procedural language, every variable value in JavaScript is an object. For example,
```javascript
	var a = 10;    
	var b = 3.14;  
	var c = 'I am an Indian';
	var d = ['foo', 'bar'];

	console.log('a.constructor.name : ' + a.constructor.name);
	console.log('b.constructor.name : ' + b.constructor.name);
	console.log('c.constructor.name : ' + c.constructor.name);
	console.log('d.constructor.name : ' + d.constructor.name);
```
	Output: 
	a.constructor.name : Number
	b.constructor.name : Number
	C.constructor.name : String
	d.constructor.name : Array

Unlike Java, JavaScript before 2015 version doesn't implement some of the standard features of Object Oriented Programming like encapsulation, inheritance. We can achieve them programmatically using prototypical inheritance and clever programming.  
	 
Though in ECMAScript 2015(Standard for JavaScript) has introduced classes with features like encapsulation and inheritance, but they are syntactical sugar over existing prototypical based inheritance.

JavaScript objects are more like key-value pairs. They can follow a predefined structure (of key-value pairs), but their structure can be altered at any point of time. Any key can be added to or deleted from a pre constructed object as shown in following examples. Any such change doesn't alter the type name retrieved by way of **typeof** or **constructor.name** operations.

```javascript
var obj = {};

console.log('typeof obj : ' + typeof obj);
// two ways to add a property to a js object
obj.prop1 = 10;
obj['prop2'] = 'See that how one can modify an object';

console.log('obj ' + JSON.stringify(obj));
console.log('typeof obj : ' + typeof obj);

// delete a property of js object
delete  obj.prop1;
console.log('obj ' + JSON.stringify(obj));

/*
 typeof obj : object
 obj {"prop1":10,"prop2":"See that how one can modify an object"}
 typeof obj : object
 obj {"prop2":"See that how one can modify an object"}
 */	
```
### It is a weak type language.

Unlike C and Java, variables in JavaScript do no have any type associated with them. In other words, variable type can vary too. For example: 
```javascript
var a; // variable declaration

a = 10;  // Number value assignment
console.log('a.constructor.name : ' + a.constructor.name);

a = 'I am an Indian';  // String value assignment
console.log('a.constructor.name : ' + a.constructor.name);
```
    Output:
       a.constructor.name : Number
       a.constructor.name : String
 
Type of the variable can only be inferred by its value. It means, a programmer needs to be absolutely sure about the possible value/s of the variable at runtime, before calling any methods or operators on it. Since there is no compilation, any oversight will only be detected during the program execution. To create large reliable programs in JavaScript, it is absolutely essential that all test cases are covered in the test plan and all of them are thoroughly executed even for a small modification to the source code.
