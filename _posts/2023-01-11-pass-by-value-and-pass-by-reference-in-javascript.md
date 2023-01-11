---
layout: post
permalink: pass-by-value-and-pass-by-reference-in-javascript
title: Pass by Value and Pass by Reference in Javascript
metadescription: "Learn the differences between pass-by-value and pass-by-reference in JavaScript, and understand how they affect the behavior of your code. Discover how primitives and objects are passed to functions and how to write efficient and maintainable code."
---

In JavaScript, understanding the difference between pass-by-value and pass-by-reference is important for writing efficient and maintainable code. In this article, we will explore the two main ways in which a function can accept variables in JavaScript and how they differ from each other.

## Pass-by-Value

In JavaScript, when a primitive value such as a number, string, or boolean is passed as an argument to a function, it is passed by value. This means that a copy of the value is passed to the function, and any changes made to the argument inside the function will not affect the original value outside of the function.

```js
function addTwo(num) {
  num += 2;
}

let a = 5;
addTwo(a);
console.log(a); // Output: 5
```

As we can see, the value of the `a` variable does not change, even though we passed it to the `addTwo` function and added 2 to it inside the function. This is because the `addTwo` function is working with a copy of the value of the `a` variable, not the variable itself.

## Pass-by-Reference

In JavaScript, when an object such as an array or an object is passed as an argument to a function, it is passed by reference. This means that a reference to the memory location of the object is passed to the function. And any changes made to the object inside the function will affect the original object outside of the function.

```js
function addTwo(obj) {
  obj.num += 2;
}

let myObj = { num: 5 };
addTwo(myObj);
console.log(myObj.num); // Output: 7
```

As we can see in this example, the value of the `myObj.num` variable changes, because the `addTwo` function is working with a reference to the memory location of the `myObj` variable.

It's worth noting that when an object contains a primitive value, modifying the primitive within the object will change the original value and it's passed by reference.
For example:

```js
function addTwo(obj) {
  obj.num = obj.num + 2;
}

let myObj = { num: 5 };
addTwo(myObj);
console.log(myObj.num); // Output: 7
```

This is because the object `myObj` holds a reference to the value 5, which is a primitive type and when we add 2 to it, it updates the value stored in the memory.

## Conclusion

In JavaScript, variables are passed by value when they are primitive, and passed by reference when they are objects. This means that any changes made to primitive values within a function will not affect the original value outside of the function, while any changes made to objects within a function will affect the original object. Understanding the difference between these two ways of passing variables is crucial to writing efficient and maintainable code in JavaScript.
