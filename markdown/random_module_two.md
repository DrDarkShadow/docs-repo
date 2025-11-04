## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns a single, uniformly random element from a given list of strings.

## parameters

- **`items`** (`List[str]`): A list of strings from which one item will be randomly selected. This list must not be empty.

## Description

This function provides a safe way to choose a random item from a list. The logic proceeds as follows:

1.  It first performs a validation check to determine if the input list `items` is empty.
2.  If the list is empty, the condition `if not items:` evaluates to `True`, and the function raises a `ValueError` with the message "items must not be empty". This prevents errors that would otherwise occur when trying to select an item from an empty sequence.
3.  If the list contains one or more elements, the function calls `random.choice(items)`. The `random.choice()` method, from Python's standard `random` library, selects a single item from the sequence at random.
4.  Finally, the chosen string is returned as the result of the function.

## Usage Notes

- The input list `items` must contain at least one element. Providing an empty list will result in a `ValueError`.
- This function requires the `random` module to be imported in the script where it is used.
- The selection is uniform, meaning every item in the list has an equal probability of being chosen.

**Output Example**: A single string from the input list. For example: `'banana'`

## Example

```python
import random
from typing import List

# The function is assumed to be available for import
def choose_random_item(items: List[str]) -> str:
    """Choose a single random item from a non-empty sequence."""
    if not items:
        raise ValueError("items must not be empty")
    return random.choice(items)

# Example 1: Successful usage with a non-empty list
fruit_list = ["apple", "banana", "cherry", "date"]
random_fruit = choose_random_item(fruit_list)
print(f"A random fruit was chosen: {random_fruit}")

# Example 2: Handling the error for an empty list
try:
    empty_list = []
    choose_random_item(empty_list)
except ValueError as e:
    print(f"Error caught as expected: {e}")
```

**Output:**

The output for the first example will vary on each run due to its random nature.

A possible output for Example 1:
```
A random fruit was chosen: cherry
```

The output for Example 2 will always be:
```
Error caught as expected: items must not be empty
```

***
## FunctionDef fibonacci
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative approach.

## parameters

- `n` (int): The 0-based index of the Fibonacci number to be computed.

## Description

This function provides a memory-efficient way to calculate a Fibonacci number. The Fibonacci sequence starts with 0 and 1, and each subsequent number is the sum of the two preceding ones (e.g., 0, 1, 1, 2, 3, 5, 8...).

The function begins by validating the input `n`. If `n` is a negative number, it raises a `ValueError` because the Fibonacci sequence is not defined for negative indices.

It initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the sequence, F₀ and F₁.

The core of the function is a `for` loop that runs `n` times. In each iteration, the values of `a` and `b` are updated simultaneously. The current value of `b` is assigned to `a`, and the sum of the old `a` and `b` is assigned to `b`. This process effectively steps through the sequence:

```python
# Initial state: a=0, b=1
# After 1st iteration: a=1, b=1
# After 2nd iteration: a=1, b=2
# After 3rd iteration: a=2, b=3
a, b = b, a + b
```

After the loop completes, the variable `a` holds the nth Fibonacci number, which is then returned. For an input of `n=0`, the loop does not run, and the initial value of `a` (0) is correctly returned.

## Usage Notes

- The index `n` is 0-based. For example, `fibonacci(0)` returns `0`, and `fibonacci(1)` returns `1`.
- The function will raise a `ValueError` if a negative integer is provided as the argument.
- This iterative implementation is efficient for large values of `n` as it avoids the overhead and potential stack overflow of a naive recursive approach.

**Output Example**: The function returns a single integer which is the Fibonacci number at the specified index `n`.

## Example

```python
# Example usage
# Calculate the 9th Fibonacci number (0-indexed)
index = 9
fib_number = fibonacci(index)
print(f"The Fibonacci number at index {index} is: {fib_number}")

# Example of invalid input
try:
    fibonacci(-1)
except ValueError as e:
    print(e)
```

**Output:**

```
The Fibonacci number at index 9 is: 34
n must be non-negative
```

***
## FunctionDef generate_random_integers
# Function: generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]

## Overview

The `generate_random_integers` function creates and returns a list of a specified number of pseudo-random integers within a defined inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | int | The total number of integers to generate in the list. |
| `start` | int | The inclusive lower bound for the random values. Defaults to `0`. |
| `end` | int | The inclusive upper bound for the random values. Defaults to `100`. |

## Description

This function provides a straightforward way to generate a list of random integers. The logic proceeds as follows:

1.  **Input Validation**: The function first validates the `count` parameter. If `count` is a negative number, it raises a `ValueError` because it's impossible to generate a negative number of items.

    ```python
    if count < 0:
        raise ValueError("count must be non-negative")
    ```

2.  **Boundary Correction**: It checks if the `start` value is greater than the `end` value. If it is, the function swaps them to ensure that `start` is always the lower bound and `end` is the upper bound. This makes the function more robust and user-friendly, as the user does not need to worry about the order of these two parameters.

    ```python
    if start > end:
        start, end = end, start
    ```

3.  **Generation**: Using a list comprehension, the function iterates `count` times. In each iteration, it calls `random.randint(start, end)` to generate a single pseudo-random integer that is greater than or equal to `start` and less than or equal to `end`.

4.  **Return Value**: The function collects all the generated integers into a list and returns it.

## Usage Notes

- This function requires the `random` module to be imported in the script.
- The `count` parameter must be a non-negative integer.
- The range defined by `start` and `end` is inclusive, meaning both `start` and `end` can appear in the output list.
- If `start` is provided as a larger value than `end`, the function will automatically swap them internally.

**Output Example**: A list containing integers.

```
[42, 8, 99, 23, 76]
```

## Example

```python
import random
from typing import List

def generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]:
    """Return a list of pseudo-random integers.

    Parameters:
        count: Number of integers to generate.
        start: Inclusive lower bound for values.
        end: Inclusive upper bound for values.

    Returns:
        A list containing `count` integers sampled uniformly in [start, end].
    """
    if count < 0:
        raise ValueError("count must be non-negative")
    if start > end:
        start, end = end, start
    return [random.randint(start, end) for _ in range(count)]

# Example usage: Generate 5 random integers between 10 and 20.
result = generate_random_integers(5, 10, 20)
print(result)
```

**Output:**

(Note: The output is random and will vary with each execution)
```
[15, 11, 20, 18, 12]
```

***
## FunctionDef shuffle_copy
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function creates and returns a new list with the elements of the input list arranged in a random order, leaving the original list unchanged.

## parameters

- **`items`** (`List[int]`): A list of integers that you want to shuffle.

## Description

This function provides a safe way to shuffle a list without altering the original data structure. The process is executed in three main steps:

1.  A shallow copy of the input `items` list is created using the `list()` constructor. This new list is stored in a variable named `copy`. This step is crucial for preserving the original list.
2.  The `random.shuffle()` function is then called on the `copy`. This function shuffles the elements of the `copy` list in-place, rearranging them into a random order.
3.  Finally, the function returns the modified `copy`, which now contains the same elements as the original `items` list but in a new, randomized sequence.

```python
# Internal logic breakdown
# Assume items = [10, 20, 30]

# 1. Create a shallow copy
copy = list(items)  # copy is now [10, 20, 30], but a separate object from items

# 2. Shuffle the copy in-place
random.shuffle(copy)  # copy might become [20, 30, 10]

# 3. Return the shuffled copy
return copy
```

## Usage Notes

- This function is non-mutating, meaning the original list passed as the `items` parameter will not be changed.
- The function depends on Python's standard `random` module. You must have `import random` at the beginning of your script to use this function.
- The randomness is based on the default random number generator used by the `random` module.

**Output Example**: The function returns a new list. For an input of `[1, 2, 3]`, a possible output could be:

```
[3, 1, 2]
```

## Example

```python
import random
from typing import List

# Definition of the function
def shuffle_copy(items: List[int]) -> List[int]:
    """Return a shuffled copy of the given list without mutating the input."""
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_numbers = [1, 2, 3, 4, 5, 6]
shuffled_numbers = shuffle_copy(original_numbers)

print(f"Original List: {original_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")
```

**Output:**

```
Original List: [1, 2, 3, 4, 5, 6]
Shuffled Copy: [4, 1, 6, 3, 5, 2]
```
*(Note: The actual order of elements in "Shuffled Copy" will vary with each execution due to its random nature.)*

***
