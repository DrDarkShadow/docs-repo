## FunctionDef add
# Function: add(a, b)

## Overview

The `add` function computes the sum of two given values.

## parameters

| Parameter | Type | Description |
|-----------|--------|-------------|
| `a` | Number | The first number or addend. |
| `b` | Number | The second number or addend. |

## Description

The `add` function takes two parameters, `a` and `b`, and returns their sum. It uses the standard addition operator (`+`) to perform the calculation. The function is straightforward and directly returns the result of the expression `a + b`.

While designed for numeric addition, it's important to note that the `+` operator in JavaScript is overloaded. If one or both of the arguments are strings, the operator will perform string concatenation instead of numeric addition.

```javascript
// Numeric addition
add(10, 5); // Returns 15

// String concatenation
add("Hello, ", "World!"); // Returns "Hello, World!"
```

## Usage Notes

- This function is primarily intended for adding two numbers.
- If string values are passed as arguments, the function will perform string concatenation instead of mathematical addition. For example, `add("5", "10")` will return `"510"`.
- To ensure numeric addition, make sure both arguments are of the `Number` type before passing them to the function.

**Output Example**: The function returns a single value which is the result of the addition or concatenation operation.

```
15
```

## Example

```javascript
// Example 1: Adding two integers
let sum = add(5, 10);
console.log(sum);

// Example 2: Adding floating-point numbers
let floatSum = add(3.14, 2.71);
console.log(floatSum);

// Example 3: Concatenating strings (demonstrates type coercion)
let greeting = add("Hello, ", "JavaScript!");
console.log(greeting);
```

**Output:**

```
15
5.85
Hello, JavaScript!
```

***
## FunctionDef factorial
# Function: factorial(n)

## Overview

The `factorial` function recursively calculates the factorial of a given non-negative integer.

## parameters

*   `n` (Number): The non-negative integer for which the factorial will be computed.

## Description

This function implements the factorial operation using recursion. The factorial of a non-negative integer `n`, denoted by `n!`, is the product of all positive integers less than or equal to `n`.

The function's logic is based on a ternary operator which serves as a compact `if-else` statement:
`return n <= 1 ? 1 : n * factorial(n - 1);`

1.  **Base Case**: The recursion terminates when `n` is less than or equal to 1. By definition, the factorial of 1 (`1!`) is 1, and the factorial of 0 (`0!`) is also 1. The function returns `1` in this case, which prevents infinite recursion.

2.  **Recursive Step**: If `n` is greater than 1, the function returns the product of `n` and the result of calling `factorial` with the argument `n - 1`. This process repeats, decrementing `n` by 1 in each subsequent call, until the base case is reached.

For example, `factorial(4)` is computed as follows:
- `factorial(4)` returns `4 * factorial(3)`
- `factorial(3)` returns `3 * factorial(2)`
- `factorial(2)` returns `2 * factorial(1)`
- `factorial(1)` returns `1` (base case)

The results are then multiplied up the call stack: `2 * 1 = 2`, then `3 * 2 = 6`, and finally `4 * 6 = 24`.

## Usage Notes

- The function is intended for non-negative integers. Providing a negative number will result in an infinite loop and a "Maximum call stack size exceeded" error.
- Due to the recursive nature of this function, calculating the factorial of very large numbers can lead to a stack overflow error. An iterative approach is recommended for large inputs.
- Factorial values grow very rapidly. JavaScript numbers may lose precision for factorials of numbers greater than 17, and will return `Infinity` for larger values.

**Output Example**: The function returns a single `Number` representing the calculated factorial.

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

- `name` (string): The name of the person to greet. This value will be embedded in the output message.

## Description

This function provides a simple way to display a standard greeting. It accepts a single argument, `name`. Inside the function, a template literal string `` `Hello, ${name}!` `` is constructed. The `${name}` placeholder is dynamically replaced with the value passed into the `name` parameter.

Finally, the built-in `console.log()` method is called to output the complete string to the standard output, which is typically the developer console in a web browser or the terminal in a Node.js environment.

```javascript
function greet(name) {
    console.log(`Hello, ${name}!`);
}
```

## Usage Notes

- This function does not return any value; its sole purpose is to log a message to the console.
- While a `string` is the expected type for the `name` parameter, JavaScript's type coercion will attempt to convert any passed value into a string representation. For example, passing the number `123` will result in the output "Hello, 123!".

## Example

```javascript
// Example usage
greet("Alice");
greet("World");
```

**Output:**

```
Hello, Alice!
Hello, World!
```

***
