## FunctionDef num(a, b)
# Function: def num(a, b)

## Overview

The `num` function returns the result of applying the addition operator (`+`) to two input arguments.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | `int`, `float`, `str`, `list` | The first operand for the addition or concatenation operation. |
| `b` | `int`, `float`, `str`, `list` | The second operand, which must be of a type compatible with `a`. |

## Description

This function takes two arguments, `a` and `b`, and computes their sum using the `+` operator. The behavior of the function is dependent on the data types of the input parameters.

If `a` and `b` are numeric types (such as `int` or `float`), the function performs arithmetic addition and returns their numerical sum.

```python
# Numeric addition
result = num(10, 20)
# result is 30
```

If `a` and `b` are sequence types (such as `str` or `list`), the function performs concatenation and returns a new, combined sequence.

```python
# String concatenation
result = num("hello", " world")
# result is "hello world"
```

The function does not include any internal type checking. Therefore, providing incompatible types (e.g., an `int` and a `str`) will result in a `TypeError`.

## Usage Notes

- Ensure that both `a` and `b` are of compatible types that support the `+` operator.
- The function will raise a `TypeError` if the operands are of unsupported types for addition, such as attempting to add a number to a string.
- The order of parameters matters for non-commutative operations like string concatenation. For example, `num("a", "b")` returns `"ab"`, while `num("b", "a")` returns `"ba"`.

**Output Example**: For numeric inputs `5` and `3`, the output would be:
```
8
```

## Example

```python
# Example usage with integers
result_int = num(5, 10)
print(result_int)

# Example usage with strings
result_str = num("doc", "umentation")
print(result_str)
```

**Output:**

```
15
documentation
```

***
## FunctionDef generate_random_integers
# Function: generate_random_integers(count: int, start: int = 0, end: int = 100)

## Overview

The `generate_random_integers` function generates a list of a specified number of pseudo-random integers within a given inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | int | The number of random integers to generate. |
| `start` | int | The inclusive lower bound of the random number range. Defaults to `0`. |
| `end` | int | The inclusive upper bound of the random number range. Defaults to `100`. |

## Description

This function provides a straightforward way to create a list of pseudo-random integers. It operates in a few distinct steps:

First, it validates the `count` parameter. If `count` is a negative number, the function cannot produce a list of that length and will raise a `ValueError`.

Next, it ensures the integrity of the numerical range. It checks if the `start` value is greater than the `end` value. If it is, the function automatically swaps them to ensure that `start` is always the lower bound and `end` is the upper bound. This makes the function more robust and user-friendly.

Finally, the function uses a list comprehension to generate the random numbers. It iterates `count` times, and in each iteration, it calls `random.randint(start, end)`. This standard library function returns a single random integer that is greater than or equal to `start` and less than or equal to `end`. The resulting integers are collected into a list, which is then returned.

```python
# Internal logic for swapping bounds
if start > end:
    start, end = end, start
# Internal logic for generation
return [random.randint(start, end) for _ in range(count)]
```

## Usage Notes

- This function requires the `random` module to be imported to work correctly.
- The `count` parameter must be a non-negative integer. Providing a negative value will result in a `ValueError`.
- The function is inclusive of both the `start` and `end` values.
- If the provided `start` value is greater than the `end` value, the function will automatically swap them to form a valid range.

**Output Example**: A list of integers.

```
[42, 8, 99, 54, 23]
```

## Example

```python
import random
from typing import List

# Definition of the function from the documentation
def generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]:
    """Return a list of pseudo-random integers."""
    if count < 0:
        raise ValueError("count must be non-negative")
    if start > end:
        start, end = end, start
    return [random.randint(start, end) for _ in range(count)]

# Example usage: Generate 5 random integers between 1 and 50.
random_numbers = generate_random_integers(5, 1, 50)
print(random_numbers)
```

**Output:**

(Note: The output is random and will vary with each execution.)
```
[34, 12, 48, 2, 25]
```

***
## FunctionDef fibonacci
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative approach.

## parameters

- `n` (int): The 0-indexed position in the Fibonacci sequence for which to find the value. Must be a non-negative integer.

## Description

This function calculates a Fibonacci number based on its index `n`. The logic begins by handling invalid input; if `n` is a negative number, a `ValueError` is raised.

The function initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the Fibonacci sequence (F₀ and F₁).

It then enters a `for` loop that iterates `n` times. In each iteration, the values of `a` and `b` are updated using tuple assignment: `a, b = b, a + b`. This operation effectively shifts the sequence forward: the new `a` takes the value of the old `b`, and the new `b` becomes the sum of the old `a` and `b`.

After the loop completes, the variable `a` holds the nth Fibonacci number, which is then returned. For `n=0`, the loop does not run, and the initial value of `a` (0) is returned correctly.

```python
# For n = 3:
# Initial state: a = 0, b = 1
# Iteration 1: a becomes 1, b becomes 0 + 1 = 1
# Iteration 2: a becomes 1, b becomes 1 + 1 = 2
# Iteration 3: a becomes 2, b becomes 1 + 2 = 3
# Loop ends. The function returns a, which is 2.
```

## Usage Notes

- The input `n` must be a non-negative integer. The function will raise a `ValueError` for negative inputs.
- The function is 0-indexed, meaning `fibonacci(0)` returns the first element of the sequence, `0`.
- This iterative implementation is memory-efficient compared to a naive recursive approach, as it avoids a deep call stack.

**Output Example**: A single integer representing the Fibonacci number at the specified index.
```
55
```

## Example

```python
# Example usage
# Calculate the 10th Fibonacci number (0-indexed)
result = fibonacci(10)
print(result)
```

**Output:**

```
55
```

***
## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns a single, uniformly random item from a given list of strings.

## parameters

- `items` (List[str]): A list of strings from which to choose. This list must not be empty.

## Description

This function provides a safe way to select a random element from a list. The logic proceeds as follows:

1.  It first performs a validation check on the input list `items`. The condition `if not items:` evaluates to `True` if the list is empty.
2.  If the list is found to be empty, the function immediately stops execution and raises a `ValueError` with the message "items must not be empty". This prevents potential errors from the underlying `random.choice` method, which requires a non-empty sequence.
3.  If the list is not empty, the function calls `random.choice(items)`. This standard library function takes the list as input and returns one of its elements, with each element having an equal probability of being selected.
4.  The randomly chosen string is then returned as the result of the function.

```python
# Internal logic for choosing an item
return random.choice(items)
```

## Usage Notes

- The input list `items` must contain at least one element. Providing an empty list will raise a `ValueError`.
- This function depends on Python's built-in `random` module. Ensure it is imported in your script (e.g., `import random`).
- The selection is uniformly random, meaning every item in the list has an equal chance of being chosen on any given call.

**Output Example**: A single string from the input list.
`"banana"`

## Example

```python
import random
from typing import List

# The function being documented
def choose_random_item(items: List[str]) -> str:
    """Choose a single random item from a non-empty sequence."""
    if not items:
        raise ValueError("items must not be empty")
    return random.choice(items)

# Example usage
options = ["red", "green", "blue", "yellow"]
selected_color = choose_random_item(options)
print(f"The selected color is: {selected_color}")

# Example of what happens with an empty list
try:
    choose_random_item([])
except ValueError as e:
    print(f"Error: {e}")
```

**Output:**

```
The selected color is: blue
Error: items must not be empty
```
*(Note: The selected color will vary with each execution as it is chosen randomly.)*

***
## FunctionDef shuffle_copy
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a new list containing a shuffled version of the elements from the input list, without modifying the original list.

## parameters

- **items** (`List[int]`): A list of integers to be shuffled.

## Description

This function provides a safe way to shuffle a list by operating on a copy rather than the original. The process is as follows:

1.  A shallow copy of the input `items` list is created using `copy = list(items)`. This is a critical step to ensure that the original list remains unchanged, adhering to the non-mutating principle of the function.
2.  The `random.shuffle()` method is then called on this `copy`. This method shuffles the elements of the list in-place, rearranging them into a random order.
3.  Finally, the function returns the modified `copy`, which now contains the same elements as the original `items` list but in a new, randomized sequence.

```python
# Internal logic
copy = list(items)
random.shuffle(copy)
return copy
```

## Usage Notes

- This function is non-mutating. It will always return a new list and will not alter the original list provided as the `items` parameter.
- The function relies on the `random` module. Ensure that `import random` is present in the file where this function is used.
- Although the type hint specifies `List[int]`, the underlying logic will work correctly with lists containing elements of any type (e.g., strings, floats, or mixed types).

**Output Example**: The function returns a `list` where the elements are the same as the input but in a random order.

## Example

```python
import random # This import is required for the function to work

# Define an original list of integers
original_numbers = [10, 20, 30, 40, 50]

# Get a shuffled copy of the list
shuffled_numbers = shuffle_copy(original_numbers)

print(f"Original List: {original_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")
```

**Output:**

```
Original List: [10, 20, 30, 40, 50]
Shuffled Copy: [30, 50, 10, 20, 40]
# Note: The actual order of elements in the output will be random with each execution.
```

***
