---
layout: post
permalink: java-is-pass-by-value
title: Java is pass by value
metadescription: "Learn about passing method arguments in Java and the differences between passing by value and passing by reference. Understand how this affects the way methods interact with their arguments and how to write more efficient and optimized code in Java."
---

Java is a popular and widely used programming language that is known for its simplicity and ease of use. However, one of the key concepts to understand when working with Java is how method arguments are passed. Depending on the programming language and the way the method is defined, arguments can be passed by value or by reference. In this article, we will explore how method arguments are passed in Java and the differences between passing by value and passing by reference.

## Java's Approach to Passing Method Arguments: By Value

In Java, all method arguments are passed by value. This means that when a method is called, a copy of the argument value is passed to the method, rather than a reference to the original memory location of the argument. This applies to both primitive data types, such as integers and booleans, as well as objects.

Let's consider the following example to understand how passing by value works in Java:

```java
class Person {
    private String name;
    
    public Person(String name) {
        this.name = name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getName() {
        return this.name;
    }
}

class Main {
    public static void changeName(Person person) {
        person.setName("John");
    }
    public static void main(String[] args) {
        Person p = new Person("Jane");
        changeName(p);
        System.out.println(p.getName()); // Output: John
    }
}
```

In this example, we have a `Person` class with a `name` attribute and methods to set and get the name. We also have a `Main` class with a `changeName` method that takes a `Person` object as an argument. When the `changeName` method is called, a copy of the reference to the person object is passed as an argument. However, the method is able to change the name of the original object because the object in the `main` method and the copy passed as an argument are pointing to the same memory location. Even though the method received a copy of the reference to the object, the original object is being modified.

When an object is passed as an argument to a method in Java, a new reference variable is created on the stack memory that points to the same object as the original reference variable. This allows the method to access and modify the object, but it does not create a new copy of the object. The method operates on the same object that is referenced by the original variable, so any changes made to the object inside the method will be reflected in the original object as well.

## Java's Approach to Passing Method Arguments: By Reference

In Java, we don't have pass by reference mechanism for method arguments. However, as we discussed earlier, in the case of objects, the copy that is passed is actually a reference to the memory location of the object, not a copy of the entire object. This means that any changes made to the object inside the method will be reflected in the original object, as they are both pointing to the same memory location.

## Conclusion

In this article, we have explored how method arguments are passed in Java, and the differences between passing by value and passing by reference. We have seen that in Java, all method arguments are passed by value, which means that a copy of the argument value is passed to the method. However, in the case of objects, the copy that is passed is actually a reference to the memory location of the object, not a copy of the entire object. This can lead to confusion, as it may not be immediately obvious that the original object is being modified. To avoid confusion, it is important to understand how method arguments are passed in Java and how it affects the way methods interact with their arguments. Understanding this concept will help you to write more efficient and optimized code.
