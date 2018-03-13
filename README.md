# JavaScript Functions and Closures #

## Functions ##
In JavaScript functions are the reusable blocks of code used to perform a specific task, they allow the code to be called many times.
- The functions in JavaScript are composed of the following components.
  - Function arguments  (values passed to a function are the function parameters)
  - Function body  (It consists statements written in JavaScript)
  - Function return statement  (It returns a value)
- A function can also access the outer variables as it works from inside out, the code outside of the function can’t access its local     variables.

- The following are different ways of creating a function in JavaScript

  - [Function Declaration](#function-declaration)
  - [Function Expression](#function-expression)
  - [Callback Function](#callback-function)
  - [Arrow Function](#arrow-function)
  - [Immediately-invoked function expression](#immediately-invoked-function-expression)
  - [_new Function_ syntax](#new-function-syntax)
 
 ### Function Declaration: ###
A function declaration is made of function keyword, followed by function name, a list of parameters in parenthesis and function body which contains the code of function body. 
 
 ```
 function square(number)
{
   return number*number;
}
```
- We can declare a function anywhere in the whole script.
- While executing the JavaScript code first the function declarations gets initialized.
- After processing the function declaration the execution continues.
- We can call a function created with function declaration even before its definition.

```
square(2);          //4
function square(number)
{
    return number*number;
}
```
- When a function declared in a code block (loops or conditional statements) it can be accessed anywhere within the block but not outside of the block.

### Function Expression: ###

A function expression is determined by a function keyword followed by function name (optional), a list of parameters (optional) in parenthesis and a pair of curly braces which contains the function code and this entire function is assigned to a variable.

```
let sayHi = function() 
{
  alert( "Hi" );
};
```
- The function created using function expression is considered as a value that is stored in the variable.
- We can call this function as the variable name followed by parenthesis.
- We can copy this function into another variable.
- A function expression is created when execution flow reaches it and can be usable from then, if the function is called before its       creation it gives error.
```
sayHello();       //sayHello is not defined

let sayHello = function() {
   document.write("Hello");
};
```
- The correct approach of creating a function using function expression inside a code block is to declare a variable outside of the code   block and assign a function to it.

### Callback Function: ###

A callback function, also known as a higher-order function, is a function that is passed to another function as a parameter, and the callback function is executed inside the other Function.

```
a("Hello", b);

function a(s, callback) {
     callback(s);
}

function b(s) {
     console.log(s + "  How are you ?");
}
```
- We can pass functions around like variables and return them in functions and use them in other functions.
- When we pass a callback function as an argument to another function, we pass only the function definition, we are not executing the     function in the parameter.
- Callback function is not executed immediately. It is “called back” at some specified point inside the containing function.
- We can use both the named and anonymous functions as callback functions.
- If we want to use a named function as callback function then first declare a named function and pass the name of that function to the   parameter.
- We can pass even more than one function as parameters into a function.
 
 
 ### Arrow Function: ###

An arrow function is defined using a pair of parenthesis that contains the list of parameters, followed by the arrow (=>) and a pair of curly braces {...} which contains the function body.

```
let sum = (a, b) => {  
  let result = a + b;
  return result;
};
alert( sum(1, 2) ); // 3
```
- When the arrow function has only one parameter, the pair of parenthesis can be omitted, when it contains a single statement, the curly   braces can also be omitted.

```
let double = n => n * 2;

alert( double(3) ); // 6
```
- If there are no parameters, parentheses should be empty but they cannot be omitted.
- The arrow function takes parameters from left side of arrow (=>) and evaluate the expression on right-side using them.
- The arrow functions are similar to function expressions, they are convenient for simple one-line functions.


### Immediately-invoked function expression (IIFE): ###

The IIFE function contains a function declaration which is enclosed in brackets, the IIFE function is created and called immediately, the code in the function body executes right away and has its own local variables.

```
(function() {

  let message = "Hello";

  alert(message); // Hello

})();
```
- If we give a name to the function declaration in IIFE it won’t work as JavaScript doesn’t allow function declarations to be called       immediately.
- Round brackets are needed to tell JavaScript that the function is created inside another expression, hence it is a function             expression, it needs no name and can be called immediately.
- There are few other ways to create function expression in JavaScript as follows.
```
(function() {
  alert("Brackets around the whole thing");
}());


!function() {
  alert("Bitwise NOT operator starts the expression");
}();


+function() {
  alert("Unary plus starts the expression");
}();
```

### _new Function_ syntax ###

The new Function syntax for function creation is as shown below
` let func = new Function ('arg1' , 'arg2' , 'functionBody') ; `
- The function parameters go first, and the body is last and all the parameters are strings.
```
let sum = new Function('a', 'b', 'return a + b');
alert( sum(1, 2) ); // 3
```
- If there are no arguments, then there is only a single argument, the function body.
- The arguments of the function body are separated from each other with semicolon.
- The major difference from other functions is this function is created from a string which is passed at run time.
- The functions created in this way don’t have the access to the current scope, they are always created in the global scope.




## Closures ##

- In JavaScript closure is an inner function which has the access to its enclosing function’s scope chain, the outer function is           returning the inner function.
- The most important feature of a closure is, it will have the access to the local variables of outer function even after the outer       function is returned.

```
 function counter() 
 {
  let index = 0;
  function increment() {
   index = index + 1;
    alert(index);
    return index;
    }
  return increment;
 }
  let a = counter();    
  let b = counter();    
     a();   // 1
     a();   // 2
     b();   // 1
     b();   // 2
     b();   // 3    
```
- The inner function has three scope chains.
  1. Its own scope(variables defined inside its curly brackets).
  2. Outer function’s scope.
  3. Global scope
- The outer function cannot access the inner function’s scope.
- Closures store references to the outer function’s variables, they do not store their actual values.
  
 
