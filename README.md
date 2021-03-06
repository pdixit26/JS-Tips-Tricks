# JS-Tips-Tricks... Concepts...  Modern JS practices...

# 1) Avoid globals
They can be very dangerous. Your code can be overwritten  your code being overwritten by any other JavaScript added to the page after yours.

# 2) var and let 
console.log(usingVar); // undefined
var usingVar = "defined";
console.log(usingVar); // "defined"

console.log(usingLet); // error
let usingLet = "defined"; // never gets executed
console.log(usingLet); // never gets executed

for (var count = 0; count < 5; count++) {
  console.log(count);
} // outputs the numbers 0 - 4 to the console
console.log(count); // 5


for (let otherCount = 0; otherCount < 5; otherCount++) {
  console.log(otherCount);
} // outputs the numbers 0 - 4 to the console
console.log(otherCount); // error, otherCount is undefined


3) Very common error 
for (var i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i + " second(s) elapsed");
  }, i * 1000);
}

output:
4 second(s) elapsed
4 second(s) elapsed
4 second(s) elapsed

There are various workarounds to this problem, but the most common one is to wrap the call to setTimeout in a closure, which will create a new scope with a different i in each iteration:
for (var i = 1; i <= 3; i++) {
  (function(i) {
    setTimeout(function() {
      console.log(i + " second(s) elapsed");
    }, i * 1000);
  })(i);
}

If you are using ECMAScript6 or later, then a more elegant solution is to use let instead of var, since let creates a new scope for i in each iteration:

for (let i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i + " second(s) elapsed");
  }, i * 1000);
}


# Callback hell
Sometimes you have a series of tasks where each step depends on the results of the previous step. This is a very straightforward thing to deal with in synchronous code:
var text = readFile(fileName),
  tokens = tokenize(text),
  parseTree = parse(tokens),
  optimizedTree = optimize(parseTree),
  output = evaluate(optimizedTree);
console.log(output);
When you try to do this in asynchronous code, it's easy to run into callback hell, a common problem where you have callback functions deeply nested inside of each other.


## Tools for dealing with asynchronous code
# Async libraries
If you are using lots of asynchronous functions, it can be worthwhile to use an asynchronous function library, instead of having to create your own utility functions. Async.js is a popular library that has many useful tools for dealing with asynchronous code.

# Promises[from ES6]

# Async/Await [frm ES7]
Async is for declaring that a function will handle asynchronous operations and await is used to declare that we want to “await” the result of an asynchronous operation inside a function that has the async keyword.
async function getSomeAsyncData(value){
    const result = await fetchTheData(someUrl, value);
    return result;
}

# Currying: 
It is the process of breaking down a fucntion into series of fucntion that each takes a single argument.  for example 
function sum(x, y, z) {
  return x + y + z;
}
console.log(sum(1, 2, 3) 

can be written as 
function sum(x) {
  return (y) => {
    return (z) => {
      return x + y + z;
    };
  };
}
console.log(sum(1)(2)(3))


# Hoisting 
Most commonly, people will explain hoisting as declarations being moved to top of your code. While this is what appears to be happening, it’s important to understand exactly what is going on. You see, your code isn’t moving anywhere. It isn’t magically being moved to the top of the file. What’s actually happening is that your function and variable declarations are added to memory during the compile phase.
a = 3;
console.log(a);
var a;
Output: 3

console.log(a);
var a = 3;
Output:Undefined // why???? 
It’s because JavaScript only hoists declarations. Initializations are not hoisted.


# Linting
“Linting” means running a very basic code quality tool which will look at yourJavaScript, and tell you where and how to clean it up.

In other words, it’s something that can AUTOMATICALLY find the dumb mistakes we all make, so you can fix them without thinking. It’ll make your code break less and prevent some very confusing problems.
Some of the linting tools are JSHint (new, fairly common, and the one I recommend), ESLint (newer, powerful)  and JSLint (the original JS linting tool).

# call() vs apply()
var test = function() {
  return arguments
}

var args1 = test.apply(this, ['Jack', 'John'], 'Jill')
var args2 = test.call(this, ['Jack', 'John'], 'Jill')

console.log(args1[1])
console.log(args2[1])

explanation: both can be called on function, while they run on context of the first argument. In call() the arguments are passed as they are while apply() expects second argument to be an array. 

output 
Jack,John
jack


console.log(args1[2])
console.log(args2[2])

output
Jill
John


# splice, slice, split
The splice() method adds/removes items to/from an array, and returns the removed item(s).
array.splice(index, howmany, item1, ....., itemX)
index: where to add/remove items.

Note: This method changes the original array.

The slice() method selects the elements starting at the given start argument, and ends at, but does not include, the given end argument.

Note: The original array will not be changed.


The split() method is used to split a string into an array of substrings, and returns the new array.
string.split(separator, limit)


# Top Javascript interview questions 
1. What is difference between var and let?
2. What is difference between == and === ?
3. What is difference between const and let? 
4. what is difference between undefined and null? 
5. what is difference between function declaration and funcion expression?
6. What is arrow functions? 
7. what is protype inheritance? 
8. what is promises? Why we should use them ?
9. what is clousure? whey we should use them?
10. what happens when SetTimeout(fun(){}, 0) is expecuted? 





# TOP CSS/HTML questions 
1. what is box model? explain with proper example and diagram for content, padding, margin, border. 
2. what is specificity? 
3. How to align block element in another block element? 
4. Difference between static, absolute, fixed, relative position?
5. Difference between visibility:hidden and display:none?
6. What is shadow dom? and what is its use? 
7. how to build a trianagle using pure CSS?
8. what is pseudo elements and pseudo clss in CSS? <p>Hi</p>   p:hove::after{content:"this is text for pseudo element"}
9. What is data attributes?


•	Web workers
•	Higher order functions 
•	single threaded and asynchronous nature of javascript --- 
•	inversion of control
•	dependency injection
