## FunctionDef num(a, b)
# Function: def num(a, b)

## Overview

The `num` function calculates and returns the sum of two provided arguments.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | int / float / str | The first operand for the addition operation. |
| `b` | int / float / str | The second operand for the addition operation. |

## Description

This function performs a basic addition operation on two input parameters, `a` and `b`. It utilizes Python's built-in addition operator (`+`) to compute the result. The behavior of the operator depends on the data types of the input arguments. If `a` and `b` are numbers (integers or floats), the function will return their arithmetic sum. If they are strings, the function will return their concatenated string.

The core logic is simply to return the result of `a + b`.

```python
return a + b
```

## Usage Notes

- This function is primarily intended for adding two numbers (`int` or `float`).
- If strings are passed as arguments, the function will perform string concatenation instead of arithmetic addition.
- Passing arguments of incompatible types (e.g., an integer and a string) will result in a `TypeError`.

**Output Example**: A numerical value representing the sum.

## Example

```python
# Example usage with integers
result = num(5, 10)
print(result)
```

**Output:**

```
15
```

***
## FunctionDef generate_random_integers(count, start, end)
# Function: generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]

## Overview

The `generate_random_integers` function generates a list of a specified number of pseudo-random integers within a given inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | int | The number of random integers to generate. This value must be non-negative. |
| `start` | int | The inclusive lower bound for the random values. Defaults to `0`. |
| `end` | int | The inclusive upper bound for the random values. Defaults to `100`. |

## Description

This function provides a convenient way to create a list of pseudo-random integers. The logic proceeds in three main steps:

1.  **Input Validation**: The function first checks if the `count` parameter is less than zero. If it is, a `ValueError` is raised, as it's impossible to generate a negative number of integers.

2.  **Range Correction**: It then compares the `start` and `end` parameters. If `start` is found to be greater than `end`, the function automatically swaps their values. This ensures that `random.randint` receives a valid range (`start` <= `end`) without requiring the user to order the boundary arguments correctly.

3.  **Generation**: Finally, the function uses a list comprehension to generate the integers. It iterates `count` times, and in each iteration, it calls `random.randint(start, end)` to produce a single integer uniformly sampled from the inclusive range `[start, end]`. These integers are collected into a list, which is then returned.

```python
# Internal logic for generating 5 numbers between 1 and 10
# This assumes the random module is imported
[random.randint(1, 10) for _ in range(5)]
```

## Usage Notes

-   The `count` parameter must be a non-negative integer. Providing a negative value will result in a `ValueError`.
-   The function gracefully handles cases where `start > end` by swapping the values internally. For example, `generate_random_integers(5, 50, 10)` will behave identically to `generate_random_integers(5, 10, 50)`.
-   This function requires the `random` module to be imported in the script.
-   The returned list will contain exactly `count` elements.

**Output Example**: A call to `generate_random_integers(5, 1, 20)` would return a list of 5 integers.

```
[4, 19, 2, 11, 8]
```

## Example

```python
# This example requires the 'random' module to be imported first.
import random
from typing import List

def generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]:
    """Return a list of pseudo-random integers."""
    if count < 0:
        raise ValueError("count must be non-negative")
    if start > end:
        start, end = end, start
    return [random.randint(start, end) for _ in range(count)]

# Generate 5 random integers between 10 and 20 (inclusive)
result = generate_random_integers(5, 10, 20)
print(result)

# Generate 3 random integers using default start (0) and end (100)
result_default = generate_random_integers(3)
print(result_default)
```

**Output:**

(Note: The output is random and will vary with each execution)
```
[15, 11, 20, 18, 12]
[87, 23, 91]
```

***
## FunctionDef fibonacci(n)
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative method.

## parameters

- `n` (int): The 0-indexed position in the Fibonacci sequence for which to find the value.

## Description

This function calculates the nth Fibonacci number, where the sequence starts with 0 and 1.

The function first validates the input `n`. If `n` is a negative number, it raises a `ValueError` because the Fibonacci sequence is not defined for negative indices.

It initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the sequence (F₀ and F₁).

The core logic resides in a `for` loop that iterates `n` times. In each iteration, the values of `a` and `b` are updated simultaneously using tuple assignment:
```python
a, b = b, a + b
```
This operation effectively shifts the sequence forward: `a` takes the value of `b` (the next number in the sequence), and `b` becomes the sum of the previous two numbers (the old `a` and `b`).

After the loop completes `n` iterations, the variable `a` will hold the value of the nth Fibonacci number, which is then returned.

## Usage Notes

- The input `n` must be a non-negative integer. Providing a negative value will result in a `ValueError`.
- The function implements a 0-indexed sequence, meaning `fibonacci(0)` returns `0`, `fibonacci(1)` returns `1`, and so on.
- This iterative approach is efficient in terms of memory and performance compared to a naive recursive implementation, especially for large values of `n`.

**Output Example**: The function returns a single integer representing the Fibonacci number at the specified index.
```
34
```

## Example

```python
# Example usage: Calculate the 9th Fibonacci number (0-indexed)
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

The `choose_random_item` function selects and returns a single, uniformly random item from a given list of strings.

## parameters

- **items** `List[str]`: A list of strings from which one item will be randomly selected. This list must not be empty.

## Description

This function provides a safe way to choose a random element from a list. It begins by performing a validation check on the input list `items`.

The core logic first evaluates if the list is empty using `if not items`. If the list is found to be empty, the function immediately stops execution and raises a `ValueError` with the message "items must not be empty". This prevents the underlying `random.choice` function from failing, as it cannot operate on an empty sequence.

If the list is not empty, the function proceeds to call `random.choice(items)`. This standard library function selects a single item from the `items` list, where each item has an equal probability of being chosen. The selected string is then returned as the result.

```python
# The function first checks if the list is empty.
if not items:
    # If so, it raises an error.
    raise ValueError("items must not be empty")
# Otherwise, it uses random.choice to pick and return an element.
return random.choice(items)
```

## Usage Notes

- The input list `items` must contain at least one element. Providing an empty list will result in a `ValueError`.
- This function depends on Python's `random` module. Ensure it is imported in the file where this function is used.
- The selection is uniformly random, meaning every item in the list has an equal chance of being chosen on any given call.

**Output Example**: The function returns a single string. If the input is `['red', 'green', 'blue']`, a possible return value is `'green'`.

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

# Example 1: Choosing from a list of colors
colors = ["red", "green", "blue", "yellow"]
random_color = choose_random_item(colors)
print(f"The chosen color is: {random_color}")

# Example 2: Handling an empty list
try:
    empty_list = []
    choose_random_item(empty_list)
except ValueError as e:
    print(f"Error when using an empty list: {e}")
```

**Output:**

```
The chosen color is: blue
Error when using an empty list: items must not be empty
```

***
## FunctionDef shuffle_copy(items)
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a shuffled copy of a given list of integers without modifying the original list.

## parameters

- **`items`** (`List[int]`): The list of integers that you want to create a shuffled copy of.

## Description

This function provides a safe way to shuffle a list by operating on a copy rather than the original data. The process involves three main steps:

1.  A shallow copy of the input `items` list is created using `copy = list(items)`. This step is crucial as it ensures that any subsequent modifications do not affect the original list provided by the user.
2.  The `random.shuffle()` function is then called on the newly created `copy`. This function shuffles the elements of the `copy` list in-place, rearranging them into a random order.
3.  Finally, the function returns the `copy`, which now contains the same elements as the original `items` list but in a new, randomized sequence.

```python
# The function depends on the 'random' module
import random

# Step 1: A copy is made
original_list = [1, 2, 3]
copy_of_list = list(original_list) # copy_of_list is [1, 2, 3]

# Step 2: The copy is shuffled in-place
random.shuffle(copy_of_list) # copy_of_list might now be [3, 1, 2]

# Step 3: The shuffled copy is returned
# The original_list remains [1, 2, 3]
```

## Usage Notes

- **Non-Mutating**: This function is designed to be non-destructive. It does not alter the original `items` list passed to it. This is in contrast to `random.shuffle()`, which shuffles a list in-place.
- **Dependency**: This function relies on Python's built-in `random` module. Ensure `import random` is present at the top of your script for the function to work.
- **Type Generality**: Although the type hint specifies `List[int]`, the function's logic will work correctly with lists containing elements of any type (e.g., strings, floats, or objects).

**Output Example**: A new list with the same elements as the input list, but in a random order. The exact order will vary with each execution.

```
[4, 1, 5, 2, 3]
```

## Example

```python
import random
from typing import List

def shuffle_copy(items: List[int]) -> List[int]:
    """Return a shuffled copy of the given list without mutating the input."""
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_numbers = [1, 2, 3, 4, 5]
print(f"Original list before shuffling: {original_numbers}")

shuffled_numbers = shuffle_copy(original_numbers)
print(f"Shuffled list: {shuffled_numbers}")
print(f"Original list after shuffling: {original_numbers}")
```

**Output:**

```
Original list before shuffling: [1, 2, 3, 4, 5]
Shuffled list: [3, 5, 1, 2, 4]
Original list after shuffling: [1, 2, 3, 4, 5]
```

***
