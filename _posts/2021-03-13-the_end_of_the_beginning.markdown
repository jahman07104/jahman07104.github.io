---
layout: post
title:      "The differnce betweena regular function and an Arrow function."
date:       2021-03-13 11:15:03 -0500
permalink:  the_end_of_the_beginning
---


Functions can be defined in many ways in Javascript.
The usual ways are The function declaration and function expression I’m going to call these regular functions.
eg.
 Function declaration
function funcName(param,) {
  return `Hello, ${param}!`;
}

 Function expression
const name = function(param) {
  return `Hello, ${param}`;
}

However with ecmascript 6 the Arrow function was introduced
Here is an example of that 
eg.

const name = (param) => {
  return `Hello, ${param}!`;
}
Both regular and arrow functions work in a similar manner, But there are certain interesting differences between them,I will discuss a few here.The first and most obvious is the syntax..
the Arrow function is less verbose and enables a more concise way of writing functions as can be seen in  the examples above.

The “This” Keyword
The JavaScript This keyword refers to the object it belongs to. It has different values depending on where it is used: In a method, this refers to the owner object. ... In a function, this refers to the global object. In a function, in strict mode, this is undefined .

The behavior of this inside of an arrow function differs considerably from the regular function’s this behavior.
Unlike regular functions, arrow functions do not have their own “This” and can’t access any other properties from a parent object.In another words, the arrow function doesn’t define its own execution context.
THE value of this inside the arrow functions callback() is equal to to the this value of the outer function.In an arrow function the context value is always resolved lexically.

A consequence of this resolved lexically is that an arrow function cannot be used as a constructor.Arrow functions cannot be called with “new":
ES6 distinguishes between functions that are callable and functions that are constructible.
If a function is constructible, it can be called with new, i.e. new User(). If a function is callable, it can be called without new (i.e. normal function call).
Regular functions created through function declarations / expressions are both constructible and callable.
Arrow functions (and methods) are only callable i.e arrow functions can never be used as constructor functions. Hence, they can never be invoked with the new keyword.

If you try to invoke an arrow function prefixed with new keyword, JavaScrip throws an error.

this resolved lexically is one of the great features of arrow functions

Another difference is the implicit return. In a regular function if the return statement is missing, or there’s no expression after return statement, the regular function implicitly returns undefined. Arrow functions allow us to make use of implicit returns..if the arrow function is written without the curly braces, it will by default return what ever comes next after the arrow
