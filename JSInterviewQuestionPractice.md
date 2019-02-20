# Q:What is difference between var and let?
Ans: 
1. Let is ES15. Var is there since beginning
2. Let has block scope. Var has function scope. 
3. Variable created by VAR gets hoisted but by LET it does not. 
=================================================================================================
Q: What is difference between == and === ?
Ans:
1. == checks only value. === checks value and type. 
Better answer: == converts type of RHS to LHS and then compare value. === doesnt do that.
=================================================================================================
Q:What is difference between const and let?
1. You can;t change const value once assigned. In let you can assign as many times as you want. 
const c=1;
c=2; // error 
const c1 = [1,2];
c1.push(3); // gives [1,2,3] .. you can modify objects but not re-assign.
==================================================================================================
what is difference between undefined and null?
1. They both represent empty value. If you declared value but not assigned it takes undefined. null is used to make value clear.
2. typeof(undefined) = undefined. typeof(null) = object.
==================================================================================================
what is difference between function declaration and funcion expression?
function foo(){
console.log("function declaration");
}

let foo = function(){
console.log("function expression"); // used to pass function as parameter
}
==================================================================================================
What is arrow functions?
1. Arrow function makes code concise without use of function and return keyword. 
var multiplyES5 = function(x, y) {
  return x * y;
};

// ES6
const multiplyES6 = (x, y) => {  x * y };
2) In code with multiple nested functions, it can be difficult to keep track of and remember to bind the correct this context. 
In ES5, you can use workarounds like the .bind method (which is slow) or creating a closure using var self = this;.
Because arrow functions allow you to retain the scope of the caller inside the function, you don’t need to create self = this 
closures or use bind.
=====================================================================================================
what is protype inheritance?
Every object in JS has property prototype. When you create an object from other object you inherit all the property from the parent. 
let car = functio(modal)
{
  this.modal = modal;
}
car.protype.getModal = function(){ return this.modal;}

let honda = new car('Honda');
let hundai = new car('hundai');

console.log(honda.getModal()); // prints honda;
console.log(hundai.getModal()); // prints hundai
===================================================================================================================================
what is promises? Why we should use them ?
Used in Async programming. When you are waiting something to happen and then want to call some another callback. 
Nested callbacks are hard to erad hard to debug and can lead to callback hell. 
 var p1 = new Prmoise(function(resolve, reject){
 });
 p1.then()

===================================================================================================================================
what is clousure? whey we should use them?
when a function return a function and it holds the environment of the function and that is called the closure

let obj = function(){
let i =0;
return {
setI(k){i=k;}.
getI(){ return i}
}

}
===================================================================================================================================
what happens when SetTimeout(fun(){}, 0) is executed?
0 doesnt mean that it will execute right way. It will be put in event loop and it will exceute when all sync call gets executed.
===================================================================================================================================
What is variable and function hoisting 
JavaScript interpreter "looks ahead" to find all the variable declarations and "hoists" them to the top of the function. 
var declaredLater;
console.log(declaredLater); // Outputs: undefined
declaredLater = "Now it's defined!";
console.log(declaredLater); // Outputs: "Now it's defined!"
So that covers variable hoisting, but what about function hoisting? Despite both being called "hoisting,"
the behavior is actually quite different. Unlike variables, a function declaration doesn't just hoist the function's name. It also hoists the actual function definition.
isItHoisted(); // Outputs: Yes!

function isItHoisted() {
    console.log("Yes!");
}
===================================================================================================================================
What is close method in Javascript do?
if its called on window onject it closes the window and if its called on the document object it closes the document. 
======================================================================================================================================


