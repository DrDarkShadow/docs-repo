## FunctionDef add
# Function: add(a, b)

## Overview

The `add` function calculates the sum of two numbers and returns the result.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | number | The first number to be added. |
| `b` | number | The second number to be added. |

## Description

This function provides a straightforward implementation of addition. It accepts two arguments, `a` and `b`. Inside the function, the `+` operator is used to compute the sum of these two arguments. The resulting value is then returned by the function.

```javascript
// The function returns the result of a + b
return a + b;
```

## Usage Notes

- This function is designed to work with numeric inputs.
- If strings are provided as arguments, the `+` operator will perform string concatenation instead of addition. For example, `add("2", "3")` would result in `"23"`.
- If one argument is a number and the other is a string, JavaScript will convert the number to a string and concatenate them.

**Output Example**: The function returns a single value of the same type as the input if both are numbers, or a string if concatenation occurs.

## Example

```javascript
// Example usage
const result = add(5, 10);
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

## parameters

-   `n` (Number): The non-negative integer for which the factorial will be calculated.

## Description

This function implements the factorial calculation using recursion. The logic is based on the mathematical definition of a factorial:

-   The factorial of 0 (0!) is 1.
-   The factorial of 1 (1!) is 1.
-   The factorial of any integer `n` greater than 1 is `n` multiplied by the factorial of `n-1`.

The function first checks for the base case: if the input `n` is less than or equal to 1. If this condition is true, it returns `1`, stopping the recursion.

If `n` is greater than 1, the function enters the recursive step. It returns the product of `n` and the result of calling itself (`factorial`) with the argument `n - 1`. This process continues until the base case is reached.

For example, `factorial(4)` would be calculated as:
`4 * factorial(3)`
`4 * (3 * factorial(2))`
`4 * (3 * (2 * factorial(1)))`
`4 * (3 * (2 * 1))`
Which evaluates to `24`.

## Usage Notes

-   This is a recursive function. Providing a very large number for `n` can lead to a "Maximum call stack size exceeded" error (stack overflow).
-   The function is intended for non-negative integers. Passing a negative number will result in an infinite recursion and a stack overflow.
-   The factorial value grows very quickly. For larger values of `n`, the result may exceed JavaScript's `Number.MAX_SAFE_INTEGER`, potentially leading to a loss of precision.

**Output Example**: The function returns a single `Number` representing the calculated factorial. For an input of `5`, the output would be `120`.

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
# Function: greet(name)

## Overview

The `greet` function logs a personalized greeting message to the console.

## parameters

- `name` (`String`): The name of the person to greet. This value will be embedded in the output message.

## Description

The `greet` function is a simple utility designed to display a personalized welcome message. It accepts a single argument, `name`, which is intended to be a string representing a name.

The core logic of the function resides in a single `console.log()` statement. This statement uses a JavaScript template literal (enclosed in backticks `` ` ``) to construct the output string. The provided `name` is embedded directly into the string `Hello, ${name}!` using the `${...}` placeholder syntax. The resulting message is then printed to the standard console.

This function does not return any value; its sole purpose is to produce a side effect by logging output.

## Usage Notes

- The function prints directly to the console and does not return the greeting string. If you need the string value for further processing, the function would need to be modified to return it.
- While the `name` parameter is expected to be a string, JavaScript's type coercion will convert other data types (like numbers or objects) into their string representation when they are passed to the function.

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
