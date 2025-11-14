## ClassDef Main
# Class: Main

## Overview

The `Main` class serves as the entry point for the application and provides a collection of static utility methods for basic mathematical operations and console output.

## attributes

This class does not have any attributes.

## Description

The `Main` class is a container for static methods and the main execution point of the Java program. Since all methods are `static`, they can be invoked directly on the class without needing to create an instance of `Main`.

The class includes the following methods:

- **`add(int a, int b)`**: A static function that accepts two integer arguments, `a` and `b`. It performs an addition operation and returns the sum as an `int`.

- **`factorial(int n)`**: A static function that calculates the factorial of a given integer `n` using recursion.
    - The base case is `if (n <= 1)`, which returns `1`.
    - For any `n` greater than 1, it recursively calls `factorial(n - 1)` and multiplies the result by `n`.

- **`greet(String name)`**: A static void function that takes a `String` argument `name`. It prints a formatted greeting message, "Hello, [name]!", to the standard console output.

- **`main(String[] args)`**: The main entry point for the Java application. This method demonstrates the usage of the other three static methods by calling them with predefined values and printing their results to the console.

```java
// Inside the main method
System.out.println("Sum: " + add(5, 10));
System.out.println("Factorial: " + factorial(5));
greet("Prateek");
```

## Usage Notes

- All methods in this class are `static` and should be called directly on the class itself (e.g., `Main.add(5, 10)`).
- The `factorial` method uses recursion. Providing a very large number can lead to a `StackOverflowError`.
- The return type of `factorial` is `int`. For input values of `n` greater than 12, the result will exceed the maximum value for an `int`, leading to an integer overflow and an incorrect result.

## Example

The following code demonstrates how to run the `main` method, which in turn calls the other utility methods in the class.

```java
public class Main {

    // Function to add two numbers
    public static int add(int a, int b) {
        return a + b;
    }

    // Function to find factorial of a number
    public static int factorial(int n) {
        if (n <= 1)
            return 1;
        else
            return n * factorial(n - 1);
    }

    // Function to print a greeting message
    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public static void main(String[] args) {
        System.out.println("Sum: " + add(5, 10));
        System.out.println("Factorial: " + factorial(5));
        greet("Prateek");
    }
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

The `add` function computes the sum of two specified integer numbers.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | `int` | The first integer operand. |
| `b` | `int` | The second integer operand. |

## Description

This function provides a straightforward implementation of integer addition. It accepts two parameters, `a` and `b`, both of type `int`. The core logic of the function uses the standard arithmetic addition operator (`+`) to calculate the sum of these two values. The resulting integer sum is then returned to the caller.

```java
// The function returns the result of a + b
return a + b;
```

## Usage Notes

- This is a `static` method and should be called on the `Main` class directly, such as `Main.add(10, 5)`.
- Users should be aware of potential integer overflow. If the sum of `a` and `b` exceeds the maximum value of an `int` (`Integer.MAX_VALUE`) or is less than the minimum value (`Integer.MIN_VALUE`), the result will wrap around, which may lead to unexpected behavior.

**Output Example**: A single integer value representing the sum.

## Example

```java
public class Main {
    public static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        // Example usage
        int result = add(25, 17);
        System.out.println(result);
    }
}
```

**Output:**

```
42
```

***
***
### FunctionDef factorial(n)
# Function: factorial(int n)

## Overview

The `factorial` function recursively calculates the factorial of a given non-negative integer.

## parameters

- **`n`** (`int`): The non-negative integer for which to calculate the factorial.

## Description

This function implements the factorial operation using recursion. The factorial of a non-negative integer `n`, denoted by `n!`, is the product of all positive integers less than or equal to `n`.

The logic follows two main paths:
1.  **Base Case**: If the input `n` is less than or equal to 1, the function returns `1`. This is the termination condition for the recursion, as the factorial of 1 (`1!`) and 0 (`0!`) is defined as 1.
2.  **Recursive Step**: If `n` is greater than 1, the function calls itself with the argument `n - 1` and multiplies the result by `n`.

For example, calculating `factorial(4)` unfolds as follows:
- `factorial(4)` returns `4 * factorial(3)`
- `factorial(3)` returns `3 * factorial(2)`
- `factorial(2)` returns `2 * factorial(1)`
- `factorial(1)` hits the base case and returns `1`

The results are then multiplied back up the call stack: `4 * (3 * (2 * 1))`, which evaluates to `24`.

## Usage Notes

- The function is designed for non-negative integers. Providing a negative number will cause infinite recursion, which will result in a `StackOverflowError`.
- The return type is `int`. Factorial values grow very quickly. For inputs `n > 12`, the result will exceed the maximum value of a standard 32-bit integer (`2,147,483,647`), causing an integer overflow and yielding an incorrect result.

**Output Example**: A single integer representing the calculated factorial.
`120`

## Example

```java
// Example of calling the static method from the Main class
int number = 5;
int result = Main.factorial(number);
System.out.println("The factorial of " + number + " is: " + result);
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

The `greet` function prints a personalized greeting message to the standard console.

## parameters

- `name` (String): The name of the person or entity to be included in the greeting message.

## Description

This `public static` method provides a simple way to display a greeting. It takes a single `String` parameter, `name`. The core logic of the function involves string concatenation. It combines the literal string `"Hello, "`, the value passed in the `name` parameter, and a literal exclamation mark `"!"` to form a complete sentence.

Finally, this constructed string is printed to the standard output stream using `System.out.println()`, which also appends a newline character at the end. As a `void` method, it does not return any value.

## Usage Notes

- This is a `static` method, so it should be called directly on the `Main` class, like `Main.greet("World");`.
- The output is always directed to the system console.
- The function will execute with any string value for `name`, including an empty string. For example, `greet("")` would print "Hello, !".

## Example

```java
public class Main {
    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public static void main(String[] args) {
        // Example usage of the greet function
        greet("Alice");
        greet("Developer");
    }
}
```

**Output:**

```
Hello, Alice!
Hello, Developer!
```

***
***
### FunctionDef main(args)
# Function: main(String[] args)

## Overview

The `main` function serves as the primary entry point for the Java application, executing a series of predefined method calls to demonstrate the program's functionality.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `args` | `String[]` | An array of `String` objects that can hold command-line arguments passed to the application at runtime. In this specific implementation, the `args` parameter is not utilized. |

## Description

The `main` method is the starting point of execution for the Java program. When the application is run, the Java Virtual Machine (JVM) calls this method.

The execution proceeds as follows:
1.  The method first calls the `add(5, 10)` function. The return value of this function is concatenated with the string `"Sum: "` and the entire string is printed to the standard output console.
2.  Next, it calls the `factorial(5)` function. The integer result is concatenated with the string `"Factorial: "` and printed to the console.
3.  Finally, the `greet("Prateek")` method is called with the string `"Prateek"` as an argument. This method is expected to perform an action, such as printing a greeting to the console.

The `main` method has a `void` return type, meaning it does not return any value upon completion.

## Usage Notes

- The `public static void main(String[] args)` signature is the standard entry point for Java applications and is invoked automatically by the JVM.
- This method's functionality is dependent on the `add`, `factorial`, and `greet` methods being defined and accessible within the same scope.
- Although the `args` parameter is defined to accept command-line arguments, they are not used within this method's body.

## Example

The following code demonstrates the execution flow within the `main` method. Running the `Main` class will produce the output shown below.

```java
public class Main {

    // Assuming the existence of the following helper methods:
    public static int add(int a, int b) {
        return a + b;
    }

    public static int factorial(int n) {
        if (n == 0) return 1;
        return n * factorial(n - 1);
    }

    public static void greet(String name) {
        System.out.println("Hello, " + name + "!");
    }

    // The main method to be executed
    public static void main(String[] args) {
        System.out.println("Sum: " + add(5, 10));
        System.out.println("Factorial: " + factorial(5));
        greet("Prateek");
    }
}
```

**Output:**

```
Sum: 15
Factorial: 120
Hello, Prateek!
```

***
***
