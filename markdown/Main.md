## ClassDef Main
# Class: Main

## Overview

The `Main` class serves as the primary entry point for the Java application and contains a collection of static utility methods for performing basic calculations and printing messages.

## attributes

This class does not have any attributes. It only contains static methods.

## Description

The `Main` class is a container for several independent, static methods and the `main` method, which orchestrates the execution of the program.

**Methods:**

- `public static int add(int a, int b)`: This function takes two integer arguments, `a` and `b`, and returns their sum. It performs a simple addition operation.

- `public static int factorial(int n)`: This function calculates the factorial of a non-negative integer `n` using recursion.
    - The base case for the recursion is when `n` is less than or equal to 1, in which case the function returns `1`.
    - For any `n` greater than 1, it recursively calls itself with `n - 1` and multiplies the result by `n`.

- `public static void greet(String name)`: This function takes a `String` argument `name` and prints a personalized greeting message to the standard output. It does not return any value (`void`).

- `public static void main(String[] args)`: This is the main entry point of the application. When the program is run, the Java Virtual Machine (JVM) calls this method. It demonstrates the usage of the other utility methods (`add`, `factorial`, and `greet`) by calling them with sample values and printing the results to the console.

The overall structure is common for simple command-line applications where functionality is grouped logically within a single class.

## Usage Notes

- All methods in this class are `static`, meaning they belong to the class itself and can be called directly using the class name (e.g., `Main.add(5, 10)`) without needing to create an instance of the `Main` class.
- The `factorial` method is recursive. Providing a very large integer as input may result in a `StackOverflowError` due to excessive recursion depth.
- The `greet` method prints directly to the console and has a `void` return type, so it cannot be used in an expression to assign a value.

**Output Example**: The `main` method demonstrates the typical output when the program is executed.

## Example

The following code is from the `main` method and demonstrates how to use the functions within the `Main` class.

```java
public static void main(String[] args) {
    System.out.println("Sum: " + add(5, 10));
    System.out.println("Factorial: " + factorial(5));
    greet("Prateek");
}
```

**Output:**

When the program is compiled and run, the console will display the following output:

```
Sum: 15
Factorial: 120
Hello, Prateek!
```

***
### FunctionDef add(a, b)
# Function: add(int a, int b)

## Overview

The `add` function calculates the sum of two integer values.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | `int` | The first integer operand. |
| `b` | `int` | The second integer operand. |

## Description

This `static` function provides a straightforward implementation of integer addition. It accepts two integer arguments, `a` and `b`. The core logic uses the standard arithmetic addition operator (`+`) to compute the sum of these two numbers. The function then returns the resulting integer value.

```java
// The function returns the result of a + b
return a + b;
```

## Usage Notes

- As a `static` method, it should be called on the class itself, not on an instance of the class (e.g., `Main.add(5, 10)`).
- Users should be aware of potential integer overflow. If the sum of `a` and `b` exceeds the maximum value of an `int` (`Integer.MAX_VALUE`) or is less than the minimum value (`Integer.MIN_VALUE`), the result will wrap around according to Java's two's complement arithmetic.

**Output Example**: The function returns a single `int` value representing the sum. For an input of `(5, 3)`, the output would be `8`.

## Example

```java
// Example usage
public class Main {
    public static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        int result = Main.add(25, 17);
        System.out.println("The result is: " + result);
    }
}
```

**Output:**

```
The result is: 42
```

***
***
### FunctionDef factorial(n)
# Function: factorial(int n)

## Overview

The `factorial` function recursively calculates the factorial of a given non-negative integer.

## parameters

- **`n`** (int): The non-negative integer for which the factorial will be computed.

## Description

This function implements the factorial calculation using a recursive approach. The logic is divided into two main parts:

1.  **Base Case**: The recursion terminates when the input `n` is less than or equal to `1`. In mathematics, the factorial of 0 (`0!`) and 1 (`1!`) are both defined as `1`. The function handles this by returning `1` directly, which prevents an infinite loop.

2.  **Recursive Step**: If `n` is greater than `1`, the function multiplies `n` by the result of calling itself with the argument `n - 1`. This process continues, breaking down the problem into smaller subproblems until the base case is reached.

For example, calculating `factorial(4)` unfolds as follows:
- `factorial(4)` returns `4 * factorial(3)`
- `factorial(3)` returns `3 * factorial(2)`
- `factorial(2)` returns `2 * factorial(1)`
- `factorial(1)` returns `1` (base case)

The results are then multiplied back up the call stack: `4 * (3 * (2 * 1)) = 24`.

## Usage Notes

- The function is intended for non-negative integers. Providing a negative number will lead to infinite recursion, resulting in a `StackOverflowError`.
- The return type is `int`. Factorial values grow very quickly. The maximum value for a standard 32-bit signed integer in Java is `2,147,483,647`. The largest factorial that can be stored in an `int` is `12!`. Any input `n > 12` will cause an integer overflow, leading to an incorrect result.
- The function correctly handles `factorial(0)` and `factorial(1)`, both of which return `1`.

**Output Example**: The function returns a single integer value representing the calculated factorial.

## Example

```java
// Example usage within the Main class
public static void main(String[] args) {
    int number = 5;
    int result = factorial(number);
    System.out.println("The factorial of " + number + " is: " + result);
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

- `name`: (String) The name to be included in the greeting message.

## Description

This `public static` method provides a simple way to display a greeting. It is accessible from anywhere in the project and can be called directly on the `Main` class without needing to create an instance of it.

The function takes a single `String` parameter, `name`. It then constructs a new string by concatenating the literal string `"Hello, "`, the value of the `name` parameter, and the literal string `"!"`. Finally, it uses the `System.out.println()` method to print the resulting string to the console, automatically appending a newline character at the end. Because its return type is `void`, the function does not return any value.

## Usage Notes

- This function prints directly to the console and does not return the greeting string. If you need to manipulate the string itself, the function would need to be modified to return a `String` instead of being `void`.
- The method is `static`, so it should be called using the class name: `Main.greet("your_name");`.
- Passing `null` as the `name` argument will not cause an error but will result in the output "Hello, null!".

## Example

```java
public class Application {
    public static void main(String[] args) {
        // Example usage of the greet function
        Main.greet("World");
        Main.greet("Alice");
    }
}

// Assuming Main.java contains the greet method
class Main {
    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }
}
```

**Output:**

```
Hello, World!
Hello, Alice!
```

***
***
### FunctionDef main(args)
# Function: main(String[] args)

## Overview

The `main` function serves as the primary entry point for the Java application, executing a series of predefined method calls to demonstrate their functionality.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `args` | `String[]` | An array of strings that holds command-line arguments passed to the application at runtime. This parameter is not utilized in the current implementation. |

## Description

As the standard entry point for a Java program, the `main` function is executed automatically when the application starts. Its logic proceeds in three distinct steps:

1.  It first calls the `add(5, 10)` method to calculate the sum of two integers. The result is then concatenated with the string `"Sum: "` and printed to the standard output console.
2.  Next, it calls the `factorial(5)` method to compute the factorial of the number 5. The returned value is concatenated with the string `"Factorial: "` and also printed to the console.
3.  Finally, it calls the `greet("Prateek")` method, passing a string literal as an argument. This method is expected to perform an action, such as printing a greeting, but it does not return a value to the `main` function.

This function demonstrates a simple, sequential execution flow and showcases how other methods within the class can be called and their results displayed.

## Usage Notes

- This method signature (`public static void main(String[] args)`) is the mandatory entry point for any executable Java class.
- The `args` parameter allows for passing configuration or data to the program from the command line, although it is not used in this specific code.
- The primary purpose of this `main` function is to demonstrate the functionality of the `add`, `factorial`, and `greet` methods.

## Example

To run this `main` function, you would compile and execute the `Main.java` file from the command line.

```java
// 1. Compile the code
javac Main.java

// 2. Run the compiled code
java Main
```

**Output:**

Assuming the `add`, `factorial`, and `greet` methods are implemented as expected, the console output will be:

```
Sum: 15
Factorial: 120
Hello, Prateek!
```

***
***
