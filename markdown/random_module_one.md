## FunctionDef num(a, b)
# num

## Overview

The `num` function calculates and returns the sum of two input values.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | int / float | The first operand for the addition. |
| `b` | int / float | The second operand for the addition. |

## Description

This function performs a basic addition operation. It accepts two arguments, `a` and `b`, and computes their sum using the standard Python `+` operator. The resulting value is then returned to the caller. The function's behavior is dependent on the types of the input arguments, as the `+` operator is overloaded for various data types in Python.

For example, if `a` is `5` and `b` is `10`, the function will return `15`.

```python
# Internal logic
return a + b
```

## Usage Notes

- While primarily intended for numeric types like `int` and `float`, this function can also be used with any data types that support the addition (`+`) operator, such as for string concatenation.
- Passing incompatible types (e.g., an integer and a string) will raise a `TypeError`.

**Output Example**: A typical numeric return value would be an integer or a float.
```
15
```

## Example

```python
# Example usage with two integers
result = num(5, 10)
print(result)
```

**Output:**
```
15
```

---
## FunctionDef generate_random_integers(count, start, end)
# generate_random_integers

## Overview

The `generate_random_integers` function returns a list of a specified number of pseudo-random integers within a given inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | `int` | The total number of integers to generate in the list. |
| `start` | `int` | The inclusive lower bound for the random values. Defaults to `0`. |
| `end` | `int` | The inclusive upper bound for the random values. Defaults to `100`. |

## Description

This function provides a straightforward way to generate a list of random integers. The core logic is built around Python's `random.randint` function.

- **Input Validation**: The function first checks if the `count` parameter is a non-negative number. If `count` is less than zero, it raises a `ValueError` to prevent invalid list creation.
- **Range Correction**: It then compares the `start` and `end` parameters. If `start` is found to be greater than `end`, the function automatically swaps their values. This ensures that `random.randint` receives a valid range (`start <= end`) and prevents potential errors.
- **Generation**: Using a list comprehension, the function iterates `count` times. In each iteration, it calls `random.randint(start, end)` to generate a single integer that is uniformly distributed within the inclusive range `[start, end]`. These integers are collected into a list.
- **Return Value**: The function returns the newly created list containing `count` random integers.

```python
# Internal logic for generating the list
return [random.randint(start, end) for _ in range(count)]
```

## Usage Notes

- This function requires the `random` module to be imported in the file where it is defined or used.
- The `count` argument must be a non-negative integer (`>= 0`). Providing a negative value will result in a `ValueError`.
- Both the `start` and `end` values are inclusive, meaning they can appear in the generated list of random numbers.
- If the `start` value is greater than the `end` value, the function will automatically swap them to form a valid range.

**Output Example**: A typical return value for `generate_random_integers(5, 1, 100)` would be a list of five integers.

```
[42, 8, 99, 15, 73]
```

---

## Example

The following example demonstrates how to use the `generate_random_integers` function to create a list of 5 random integers between 10 and 20.

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

# Example usage: Generate 5 random integers between 10 and 20 (inclusive)
random_numbers = generate_random_integers(count=5, start=10, end=20)
print(random_numbers)
```

**Output:**

The output will be a list containing 5 random integers between 10 and 20. The exact values will vary with each execution.

```
[15, 11, 20, 18, 12]
```
## FunctionDef choose_random_item(items)
# choose_random_item

## Overview

The `choose_random_item` function selects and returns a single item at random from a given list of strings.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `items` | `List[str]` | A non-empty list of strings from which a single item will be randomly selected. |

## Description

The `choose_random_item` function provides a simple way to get a random element from a sequence of strings. The function's logic proceeds in two main steps:

1.  **Input Validation**: It first checks if the provided `items` list is empty. If the list contains no elements, the function cannot make a choice and will raise a `ValueError` to prevent runtime errors. This ensures that the function only operates on valid, non-empty inputs.

2.  **Random Selection**: If the list is not empty, the function utilizes the `random.choice()` method from Python's `random` module. This method performs a uniform random selection, meaning every item in the `items` list has an equal probability of being chosen. The selected string is then returned as the result.

```python
# Internal logic for a non-empty list
return random.choice(items)
```

## Usage Notes

- The input list `items` **must not be empty**. Providing an empty list will result in a `ValueError`.
- The selection is uniformly random, meaning every item in the list has an equal chance of being chosen.
- This function depends on Python's `random` module, which must be available in the execution environment.

**Output Example**:
A possible return value for an input of `['red', 'green', 'blue']` would be the string `'green'`.

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
color_options = ["red", "green", "blue", "yellow"]
chosen_color = choose_random_item(color_options)
print(f"The chosen color is: {chosen_color}")

# Example of what happens with an empty list
try:
    choose_random_item([])
except ValueError as e:
    print(f"Error: {e}")
```

**Output:**
```
The chosen color is: blue
Error: items must not be empty
```
*(Note: The chosen color in the first line of the output will vary with each execution due to its random nature.)*

---
## FunctionDef shuffle_copy(items)
# shuffle_copy

## Overview

The `shuffle_copy` function returns a shuffled copy of a given list without modifying the original list.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `items` | `List[int]` | A list of integers to be shuffled. |

## Description

The `shuffle_copy` function provides a safe way to create a randomly ordered version of a list while preserving the original data. The function's logic is straightforward and ensures non-mutation of the input.

First, it creates a shallow copy of the input `items` list by calling `list(items)`. This step is crucial as it creates a new list object in memory, independent of the original.

Next, it utilizes the `random.shuffle()` method to shuffle the elements of the newly created `copy` in-place. The `random.shuffle()` function rearranges the items in the list into a random sequence.

Finally, the function returns the shuffled `copy`, leaving the original `items` list completely unchanged.

```python
# Internal logic breakdown
def shuffle_copy(items: List[int]) -> List[int]:
    # 1. Create a shallow copy of the input list
    copy = list(items)
    
    # 2. Shuffle the copy in-place
    random.shuffle(copy)
    
    # 3. Return the shuffled copy
    return copy
```

## Usage Notes

- This function is **non-mutating**. It will not alter the original list passed as the `items` parameter.
- The function depends on Python's built-in `random` module. Ensure that `random` is imported in the scope where this function is defined.
- While the type hint specifies `List[int]`, the function's logic will work correctly with lists containing elements of any type (e.g., strings, floats, or mixed types).

**Output Example**: The function returns a new list with the same elements as the input but in a random order. The exact order will vary with each call.

For an input of `[1, 2, 3, 4, 5]`, a possible output could be:
```
[4, 1, 5, 3, 2]
```

## Example

```python
import random # The shuffle_copy function relies on this module

def shuffle_copy(items: list) -> list:
    """Return a shuffled copy of the given list without mutating the input."""
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_list = [10, 20, 30, 40, 50]
shuffled_list = shuffle_copy(original_list)

print(f"Original List (unchanged): {original_list}")
print(f"Shuffled Copy: {shuffled_list}")

# Another run will likely produce a different order
another_shuffled_list = shuffle_copy(original_list)
print(f"Another Shuffled Copy: {another_shuffled_list}")
```

**Output:**
```
Original List (unchanged): [10, 20, 30, 40, 50]
Shuffled Copy: [30, 50, 10, 20, 40]
Another Shuffled Copy: [50, 20, 40, 10, 30]
```
