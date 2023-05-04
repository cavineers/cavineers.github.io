# Methods

Methods are an essential concept in Java programming, especially for beginners who are just starting to learn the language. In this article, we will explore the basics of methods in Java, their syntax, and their usage.

## Syntax of a Method

A method in Java consists of a method header and a method body. The method header contains the method's access specifier, return type, method name, and parameter list. The method body contains the code that the method executes when it is called.

Here's an example of a method header:

```java
public int add(int num1, int num2)
```

In this example, we have defined a method called `add` that takes two integer parameters, `num1` and `num2`, and returns an integer. The access specifier `public` means that the method can be accessed from any class, and the return type `int` specifies that the method returns an integer value.

Here's an example of a method body:

```java
{
    return num1 + num2;
}
```

In this example, we have defined the code that the `add` method executes when it is called. The method adds the two integer parameters, `num1` and `num2`, and returns the result.

## Usage of Methods

Methods are used to define the behavior of a class. They provide a way to encapsulate functionality and reuse code. In Java, there are two types of methods: instance methods and static methods.

### Instance Methods

Instance methods are methods that are associated with an instance of a class. These methods are the primary methods you will use when programming the bot and can access and modify the instance variables of the class. Here's an example of an instance method in the `Person` class:

```java
public void sayHello() {
    System.out.println("Hello, my name is " + name + " and I am " + age + " years old.");
}
```

In this example, we have defined an instance method called `sayHello()`. The method uses the `name` and `age` instance variables to print a message to the console.

To call an instance method, you need to create an instance of the class and then call the method on that instance. Here's an example:

```java
Person john = new Person("John", 25);
john.sayHello();
```

In this example, we create a new `Person` object called `john` with the name "John" and age 25. We then call the `sayHello()` method on the `john` object, which prints the message "Hello, my name is John and I am 25 years old." to the console.

Create your own person class using this file as a reference and try it!

!!! tip 

    Use your `Main` class to instantiate your Person class and call the method.