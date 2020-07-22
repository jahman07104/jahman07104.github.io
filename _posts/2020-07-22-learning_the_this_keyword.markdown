---
layout: post
title:      "Learning the this Keyword"
date:       2020-07-22 15:29:13 +0000
permalink:  learning_the_this_keyword
---


The content of your blog post goes here.
THe best way for a novice to learn the this keyword in Javascript is to first get an understanding of what an object is.
Objects are the basic building blocks of Javascript and the this key word is a special object. The this object is by default is a global object which means if a code is being executed as part of a function call then this refers to a global object.
Additionally the value of "this" can also be observed at every line of JavaScript execution. The value of "this" is dependent on how the code is being executed and the novice will need to move on to understanding the basics of the JavaScript runtime environment and how a JavaScript code is executed.The JavaScript runtime has a setup of stacks of commands in an execution context, and the execution context thats at the top of this stack is the one currently being executed. The object this in this case will refer to changes every time the execution context is carried out.

There are a few tricks to figure out the value of this
as stated above by default this refers to a global object, which is global  and a window object in the case of a browser
When a method is called as a property of an object, then this refers to the parent object
When a function is called with the new operator, then this refers to the newly created instance
When a function is called using the call and apply methods, then this refers to the value passed as the first argument of the call or apply method
Admittedly, the value of this can sometimes be confusing, but the above rules can help you to figure out the value of this.

