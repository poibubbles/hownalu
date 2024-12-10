### [Method definitions are not constructable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions#method_definitions_are_not_constructable)

Methods cannot be constructors! They will throw a [`TypeError`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError) if you try to instantiate them. On the other hand, a property created as a function can be used as a constructor.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions

ES6 introduced some new shortcuts for assigning properties to [variables](https://www.codecademy.com/resources/docs/javascript/variables) known as _destructuring_. (Property value shorthand.)
https://www.codecademy.com/courses/introduction-to-javascript/lessons/advanced-objects/exercises/prop-val-shorthand

ES6

	obj = {
		prop: 2,
		meth() {
			this.prop; }}

	obj = {
		prop: 2,
		meth: () => {
			this.prop; // not what you want }}

Arrow functions inherently _bind_, or tie, an already defined `this` value to the function itself that is NOT the calling object. In the code snippet above, the value of `this` is the _global object_, or an object that exists in the global scope, which doesn’t have a `dietType` property and therefore returns `undefined`. To read more about either arrow functions or the global object check out the MDN documentation of [the global object](https://developer.mozilla.org/en-US/docs/Glossary/Global_object) and [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions). The key takeaway from the example above is to _avoid_ using arrow functions when using `this` in a method!
https://www.codecademy.com/courses/introduction-to-javascript/lessons/advanced-objects/exercises/arrow-and-this

..SO WHAT DOES THIS DO?

	obj = {
		prop: 2,
		meth = function() {
		}}

Destructured assignment:

	const { field } = obj;

`Promise.all()` also has the benefit of _failing fast_, meaning it won’t wait for the rest of the asynchronous actions to complete once any one has rejected.

Creating an error doesn't cause a program to stop - throwing an error will.

Currying with arrow functions is cool. Somebody was looking forward to that.

Hoisting postpones initialization until code is executed, which is why const arrow functions aren't available globally from the start. Variable names and function declarations are raised to the top of their scope, function declarations are immediately initialized.

`var` variables are hoisted to the top of function blocks but not other blocks. `var` variables are initialized with undefined when hoisted. `let` and `const` aren't initialized with anything therefore they will throw a `ReferenceError` if used before being assigned.

And it looks like vars are hoisted a little higher than functions:

	var foo = function() { console.log('var foo func'); }
	function foo() { console.log('func foo'); } 
	foo()
	
..and:

	function foo() { console.log('func foo'); }
	foo = function() { console.log('foo func'); }
	
..and avoid:

	foo();
	let foo = function () { }

..which throws a SyntaxError because foo() is already defined/initialized/used?

## Memory leaks

Good exercise in debugging via dev tools: https://www.codecademy.com/courses/learn-intermediate-javascript/articles/javascript-debugging-memory-issues

"We refer to them as detached DOM elements because they’ve been created using document.createElement(), but are not appended to the document yet."

### Messy Closures

	function bigObjMaker() {
		const bigObj = {};
		return (key, val) => {
			bigObj[key] = val;
			console.log(bigObj);
		}}
	
	let bigMemoryUser = bigObjMaker();
	Array(1000).fill(1).map((x,i) => {
		bigMemoryUser(i, i);
		});

#### Dangling Timers and Event Listeners

	function cb() {
		let count = 0;
		return function() {
			count++;
			console.log(count);
		}}
	
	setInterval(cb(), 1000);
  
#### Circular References

	let first = new Object();
	let second = new Object();
	first.aProperty = second;
	second.anotherProperty = first;

#### Declaring Variables on the Global Object

	function helloWorld() {
	// below greeting does not use a `let`, `const` or `var` statement to
	// declare the variable, so it's added to the global object after we
	// call `helloWorld()`
		greeting = "Hello world"; 
	// This also leaks into the global `this`
		this.greeting2 = "Goodbye!"; 
	}
	
	helloWorld();