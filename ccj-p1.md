# Crispy Crunchy JavaScript

Crispy Crunchy JavaScript is a series of blog posts designed to help Javascript programmers to transition from basic to advance level

#### Assumptions: 
1. Reader are expected to have some experience in programming with JavaScript. 
2. They are expected to be aware of general JavaScript syntax and basic HTML DOM manipulation.


## Part-1:Interpreted and Object based

### It is interpreted

Unlike C and Java, JavaScript is interpreted language. It is also categorised as a scripting language. In case of C and Java, source code is read and compiled to either a CPU understandable format or a CPU friendly intermediary format. Both format are not intended to be friendly to the human readers. The result of successful compilation is be stored in a file to be fed to CPU to get the output of the original C or Java source code.

Major benefit of the compilation are:
1. The capture of many language syntax errors in the original source code.
3. Compilation also performs many language dependent optimization to improved reliability and efficiency of the original source code.  
2. CPU friendly format makes program run faster.


JavaScript, being scripted or interpreted language doesn't have a manual compilation step. the source code is directly fed to an interpreter or execution engine that reads it line by line, converts it into CPU instruction and run it immediately on the CPU without any manual intervention. In case of any error it stops the interpretation and execution of further code.

All browsers have built-in JavaScript interpreters. When an HTML source is parsed by browser window, any JavaScript code or file in script tag is fed to JavaScript engine and immediately executed. 

We also have standalone JavaScript engine of interpreters like nodejs. They can run JavaScript file directly without it being loaded through a browser.

Pros of being interpreted language.
1. faster development: Since there is no compilation step involved, modified code change is directly executed and tested. It save time and hassle of compilation. 
2. It allows programmers to embed human readable source code directly into the html or similar places. It results easier management of entire source code. Imagine how hard it would be to understand and management of different versions of non-friendly compiled code in the middle of html file.

Both benefits lead to faster turnaround of programs. It is a major factor in rapid business development.

Cons of being interpreted language.
1. Since there is no compilation, programmers have tremendous responsibility to supply error free code to the production application environments. Nowadays, IDEs like Rubymine are very effective in catching possible syntax errors and bugs at the time of source code writing itself.

2. Interpreted code executes slower than the compiled code, because of its conversion to a machine understandable format at the time of execution itself. But with modern CPUs and kind of programs where JavaScript is used, impact on user experience is negligible.

### It is Object based.

Unlike C or other procedural language, every variable value in JavaScript is an object. For example,
```javascript
	var a = 10;    
	var b = 3.14;  
	var C = 'I am an Indian';
	var d = ['foo', 'bar'];

	console.log('in js1. a.constructor.name : ' + a.constructor.name);
	console.log('in js1. b.constructor.name : ' + b.constructor.name);
	console.log('in js1. C.constructor.name : ' + C.constructor.name);
	console.log('in js1. d.constructor.name : ' + d.constructor.name);

	Result:
	/*
	in js1. a.constructor.name : Number
	in js1. b.constructor.name : Number
	in js1. C.constructor.name : String
	in js1. d.constructor.name : Array
	 */
```
Unlike Java, JavaScript before 2015 version does not implement some of the standard features of Object Oriented Programming like encapsulation, inheritance. We can achieve them programmatically using prototypical inheritance and clever programming.  
	 
Though in ECMAscript 2015(Standard for JavaScript) has introduced classes with features like encapsulation and inheritance, but they are syntactical sugar over existing prototypical based inheritance.

JavaScript objects are more like key value pairs. They can follow a predefined structure (of key value pairs), but their structure can be altered at any point of time. Any key can be added to or deleted from a pre constructed object as shown in following examples. Any such change doesn't alter the type name retrieved by way of typeof or constructor.name operations.

```javascript
var obj = {};

console.log('in js1. typeof obj : ' + typeof obj);

obj.prop1 = 10;
obj['prop2'] = 'See that how one can modify an object';

console.log('in js1. obj ' + JSON.stringify(obj));
console.log('in js1. typeof obj : ' + typeof obj);

delete  obj.prop1;
console.log('in js1. obj ' + JSON.stringify(obj));

/*
 in js1. typeof obj : object
 in js1. obj {"prop1":10,"prop2":"See that how one can modify an object"}
 in js1. typeof obj : object
 in js1. obj {"prop2":"See that how one can modify an object"}
 */	
```
### It is weak type language.

Unlike C and Java, variables in JavaScript do no have any type associated with them. In other words variable type can vary. For example: 
```javascript
var a; // variable declaration

a = 10;  // Number value assignment
console.log('in js1. a.constructor.name : ' + a.constructor.name);

a = 'I am an Indian';  // String value assignment
console.log('in js1. a.constructor.name : ' + a.constructor.name);

Result:
/*
   in js1. a.constructor.name : Number
   in js1. a.constructor.name : String
 */
```
Type of the variable can only be inferred by its type. It means programmer needs to be absolutely sure about the possible value/s of the variable at runtime, before calling any methods or operators on it. Since there is no compilation, any oversight will only be detected during the program execution. To create large reliable programs in JavaScript, it is absolute essential that all test cases are covered in the test plan and all of them are thoroughly executed even for small modification of the source code.
