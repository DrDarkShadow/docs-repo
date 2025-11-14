## ClassDef Main
# Class: Main

## Overview

The `Main` class serves as a container for several static utility methods and includes the primary entry point for the Java application.

## Description

The `Main` class provides a collection of standalone, static functions for performing basic mathematical operations and printing messages. As a container for static methods, it does not need to be instantiated. The class also contains the `main` method, which is the standard entry point for any Java program.

The class includes the following methods:

- **`add(int a, int b)`**: A simple function that takes two integer arguments, `a` and `b`, and returns their sum.

- **`factorial(int n)`**: A recursive function that calculates the factorial of a given integer `n`.
    - The base case is when `n` is less than or equal to 1, where the function returns `1`.
    - For any `n` greater than 1, it multiplies `n` by the result of `factorial(n - 1)`.

- **`greet(String name)`**: A `void` function that prints a formatted greeting message to the console. It takes a `String` `name` and outputs "Hello, [name]!".

- **`main(String[] args)`**: The main entry point of the application. This method demonstrates the usage of the other three static methods by calling them with predefined values and printing their results to the standard output.

## Usage Notes

- All methods in this class are `static`, meaning they should be called directly on the class itself (e.g., `Main.add(5, 3)`) rather than on an instance of the class.
- The `factorial` method is implemented recursively. Using a very large input value for `n` can lead to a `StackOverflowError`.
- The `main` method is the designated starting point for the Java Virtual Machine (JVM) when the program is executed.

## Example

The `main` method within the class provides a clear example of how to use the utility functions.

```java
public static void main(String[] args) {
    // Calling the add function
    System.out.println("Sum: " + add(5, 10));

    // Calling the factorial function
    System.out.println("Factorial: " + factorial(5));

    // Calling the greet function
    greet("Prateek");
}
```

**Output:**

When the `main` method is executed, the following output is printed to the console:

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
| `a` | `int` | The first integer operand. |
| `b` | `int` | The second integer operand. |

## Description

This `static` function provides a straightforward way to perform integer addition. It accepts two integer parameters, `a` and `b`. The core logic of the function is executed in a single statement, `return a + b;`, which uses the standard arithmetic addition operator (`+`) to compute the sum of the two inputs. The resulting `int` value is then returned to the caller.

Because the method is `static`, it belongs to the `Main` class itself and can be invoked directly without needing to create an instance of the class.

```java
// The function simply returns the sum of its two integer parameters.
return a + b;
```

## Usage Notes

- As a `static` method, it should be called directly on the class, e.g., `Main.add(5, 10)`.
- The function is designed specifically for `int` types. Providing arguments of other data types will result in a compile-time error.
- Be mindful of integer overflow. If the sum of `a` and `b` exceeds the maximum value of an `int` (`Integer.MAX_VALUE`) or is less than the minimum value (`Integer.MIN_VALUE`), the result will wrap around without throwing an exception.

**Output Example**: The function returns a single `int` value representing the sum. For an input of `(5, 10)`, the output would be `15`.

## Example

The following code demonstrates how to call the `add` function and print the result.

```java
public class Demo {
    public static void main(String[] args) {
        // Define two integers
        int number1 = 7;
        int number2 = 8;

        // Call the static add method from the Main class
        int result = Main.add(number1, number2);

        // Print the result
        System.out.println("The sum of " + number1 + " and " + number2 + " is: " + result);
    }
}

// Assuming Main class is accessible
class Main {
    public static int add(int a, int b) {
        return a + b;
    }
}
```

**Output:**

```
The sum of 7 and 8 is: 15
```

***
***
### FunctionDef factorial(n)
# Function: factorial(int n)

## Overview

The `factorial` function recursively calculates the factorial of a given non-negative integer.

## parameters

- `n` (int): The non-negative integer for which the factorial will be computed.

## Description

This function implements the mathematical factorial operation, which is the product of all positive integers up to a given number `n` (denoted as `n!`). The implementation uses recursion.

The logic follows two main paths:
1.  **Base Case**: The recursion terminates when the input `n` is less than or equal to `1`. In this case, the function returns `1`, as the factorial of 1 (`1!`) and 0 (`0!`) is defined as 1.
2.  **Recursive Step**: If `n` is greater than `1`, the function multiplies `n` by the result of calling itself with the argument `n - 1`. This process continues until the base case is reached.

For example, a call to `factorial(4)` unfolds as follows:
- `factorial(4)` returns `4 * factorial(3)`
- `factorial(3)` returns `3 * factorial(2)`
- `factorial(2)` returns `2 * factorial(1)`
- `factorial(1)` returns `1` (base case)

The final result is calculated by multiplying back up the call stack: `4 * 3 * 2 * 1 = 24`.

## Usage Notes

- The function is designed for non-negative integers. Providing a negative number will cause infinite recursion, leading to a `StackOverflowError`.
- The return type is `int`. Factorials grow very rapidly. Inputs greater than `12` will cause an integer overflow, resulting in an incorrect value, as `13!` exceeds the maximum value for a standard 32-bit signed integer.
- This is a `static` method, so it should be called on the class itself (e.g., `Main.factorial(5)`), not on an instance of the class.

**Output Example**: A single integer representing the calculated factorial.
`120`

## Example

```java
// Example usage within the Main class or another static context
public static void main(String[] args) {
    int number = 5;
    int result = Main.factorial(number);
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

- `name` (String): The name of the person or entity to be included in the greeting message.

## Description

This `public static` method provides a simple way to display a greeting. It takes a single `String` argument named `name`. The function constructs a new string by concatenating the literal `"Hello, "`, the value of the `name` parameter, and the literal `"!"`. This complete greeting string is then passed to `System.out.println()`, which prints it to the console, followed by a new line.

```java
System.out.println("Hello, " + name + "!");
```

Because the method is `static`, it can be called directly on the `Main` class without needing to create an instance of it.

## Usage Notes

- As a `static` method, it should be called directly on the class, for example, `Main.greet("World")`.
- This method has a `void` return type, meaning it does not return any value. Its only effect is printing to the console.
- The input `name` can be any valid string. If an empty string is passed, it will print "Hello, !".

## Example

```java
public class Main {
    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public static void main(String[] args) {
        // Example usage
        greet("Alice");
        greet("World");
    }
}
```

**Output:**

```
Hello, Alice!
Hello, World!
```

***
***
### FunctionDef main(args)
# Function: main

## Overview

The `main` function serves as the primary entry point for the Java application, executing a sequence of calls to demonstrate other utility methods.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `args` | `String[]` | An array of strings containing command-line arguments passed to the program upon execution. This parameter is not utilized in the current implementation. |

## Description

The `main` method is a special, required method in Java that the Java Virtual Machine (JVM) calls to start the execution of a program. It acts as the orchestrator for the application's initial operations.

The execution flow is as follows:
1.  It first calls the `add(5, 10)` method. The return value of this method is concatenated with the string `"Sum: "` and printed to the standard output console.
2.  Next, it calls the `factorial(5)` method. Similarly, its return value is concatenated with the string `"Factorial: "` and printed to the console.
3.  Finally, it calls the `greet("Prateek")` method, passing the string `"Prateek"` as an argument. This method is expected to perform an action, such as printing a greeting.

This method effectively serves as a simple test driver to showcase the functionality of the `add`, `factorial`, and `greet` methods.

## Usage Notes

- The `public static void main(String[] args)` signature is the mandatory entry point for any standalone Java application.
- The `args` parameter allows for passing configuration or data from the command line, which can be accessed within the program.
- This method's successful compilation and execution depend on the presence and accessibility of the `add`, `factorial`, and `greet` methods within the same scope.

## Example

The `main` method is executed by running the compiled Java class from the command line.

```java
// 1. Compile the source file (e.g., Main.java)
// javac Main.java

// 2. Run the compiled class
// java Main
```

**Output:**

Assuming standard implementations where `add(5, 10)` returns `15`, `factorial(5)` returns `120`, and `greet("Prateek")` prints a greeting to the console, the output would be:

```
Sum: 15
Factorial: 120
[Output from the greet method, e.g., "Hello, Prateek!"]
```

***
***
