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

Same rule applies to case when object is passed to function. Here is an example:

```js
function modifyObject(obj) {
  // Assigning a completely new object to the 'obj' parameter
  obj = { newValue: 'This is a new object' };
}

let originalObj = { value: 'This is the original object' };
console.log('Original object before function call:', originalObj);

// Call the function with the original object
modifyObject(originalObj);

console.log('Original object after function call:', originalObj);
```

In this example, we have a function called `modifyObject` that takes an object as a parameter and assigns a completely new object to that parameter. We then have an `originalObj` outside of the function, which we log before and after calling the `modifyObject` function.

When you run this code, you'll see that the `originalObj` remains unchanged after the function call because the function assignment to the `obj` parameter inside the function does not affect the original object. This demonstrates that assigning a new object within the function does not modify the original object outside the function.

## Pass-by-Reference

In JavaScript, when an object, such as an array or an object, is passed as an argument to a function, it may seem as if it's passed by reference. However, it's essential to clarify that JavaScript actually passes a reference to the object's memory location by value. This means that a copy of the reference to the object is passed to the function, rather than the object itself. Consequently, any changes made to the object's properties inside the function will affect the original object outside of the function, because both the original object and the function's parameter hold references to the same memory location.

Here's an example illustrating this behavior:

```js
function addTwo(obj) {
  obj.num += 2;
}

let myObj = { num: 5 };
addTwo(myObj);
console.log(myObj.num); // Output: 7
```

In this example, the `addTwo` function operates on a reference to the memory location of the `myObj` variable, which is why changes to the object's property `num` persist outside of the function. However, it's important to note that the actual object reference is passed by value, so you cannot assign a completely new object to the outer variable that is passed to the function.

## Conclusion

In JavaScript, variables are passed by value, but with objects, what is actually passed by value is a reference to the object's memory location. This means that any changes made directly to the passed variable within a function will not affect the original value outside of the function. When it comes to objects, changes made to the object's properties within a function will affect the original object, as a copy of the reference to the object's memory location is passed by value.

However, it's important to note that if you assign a completely new object to a function argument inside the function, it won't change the original object that was assigned to that argument before the function call. In such cases, the function parameter is essentially reassigned to a new object, breaking the reference to the original object. Understanding this distinction is crucial for writing efficient and maintainable code in JavaScript.
