## Variables and Data Types

Variables are used to store values in Java. Here's how you can declare and initialize a variable:

```java
int myNumber = 42;
double myLongNumber = 3.1415926535; //15-16 digits of precision
boolean myBoolean = true;
```

In this example, `myNumber` is a variable of type `int` that is initialized with the value `42`. Java has several different data types, including:

- `int`: used for storing integers (whole numbers).
- `double`: used for storing floating-point numbers (numbers with decimal points).
- `boolean`: used for storing `true` or `false` values.

You can also declare variables without initializing them:

```java
int myNumber;
double myLongNumber;
boolean myBoolean;
```

Many programmers prefer to initialize variables when they are declared, but it is not required. This method of initializing variables designates space in memory for the variable, but does not assign a value to it. This is useful when you want to declare a variable, but don't know what value it will have yet.