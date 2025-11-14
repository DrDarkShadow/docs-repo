## FunctionDef add
# Function: add(a, b)

## Overview

The `add` function computes the sum of two numbers.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | number | The first number to be added. |
| `b` | number | The second number to be added. |

## Description

This function takes two arguments, `a` and `b`, and returns their sum. It uses the standard addition operator (`+`) to perform the calculation. The primary purpose of this function is to encapsulate the addition operation, making the code where it's used more readable and modular.

```javascript
// The function simply returns the result of a + b
return a + b;
```

## Usage Notes

- This function is designed to work with numeric types (integers or floating-point numbers).
- If strings are provided as arguments, the `+` operator will perform string concatenation instead of numeric addition due to JavaScript's type coercion. For example, `add("5", "10")` would result in `"510"`.
- Ensure that the inputs are numbers to get the expected arithmetic sum.

**Output Example**: The function returns a single numeric value representing the sum of the two input parameters.

## Example

```javascript
// Example usage
let result = add(5, 10);
console.log(result);
```

**Output:**

```
15
```

***
## FunctionDef factorial
# Function: factorial(n)

## Overview

The `factorial` function recursively calculates the factorial of a given non-negative integer.

## Parameters

-   `n` (Number): The non-negative integer for which the factorial will be computed.

## Description

The `factorial` function is a classic example of recursion. It calculates the product of all positive integers up to a given number `n`.

The function operates based on two conditions:

1.  **Base Case**: The recursion terminates when the input `n` is less than or equal to 1. In this scenario, the function returns `1`. This is because the factorial of 1 (`1!`) is 1, and by convention, the factorial of 0 (`0!`) is also 1.

2.  **Recursive Step**: If `n` is greater than 1, the function multiplies `n` by the result of calling itself with the argument `n - 1`. This process continues, decrementing `n` by 1 in each subsequent call, until the base case is reached.

For example, calling `factorial(4)` triggers the following sequence:
```javascript
factorial(4) returns 4 * factorial(3)
factorial(3) returns 3 * factorial(2)
factorial(2) returns 2 * factorial(1)
factorial(1) returns 1 // Base case reached
```
The results are then multiplied back up the call stack: `2 * 1 = 2`, then `3 * 2 = 6`, and finally `4 * 6 = 24`.

## Usage Notes

-   This function is designed for non-negative integers. Providing a negative number will result in an infinite recursion, leading to a "Maximum call stack size exceeded" error.
-   Due to its recursive nature, calculating the factorial of very large numbers can also lead to a stack overflow error. For such cases, an iterative approach might be more suitable.
-   The input `n` is expected to be an integer. While it may work for floating-point numbers until the base case is met, the mathematical concept of a factorial is typically defined only for non-negative integers.

**Output Example**: The function returns a single number representing the calculated factorial.
`24`

## Example

```javascript
// Example usage
let number = 5;
let result = factorial(number);
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

- `name` (string): The name to be included in the greeting message.

## Description

This function provides a simple way to display a standardized greeting. It accepts a single argument, `name`. Inside the function, a template literal is used to construct the string `` `Hello, ${name}!` ``, where `${name}` is a placeholder that gets replaced by the value passed into the function.

The resulting string is then passed to the `console.log()` method, which outputs the message to the web console. The function itself does not have a `return` statement, so it implicitly returns `undefined`.

```javascript
// The function takes a 'name' and logs a greeting.
function greet(name) {
    // A template literal constructs the final string.
    console.log(`Hello, ${name}!`);
}
```

## Usage Notes

- This function's primary effect is logging to the console. It does not return a value that can be assigned to a variable for further use.
- While the `name` parameter is intended to be a string, JavaScript's type coercion will attempt to convert non-string arguments into a string representation for the output.

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
