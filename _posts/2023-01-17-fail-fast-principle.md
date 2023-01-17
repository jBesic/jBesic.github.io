---
layout: post
permalink: fail-fast-principle
title: What is Fail Fast principle in software engineering
metadescription: "The Fail Fast principle in software engineering is a strategy that encourages the early detection and reporting of errors or exceptional conditions in a program, rather than allowing them to persist or propagate."
---

The "Fail Fast" principle in software engineering is a strategy that encourages the early detection and reporting of errors or exceptional conditions in a program, rather than allowing them to persist or propagate. The idea is that by failing fast, the program can stop execution as soon as an error occurs and provide an immediate notification to the developer or user, rather than allowing the error to go unnoticed and potentially cause more damage or complexity down the road. This approach can help to reduce the overall cost and impact of bugs and errors in a software system, by making them easier to detect and fix.

An example of code that does not follow the "Fail Fast" principle in javascript could be a method that attempts to divide two numbers without first checking if the denominator is zero.

```js
function divide(int numerator, int denominator) {
    return numerator / denominator;
}
```

In this example, if the denominator is zero, the program will throw an ArithmeticException at runtime. This is not following the "Fail Fast" principle, because the error is not being detected and handled early in the program's execution. Instead, it is allowing the error to propagate and potentially cause complexity later on. To follow the "Fail Fast" principle, the method should check for this condition before performing the division:

```js
function divide(int numerator, int denominator) {
    if (denominator === 0) {
        throw new Error("Cannot divide by zero.");
    }

    return numerator / denominator;
}
```

This way, the program will stop execution immediately and provide an immediate notification to the developer or user if the denominator is zero, rather than allowing the error to go unnoticed.

Here is an example of "Fail Fast" in javascript when fetching data from another service via HTTP:

```js
function dataFetcher(url) {
    return fetch(url)
        .then(response => {
            if (!response.ok) {
                throw new Error(`Error fetching data from URL: ${url}, HTTP status code: ${response.status}`);
            }
            return response.json();
        })
        .then(jsonData => {
            // Do something with the JSON data
            // ...
            return jsonData;
        })
        .catch(error => {
            throw new Error(`Error fetching data from URL: ${url}, ${error}`);
        });
}
```

In this example, the `dataFetcher` function uses the `fetch` function to send an HTTP GET request to the specified URL. It then checks the `ok` property of the `response` object which is a boolean indicating if the status code is in the range 200-299. If it's not, the function throws an error with a detailed message.

The `response.json()` method is used to parse the response body as JSON. The code after that can access the data and do something with it, for example, by logging it to the console or by returning it to the calling function. This way, the code can continue to execute only if the request was successful and no error was thrown.

## Stop after first failing test

Unit tests are a powerful tool for ensuring that code follows the "Fail Fast" principle. They allow developers to test individual units of code, such as functions or methods, in isolation from the rest of the system. This makes it easier to test the code's behavior under different conditions.

When writing unit tests, developers should focus on testing the code's behavior under different conditions, including exceptional or error scenarios. This can include things like testing that the code correctly handles invalid input, that it fails fast when certain conditions are met, and that it doesn't continue to execute after an error or exception has occurred. By verifying that the code behaves correctly under these scenarios, developers can be confident that the code is following the "Fail Fast" principle.

For example, when testing a method that performs a division, developers should test the method with various inputs, including zero and non-zero denominator. If the code throws an exception when the denominator is zero, it means that the code is following the "Fail Fast" principle. And if it continues to execute, it means that the code is not following the principle.

Additionally, unit tests can help to catch regressions, which are bugs that are introduced later in development, and ensure that changes to the codebase don't break existing functionality.

In summary, unit tests can help to ensure that the code is following the "Fail Fast" principle by giving developers a way to test the code's behavior under different conditions, including exceptional or error scenarios, and catch any regressions.

## Conclusion

In order to adhere to the "Fail Fast" principle in software development, it's crucial to identify and handle errors as early as possible in the code, produce meaningful exception messages, and to write comprehensive unit tests to decrease the number of potential errors. This proactive approach will ultimately save time and effort in debugging and troubleshooting in the future.
