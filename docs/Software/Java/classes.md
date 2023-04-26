# Classes

Classes are the building blocks of object-oriented programming (OOP) in Java. A class is a blueprint for creating objects, which are instances of the class. In this guide, we will cover the basics of Java classes.

## Creating a Class

To create a class in Java, you use the `class` keyword followed by the name of the class. Here's an example:

```java
public class Person {
    String name;
    int age;
}
```

In this example, we have created a class called `Person`. The class has two instance variables: `name` and `age`.

## Instance Variables

Instance variables are variables that belong to each instance of a class. Each instance has its own copy of the instance variables. Here's an example:

```java
Person person1 = new Person();
person1.name = "John";
person1.age = 25;

Person person2 = new Person();
person2.name = "Jane";
person2.age = 30;
```

In this example, we have created two instances of the `Person` class: `person1` and `person2`. We have set the `name` and `age` instance variables for each instance.

## Constructors

Constructors are used to create instances of a class. Here's an example of a constructor in the `Person` class:

```java
public Person(String name, int age) {
    this.name = name;
    this.age = age;
}
```

In this example, we have defined a constructor that takes two parameters: `name` and `age`. The constructor initializes the `name` and `age` instance variables using the `this` keyword.

## Using Constructors

Here's an example of how to use the `Person` constructor:

```java
Person person1 = new Person("John", 25);
Person person2 = new Person("Jane", 30);
```

In this example, we have used the `Person` constructor to create two instances of the `Person` class: `person1` and `person2`. We have passed in values for the `name` and `age` parameters.
