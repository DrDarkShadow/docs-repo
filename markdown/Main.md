## ClassDef Main
# Class: Main

## Overview

The `Main` class is a utility class that contains static methods for performing basic mathematical operations and printing messages, and it includes the main entry point for the Java application.

## Description

The `Main` class serves as a container for several independent, static methods, meaning they can be called directly on the class without needing to create an instance of it. It also contains the `main` method, which is the standard entry point for execution of a Java program.

The class provides the following functionalities:

-   **`add(int a, int b)`**: A simple function that takes two integer parameters, `a` and `b`, and returns their sum.

-   **`factorial(int n)`**: This function calculates the factorial of a non-negative integer `n` using recursion.
    -   The base case for the recursion is when `n` is less than or equal to 1, in which case the function returns `1`.
    -   For any `n` greater than 1, it recursively calls itself with `n - 1` and multiplies the result by `n`.

-   **`greet(String name)`**: A `void` function that takes a `String` parameter `name` and prints a formatted greeting message to the console. It does not return any value.

-   **`main(String[] args)`**: The primary execution method for the program. It demonstrates the usage of the `add`, `factorial`, and `greet` methods and prints their results to the standard output.

```java
// Example of the factorial logic
factorial(5)
// returns 5 * factorial(4)
// returns 5 * 4 * factorial(3)
// returns 5 * 4 * 3 * factorial(2)
// returns 5 * 4 * 3 * 2 * factorial(1)
// returns 5 * 4 * 3 * 2 * 1 = 120
```

## Usage Notes

-   All methods in this class are `static`, so they should be invoked directly on the `Main` class (e.g., `Main.add(5, 10)`).
-   The `factorial` method is recursive. Providing a very large integer may lead to a `StackOverflowError`.
-   The `main` method serves as a built-in example of how to use the other methods in the class.

## Example

The following code demonstrates how to call the methods within the `Main` class. This is the content of the `main` method itself.

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
