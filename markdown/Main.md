## ClassDef Main
# Class: Main

## Overview

The `Main` class serves as the primary entry point for the application and provides a collection of static utility methods for basic mathematical operations and console output.

## attributes

This class does not have any attributes. It contains static methods that operate on the parameters passed to them.

## Description

The `Main` class is a container for several static methods, meaning they can be called directly on the class without needing to create an object instance. It also contains the `main` method, which is the standard entry point for a Java application.

The class includes the following utility methods:

-   `add(int a, int b)`: A simple function that accepts two integer parameters, `a` and `b`, and returns their sum.
-   `factorial(int n)`: A recursive function that calculates the factorial of a non-negative integer `n`. The base case is when `n` is less than or equal to 1, where it returns 1. Otherwise, it recursively calls itself with `n - 1` and multiplies the result by `n`.
-   `greet(String name)`: A `void` function that takes a `String` parameter `name` and prints a personalized greeting message to the standard output console.

The `main(String[] args)` method demonstrates the usage of these utility functions by calling them with sample values and printing the results to the console.

```java
// Example of the factorial logic
// factorial(5)
// 5 * factorial(4)
// 5 * 4 * factorial(3)
// 5 * 4 * 3 * factorial(2)
// 5 * 4 * 3 * 2 * factorial(1)
// 5 * 4 * 3 * 2 * 1 = 120
```

## Usage Notes

-   All helper methods (`add`, `factorial`, `greet`) are `static` and should be invoked directly on the `Main` class (e.g., `Main.add(5, 10)`).
-   The `factorial` method is recursive. Providing a very large integer as input may lead to a `StackOverflowError`.
-   The `greet` method prints its output directly to `System.out` and does not return any value.

## Example

The provided `main` method serves as a clear example of how to use the class's functions.

```java
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
