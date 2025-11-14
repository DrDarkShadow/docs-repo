## ClassDef Main
# Class: Main

## Overview

The `Main` class serves as a container for several static utility methods and acts as the primary entry point for the Java application.

## attributes

This class does not have any attributes. It contains static methods that operate on the parameters passed to them.

## Description

The `Main` class provides a collection of independent, static methods designed for common tasks. As all methods are static, there is no need to instantiate the `Main` class to use them.

The class includes the following methods:

-   `public static int add(int a, int b)`: This function takes two integer arguments, `a` and `b`, and returns their sum. It performs a simple addition operation.

-   `public static int factorial(int n)`: This function calculates the factorial of a given non-negative integer `n` using a recursive approach.
    -   The base case for the recursion is when `n` is less than or equal to 1, in which case the function returns `1`.
    -   For any `n` greater than 1, it recursively calls itself with `n - 1` and multiplies the result by `n`.

-   `public static void greet(String name)`: This function takes a `String` argument `name` and prints a formatted greeting message to the console. It does not return any value (`void`).

-   `public static void main(String[] args)`: This is the main entry point of the application. The Java Virtual Machine (JVM) calls this method to start the program. The implementation within this class demonstrates the usage of the `add`, `factorial`, and `greet` methods and prints their results to the standard output.

```java
// Example of calling the static methods
int sum = Main.add(5, 10);
int fact = Main.factorial(5);
Main.greet("Prateek");
```

## Usage Notes

-   All methods in this class are `static`, meaning they should be called directly on the class itself (e.g., `Main.add(5, 10)`) rather than on an instance of the class.
-   The `factorial` method is recursive and may lead to a `StackOverflowError` if called with a very large integer value.
-   The `main` method is the standard entry point for any Java application and is used here to demonstrate the functionality of the other methods.

## Example

The `main` method within the class provides a clear example of how to use the other static methods.

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
### FunctionDef add(a, b)
# Function: add(int a, int b)

## Overview

The `add` function calculates and returns the sum of two integer values.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | `int` | The first integer to be added. |
| `b` | `int` | The second integer to be added. |

## Description

This `public static` method provides a straightforward way to perform integer addition. Being `static`, it can be called directly on the `Main` class without needing to create an instance of it. The function takes two integer parameters, `a` and `b`. Internally, it uses the `+` operator to compute their sum. The resulting integer value is then returned to the caller.

The core logic is expressed in a single statement:
```java
return a + b;
```

## Usage Notes

- This function is designed specifically for `int` data types. Passing other numeric types (like `double` or `long`) will result in a compilation error unless they are explicitly cast to `int`.
- Be mindful of integer overflow. If the sum of `a` and `b` exceeds the maximum value of an `int` (`Integer.MAX_VALUE`, which is 2,147,483,647), the result will wrap around to a negative number.
- As a `static` method, it should be invoked using the class name, e.g., `Main.add(5, 3)`.

**Output Example**: An integer representing the sum.

## Example

```java
// Example usage
int result = Main.add(5, 3);
System.out.println(result);
```

**Output:**

```
8
```

***
***
### FunctionDef factorial(n)
# Function: factorial

## Overview

The `factorial` function recursively calculates the factorial of a given non-negative integer.

## parameters

- `n`: The non-negative integer for which the factorial is to be calculated.

## Description

This function implements the mathematical factorial operation using recursion. The logic is divided into two main parts:

1.  **Base Case**: The recursion terminates when the input `n` is less than or equal to 1. According to the definition of factorials, the factorial of 0 (`0!`) and 1 (`1!`) is 1. The function returns `1` in this case, preventing infinite recursion.

2.  **Recursive Step**: If `n` is greater than 1, the function calculates the factorial by multiplying `n` with the result of calling itself with the argument `n - 1`. This process continues until the base case is reached.

For example, `factorial(4)` is computed as follows:
`4 * factorial(3)`
`4 * (3 * factorial(2))`
`4 * (3 * (2 * factorial(1)))`
`4 * (3 * (2 * 1))` which evaluates to `24`.

## Usage Notes

-   **Input Domain**: This function is intended for non-negative integers. Providing a negative number will cause infinite recursion, leading to a `StackOverflowError`.
-   **Integer Overflow**: The factorial value grows very rapidly. The `int` data type in Java has a limited range. For values of `n` greater than 12, the result will exceed the maximum value for a standard 32-bit integer, causing an overflow and producing an incorrect result. For larger numbers, consider using a data type with a larger range, such as `long` or `java.math.BigInteger`.

**Output Example**: A single integer representing the calculated factorial.
`120`

## Example

```java
// Example usage within a main method
public class Main {
    public static int factorial(int n) {
        if (n <= 1)
            return 1;
        else
            return n * factorial(n - 1);
    }

    public static void main(String[] args) {
        int number = 5;
        int result = factorial(number);
        System.out.println("The factorial of " + number + " is: " + result);
    }
}
```

**Output:**

```
The factorial of 5 is: 120
```

***
***
### FunctionDef greet(name)
# Function: greet(String name)

## Overview

The `greet` function prints a personalized greeting message to the standard console output.

## parameters

- `name` (String): The name to be included in the greeting message.

## Description

This `static` function provides a simple way to display a standardized greeting. It takes a single `String` parameter, `name`. The function's logic concatenates the literal string `"Hello, "`, the value of the `name` parameter, and the literal string `"!"`. The resulting string is then printed to the console using `System.out.println()`, which also appends a newline character at the end.

Because the function is declared as `void`, it does not return any value. Its entire effect is the side effect of printing text to the output stream.

```java
// The function concatenates "Hello, ", the name, and "!"
System.out.println("Hello, " + name + "!");
```

## Usage Notes

- This is a `static` method and should be called on the `Main` class directly, such as `Main.greet("Alice")`.
- The function does not return a value; its purpose is solely to print output to the console.
- The `name` parameter can be any string, including an empty one. If an empty string is passed, the output will be "Hello, !".

## Example

```java
public class Main {
    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public static void main(String[] args) {
        // Example usage
        greet("World");
    }
}
```

**Output:**

```
Hello, World!
```

***
***
### FunctionDef main(args)
# Function: main(String[] args)

## Overview

The `main` function serves as the entry point for the Java application, demonstrating the functionality of the `add`, `factorial`, and `greet` methods by calling them with predefined values.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `args` | `String[]` | An array of strings that contains command-line arguments passed to the program. This parameter is not utilized in the current implementation. |

## Description

The `main` method is the standard starting point for the execution of a Java program. When the application is run, the Java Virtual Machine (JVM) invokes this method.

The execution flow is as follows:
1.  The method first calls the `add(5, 10)` function to compute the sum of `5` and `10`. The result is concatenated with the string `"Sum: "` and printed to the standard console output.
2.  Next, it calls the `factorial(5)` function to calculate the factorial of `5`. The result is then concatenated with the string `"Factorial: "` and printed to the console.
3.  Finally, it calls the `greet("Prateek")` method, passing the string `"Prateek"` as an argument to display a greeting message.

This method effectively acts as a driver to showcase the core functionalities implemented in other methods of the class.

## Usage Notes

- The `main` method is the designated starting point for any Java application.
- It is automatically invoked by the Java Virtual Machine (JVM) when the program starts.
- The method signature must be `public static void main(String[] args)` to be recognized by the JVM as the program's entry point.

## Example

The `main` method is not called directly by user code but is executed by the JVM when running the compiled Java class. To run this program from the command line, you would execute:

```java
// Assuming the file is compiled into Main.class
// Command to run the program:
// java Main
```

**Output:**

```
Sum: 15
Factorial: 120
// The output of the greet method will also be printed, for example: Hello, Prateek!
```

***
***
