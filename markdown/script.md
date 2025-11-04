## FunctionDef add
# Function: add(a, b)

## Overview

The `add` function computes the sum of two numbers.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | Number | The first number to be added. |
| `b` | Number | The second number to be added. |

## Description

This function takes two parameters, `a` and `b`, and returns their sum. It uses the standard addition operator (`+`) to perform the calculation. The function directly returns the result of the `a + b` operation.

```javascript
// The function returns the result of the addition
return a + b;
```

## Usage Notes

- While designed for numbers, the `+` operator in JavaScript will perform string concatenation if one or both of the operands are strings. For example, `add(5, "5")` would result in `"55"`.
- The function does not include any type checking or error handling. It is the caller's responsibility to ensure that both arguments are of the `Number` type for a predictable arithmetic result.

**Output Example**: The function returns a single `Number` which is the sum of the two input parameters.

## Example

```javascript
// Example usage
const num1 = 10;
const num2 = 25;
const result = add(num1, num2);
console.log(result);
```

**Output:**

```
35
```

***
## FunctionDef factorial
# Function: factorial(n)

## Overview

The `factorial` function recursively calculates the factorial of a given non-negative integer `n`.

## parameters

- `n` (Number): The non-negative integer for which the factorial will be calculated.

## Description

This function implements the factorial calculation using a recursive approach. The logic is based on the mathematical definition of a factorial, where the factorial of a non-negative integer `n` is the product of all positive integers up to `n`.

The function operates as follows:

- **Base Case:** It first checks if the input `n` is less than or equal to 1. If true, the function returns `1`. This serves as the termination condition for the recursion, as the factorial of 1 (`1!`) and 0 (`0!`) are both defined as 1.

- **Recursive Step:** If `n` is greater than 1, the function returns the product of `n` and the result of calling itself with the argument `n - 1`. This process continues to break down the number until it reaches the base case.

For example, `factorial(4)` is computed as follows:
```javascript
factorial(4) = 4 * factorial(3)
             = 4 * (3 * factorial(2))
             = 4 * (3 * (2 * factorial(1)))
             = 4 * (3 * (2 * 1))
             = 24
```

## Usage Notes

- The function is intended for non-negative integers. Providing a negative number will cause an infinite recursion, leading to a stack overflow error.
- The base case `n <= 1` ensures that `factorial(0)` correctly returns `1`.
- Be cautious with large input values. Deep recursion can lead to a "Maximum call stack size exceeded" error. Furthermore, the result can quickly grow larger than JavaScript's `Number.MAX_SAFE_INTEGER`, which may cause a loss of precision.

**Output Example**: A single number representing the calculated factorial value.

## Example

```javascript
// Example usage
const number = 5;
const result = factorial(number);
console.log(`The factorial of ${number} is ${result}`);
```

**Output:**

```
The factorial of 5 is 120
```

***
## FunctionDef greet
# Function: greet

## Overview

The `greet` function prints a personalized greeting message to the console.

## parameters

- `name` (String): The name to be included in the greeting message.

## Description

This function provides a simple way to display a standardized greeting to the console. It accepts a single string argument, `name`.

The core logic uses the `console.log()` method to output a formatted string. The string is created using a template literal: `` `Hello, ${name}!` ``. This syntax allows for string interpolation, where the value of the `name` parameter is directly embedded into the output string, creating a personalized message. The function does not return any value; its only purpose is to log a message as a side effect.

```javascript
// The function takes a 'name' and logs a greeting.
function greet(name) {
    // The template literal constructs the final string.
    console.log(`Hello, ${name}!`);
}
```

## Usage Notes

- The output of this function is directed to the standard console, such as a browser's developer console or a Node.js terminal. It does not render content on a webpage.
- While a string is the expected type for the `name` parameter, JavaScript's type coercion will attempt to convert other data types (like numbers or objects) into a string representation when they are passed.

## Example

```javascript
// Example usage
greet("World");
greet("Alice");
```

**Output:**

```
Hello, World!
Hello, Alice!
```

***
