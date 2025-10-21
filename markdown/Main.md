## ClassDef Main
# Class: Main

## Overview

The `Main` class serves as the entry point for the application and provides a collection of static utility methods for basic mathematical calculations and console output.

## attributes

This class does not have any attributes or fields. It contains static methods that operate on the parameters passed to them.

## Description

The `Main` class is a container for several independent, `static` methods. As the methods are static, they can be called directly on the class without needing to create an instance of `Main`. The class demonstrates basic Java functionalities including arithmetic operations, recursion, and console I/O.

The class includes the following methods:

- `add(int a, int b)`: A simple function that accepts two integer arguments, `a` and `b`, and returns their sum.
- `factorial(int n)`: A recursive function that calculates the factorial of a non-negative integer `n`. It uses a base case where if `n` is less than or equal to 1, it returns 1. Otherwise, it recursively calls itself with `n - 1` and multiplies the result by `n`.
- `greet(String name)`: A `void` function that takes a `String` argument `name` and prints a personalized greeting message to the standard output.
- `main(String[] args)`: The primary entry point for the Java application. When the program is executed, this method is called. It demonstrates the usage of the `add`, `factorial`, and `greet` methods and prints their results to the console.

The `main` method orchestrates the execution flow by calling the other utility methods with sample data:

```java
public static void main(String[] args) {
    // Calls the add method with 5 and 10
    System.out.println("Sum: " + add(5, 10));
    // Calls the factorial method with 5
    System.out.println("Factorial: " + factorial(5));
    // Calls the greet method with "Prateek"
    greet("Prateek");
}
```

## Usage Notes

- All utility methods (`add`, `factorial`, `greet`) are `static` and should be invoked directly on the class, e.g., `Main.add(5, 10)`.
- The `factorial` method is implemented recursively. Providing a very large integer as input may lead to a `StackOverflowError` due to deep recursion.
- The `main` method is the designated starting point for execution by the Java Virtual Machine (JVM) and is where the program begins.

## Example

The `main` method within the class itself provides a clear example of how to use the other methods. To run this example, you would compile and execute the `Main.java` file.

```java
// Example usage is demonstrated within the main method
public static void main(String[] args) {
    System.out.println("Sum: " + add(5, 10));
    System.out.println("Factorial: " + factorial(5));
    greet("Prateek");
}
```

**Output:**

```
Sum: 15
Factorial: 120
Hello, Prateek!
```

***
