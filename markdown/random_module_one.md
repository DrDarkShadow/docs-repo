## FunctionDef num(a, b)
# Function: def num(a, b)

## Overview

The `num` function calculates and returns the sum of two provided numbers.

## parameters

| Parameter | Type      | Description                |
|-----------|-----------|----------------------------|
| `a`       | int/float | The first number to add.   |
| `b`       | int/float | The second number to add.  |

## Description

This function provides a straightforward way to perform addition. It accepts two arguments, `a` and `b`, which are expected to be numerical values (integers or floating-point numbers). The core logic of the function is to use the `+` operator to compute the sum of `a` and `b`. The resulting value is then returned to the caller.

For example, if `a` is `5` and `b` is `10`, the function will compute `5 + 10` and return `15`.

```python
# The function simply returns the result of a + b
return a + b
```

## Usage Notes

- This function is designed for numeric types like `int` and `float`.
- If string values are passed as arguments, the function will perform string concatenation instead of mathematical addition (e.g., `num("hello", "world")` would return `"helloworld"`).
- The type of the returned value will depend on the types of the input parameters (e.g., adding two integers returns an integer; adding an integer and a float returns a float).

**Output Example**: A numeric value representing the sum.
`15`

## Example

```python
# Example usage with two integers
result = num(5, 10)
print(result)

# Example usage with a float and an integer
result_float = num(7.5, 3)
print(result_float)
```

**Output:**

```
15
10.5
```

***
## FunctionDef generate_random_integers(count, start, end)
# Function: generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]

## Overview

The `generate_random_integers` function generates a list of a specified number of pseudo-random integers within a given inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | `int` | The number of random integers to generate. This value must be non-negative. |
| `start` | `int` | The inclusive lower bound for the random numbers. Defaults to `0`. |
| `end` | `int` | The inclusive upper bound for the random numbers. Defaults to `100`. |

## Description

This function provides a convenient way to create a list of pseudo-random integers. Its operation can be broken down into three main steps:

1.  **Input Validation**: The function first checks if the `count` parameter is a non-negative number. If `count` is less than zero, it is considered invalid for generating a list, and the function will raise a `ValueError`.

2.  **Boundary Correction**: It then compares the `start` and `end` parameters. If `start` is found to be greater than `end`, the function automatically swaps their values. This ensures that the range is always valid, preventing errors in the random number generation step. For example, a call with `start=50` and `end=10` will be treated as `start=10` and `end=50`.

3.  **Random Number Generation**: Using a list comprehension, the function iterates `count` times. In each iteration, it calls `random.randint(start, end)` to produce a single integer that is uniformly sampled from the inclusive range `[start, end]`. These integers are collected into a list.

```python
# The core generation logic
return [random.randint(start, end) for _ in range(count)]
```

Finally, the function returns the newly created list of random integers.

## Usage Notes

- This function requires the `random` module to be imported in the script.
- If the `start` value is greater than the `end` value, they will be swapped internally to ensure a valid range.
- Providing a negative value for the `count` parameter will raise a `ValueError`.
- The default behavior, if no `start` or `end` is provided, is to generate numbers in the range `[0, 100]`.

**Output Example**: The function returns a list of integers. The length of the list will be equal to the `count` parameter.

## Example

```python
import random # This import is necessary for the function to work

# Example 1: Generate 5 random integers between 10 and 20.
result = generate_random_integers(5, 10, 20)
print(result)

# Example 2: Generate 3 random integers using default bounds (0 to 100).
result_default = generate_random_integers(3)
print(result_default)
```

**Output:**

(Note: The actual output will vary with each execution due to its random nature)

```
[12, 18, 11, 20, 15]
[87, 2, 54]
```

***
## FunctionDef fibonacci(n)
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative approach.

## parameters

- `n` (int): The 0-indexed position in the Fibonacci sequence for which to find the number.

## Description

This function provides a memory-efficient, iterative method to calculate a Fibonacci number. The logic proceeds as follows:

1.  **Input Validation**: The function first checks if the input `n` is a negative number. Since the Fibonacci sequence is not defined for negative indices, it raises a `ValueError` if this condition is met.

2.  **Initialization**: Two variables, `a` and `b`, are initialized to `0` and `1` respectively. These represent the first two numbers in the sequence, F₀ and F₁.

3.  **Iteration**: The function then enters a `for` loop that iterates `n` times. In each iteration, the values of `a` and `b` are updated using tuple assignment: `a, b = b, a + b`. This simultaneously sets `a` to the current value of `b` and `b` to the sum of the previous `a` and `b`, effectively advancing one step in the sequence.

4.  **Return Value**: After the loop completes, the variable `a` holds the nth Fibonacci number. If `n` is `0`, the loop does not run, and the initial value of `a` (`0`) is returned, which is correct.

For example, to compute `fibonacci(3)`:
- Initial state: `a = 0`, `b = 1`
- Loop 1: `a` becomes `1`, `b` becomes `0 + 1 = 1`
- Loop 2: `a` becomes `1`, `b` becomes `1 + 1 = 2`
- Loop 3: `a` becomes `2`, `b` becomes `1 + 2 = 3`
- The loop finishes, and the function returns the final value of `a`, which is `2`.

## Usage Notes

- The input `n` must be a non-negative integer. The function will raise a `ValueError` for negative inputs.
- The sequence is 0-indexed, meaning `fibonacci(0)` returns the first number in the sequence, which is `0`.
- This iterative implementation is efficient in terms of memory and performance for large values of `n` compared to a naive recursive approach, as it avoids deep recursion stacks.

**Output Example**: The function returns a single integer.
```
34
```

## Example

```python
# Example usage to find the 9th Fibonacci number (0-indexed)
result = fibonacci(9)
print(result)
```

**Output:**

```
34
```

***
## FunctionDef choose_random_item(items)
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns a single random item from a given non-empty list of strings.

## parameters

- `items` (`List[str]`): A list of strings to choose from. This list must not be empty.

## Description

This function provides a safe way to select a random element from a list of strings.

The function first performs a validation check on the input `items` list. It uses the condition `if not items` to determine if the list is empty. If the list has no elements, the condition is `True`, and the function raises a `ValueError` with the message "items must not be empty". This prevents runtime errors that would occur if trying to select an item from an empty sequence.

If the list is not empty, the function proceeds to use the `random.choice()` method. This method, from Python's built-in `random` module, takes a sequence as an argument and returns a single item chosen uniformly at random. The item selected from the `items` list is then returned as the result of the `choose_random_item` function.

```python
# Internally, the function first checks the list
if not items:
    raise ValueError("items must not be empty")
# Then, it returns a random choice
return random.choice(items)
```

## Usage Notes

- The input list `items` must contain at least one element. Providing an empty list will result in a `ValueError`.
- This function requires the `random` module to be imported in the execution environment.
- The selection is uniformly random, meaning every item in the list has an equal probability of being chosen.

**Output Example**: A single string from the input list, such as `"cherry"`.

## Example

```python
import random
from typing import List

# Definition of the function
def choose_random_item(items: List[str]) -> str:
    """Choose a single random item from a non-empty sequence."""
    if not items:
        raise ValueError("items must not be empty")
    return random.choice(items)

# Example usage
options = ["apple", "banana", "cherry", "date"]
random_fruit = choose_random_item(options)
print(f"A random fruit was chosen: {random_fruit}")

# Example of error handling
try:
    choose_random_item([])
except ValueError as e:
    print(f"Error caught: {e}")
```

**Output:**

```
A random fruit was chosen: banana
Error caught: items must not be empty
```
(Note: The chosen fruit in the first line of the output is random and will vary with each execution.)

***
## FunctionDef shuffle_copy(items)
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a new, randomly shuffled copy of a given list, ensuring the original list remains unchanged.

## parameters

- `items` (`List[int]`): A list of integers that will be copied and then shuffled.

## Description

This function provides a safe way to shuffle a list without altering the original data structure. The process is executed in three main steps:

1.  A shallow copy of the input `items` list is created using the `list()` constructor. This new list is stored in a variable named `copy`. This step is crucial for preserving the original list.
2.  The `random.shuffle()` function is then called on the `copy`. `random.shuffle()` shuffles the elements of a sequence *in-place*, meaning it directly modifies the `copy` list by rearranging its elements into a random order.
3.  Finally, the function returns the modified `copy` list, which now contains the same elements as the original `items` list but in a new, random sequence.

```python
# Internal logic breakdown
copy = list(items)      # Create a new list object with the same elements
random.shuffle(copy)    # Shuffle the new list in-place
return copy             # Return the shuffled new list
```

## Usage Notes

- This function is non-mutating. It will not change the order of the original list passed as the `items` argument.
- The function depends on Python's built-in `random` module. Ensure that `import random` is present in the file where this function is used.
- The returned value is a new list object, not a reference to the original.
- While the type hint specifies `List[int]`, the function will work correctly with lists containing any type of element (e.g., strings, floats, or mixed types).

**Output Example**: A possible return value for an input of `[1, 2, 3, 4, 5]`.

```
[4, 1, 5, 3, 2]
```

## Example

The following example demonstrates how to use `shuffle_copy` and confirms that the original list remains unmodified.

```python
import random

# Assume shuffle_copy is defined in the same scope
def shuffle_copy(items: list) -> list:
    copy = list(items)
    random.shuffle(copy)
    return copy

# Define an original list of numbers
original_list = [10, 20, 30, 40, 50]
print(f"Original list before shuffling: {original_list}")

# Get a shuffled copy of the list
shuffled_list = shuffle_copy(original_list)

print(f"Shuffled copy: {shuffled_list}")
print(f"Original list after shuffling: {original_list}")

```

**Output:**

```
Original list before shuffling: [10, 20, 30, 40, 50]
Shuffled copy: [30, 50, 10, 20, 40]  # Note: The order is random and will vary with each execution.
Original list after shuffling: [10, 20, 30, 40, 50]
```

***
