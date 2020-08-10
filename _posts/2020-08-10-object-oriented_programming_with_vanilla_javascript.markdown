---
layout: post
title:      "Object-Oriented Programming with Vanilla Javascript"
date:       2020-08-10 17:04:27 +0000
permalink:  object-oriented_programming_with_vanilla_javascript
---


The paradigm of Object-Oriented Programming (OOP) is quite popular; understandably so, as it provides a conceptual framework for approaching programming in a manner that is similar to how we naturally interpret the world around us. Importantly, it provides us with reusable code that is defined in our classes and applicable to every instance of that class. Along the same lines, it provides us with inheritance, where multiple classes can gain the functionality of another class without having to rewrite even more code.

That being said, OOP is not the only programming paradigm out there. As such, different programming languages may have natural strengths in a variety of paradigms. JavaScript being one of these languages.

JavaScript is a multi-paradigm language, in that it is effective for functional programming through its treatment of functions as first-class citizens, while also supporting object-oriented programming through its prototypal inheritance.

With my main programming to date having been in Ruby, I have found a particular love and appreciation for abstraction through object-oriented programming. The transition to working in JavaScript, however, was not as smooth as I would have hoped. Even though JavaScript does support OOP, its implementation does have a few differences to adjust to.


# “this”

Loss of “this” in functions within functions. The challenge is not so much that the “this” is lost, but rather, the context of the inner function is being defined as the document instead of the context of the “this” that is being held by the outer function. The impact made by the defining of the “this” is that object-oriented programming in JavaScript feels less intuitive.

Thankfully the need for actively defining the “this” context in JavaScript was noted early on, and so the use of apply() and call() were introduced in ECMAScript 3, and bind() was introduced in ECMAScript 5. The use of apply() and call() allow for the immediate invocation of a function with a defined “this”, while bind() defines a function that now has the “this” context bound to its execution.


# Prototypal Inheritance

Until relatively recently in the life of JavaScript the language couldn’t directly build a class, but instead directly used what is the engine of OOP in JavaScript—prototypal inheritance. This allows functions defined in one object to be called on another object—in other words, inherited—so long as the prototype of the second object has been assigned to that of the first. This behavior of inheriting the functions (or characteristics) of another object is the backbone of object orientation, and therefore allows JavaScript to be written using this programming paradigm. Though functional, the implementation of it doesn’t feel very smooth and and at times is down-right clunky.

Finding this approach confusing? Many others would agree with you, and this is where ECMAScript 6 steps in.


# ECMAScript 6

Ever notice how the conversation around JavaScript will almost always bring up ECMAScript 6 (ES6)? Despite this not being the most recent of updates to happen to JavaScript, it is one of the most widely talked about. My personal opinion on why this is, has to do with ES6 appearing to be a turning point for JavaScript. It is at this time where programmers no longer have to build object orientation through the language of functions and prototypes, but instead are provided new tools, one of which is called class. The introduction of class allows for a much smoother and more natural feeling of creating objects and instances of objects.

The other major addition from ES6 that makes it stand out is the addition of arrow functions. Not only does this simplify function expressions, which are such a central part to JavaScript, but also doesn’t define its own “this”, but instead uses the “this” defined in the enclosing scope. This change to how functions handle the “this” definition has reduced the number of circumstances that necessitate the use of bind when working with object-oriented programming.

