---
layout: post
permalink: java-is-pass-by-value
title: Java is pass by value
metadescription: ""
---

In programming, one of the key concepts to understand is how method arguments are passed. Depending on the programming language and the way the method is defined, arguments can be passed by value or by reference. In this article, we will explore how method arguments are passed in Java, one of the most widely used programming language. We will take a look at the differences between passing by value and passing by reference and show you how this affects the way methods can interact with their arguments. This article will help you to understand this concept in a better way which will help you to write more efficient and optimized code.

## Java: Passing by value

Java is a programming language that uses the concept of passing by value for all its method arguments. This means that when a method is called, a copy of the argument value is passed to the method, rather than a reference to the original memory location of the argument. This applies to both primitive data types, such as integers and booleans, as well as objects.

For example, let's consider the following class `Person` and the method `changeName`:

```java
class Person {
    private String name;
    
    public Person(String name) {
        this.name = name;
    }
    public String setName(String name) {
        return this.name = name;
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
        System.out.println(p.getName());
    }
}
```

When the `changeName` method is called, a copy of the `person` object is passed as an argument. However, the method is able to change the name of the original object because the object in the main method and the copy passed as an argument are pointing to the same memory location. Even though the method received a copy of the object, the original object is being modified.

In summary, in Java, all method arguments are passed by value, which means that a copy of the argument value is passed to the method, rather than a reference to the original memory location of the argument. This applies to both primitive data types and objects.
