---
layout: post
permalink: floating-point-arithmetic
title: Floating-Point Arithmetic
metadescription: "Ever wondered why 0.1 + 0.2 doesn't equal 0.3?"
---

A couple of days ago, I ran into an issue often overlooked in programming.

It’s the kind of thing you might not think about until it causes problems.

I was doing something like the following:

```csharp
Console.WriteLine(66 / 2.2 == 30.0);
```

Looking at it, you’d expect it to evaluate as `true`. But it won’t, and the reason is something called **floating-point arithmetic**.

#### What’s Floating-Point Arithmetic?

Floating-point numbers represent real numbers in a way that balances range and precision. Computers store these numbers in binary format, which brings in some problems. Not all decimal numbers can be represented in a finite number of 0s and 1s, leading to small inaccuracies.

Take the above example: `66 / 2.2`. You’d think this should be exactly `30`, right? Well, computers see it a bit differently. In JavaScript, C#, or Java, the result is slightly off, like `29.999999999999996`. This happens because `2.2` can’t be perfectly represented in binary.

As we already know, computers use 0s and 1s to store numbers. Some decimal numbers, like `2.5`, convert neatly into binary (`10.1`). But others, like `2.2`, turn into an endless repeating binary fraction: `10.00110011001100110011...`.

In the end, since computers have limited space to store these numbers, they cut off the repeating part, approximating the value. And this tiny approximation can lead to unexpected results in code.

#### Dealing with Floating-Point Issues

So, how did I handle this issue? I decided to use a small tolerance when comparing numbers. Instead of checking if they’re exactly equal, I check if they’re close enough. Here’s an example in JavaScript:

```javascript
const epsilon = 1e-10;
console.log(Math.abs(66 / 2.2 - 30) < epsilon);
```

This approach helps to avoid the issue with the precision of floating-point arithmetic and ensures that code behaves as expected.
