## FunctionDef num(a, b)
# Function: def num(a, b)

## Overview

The `num` function calculates the sum of two provided arguments.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | int / float | The first number to be added. |
| `b` | int / float | The second number to be added. |

## Description

This function takes two parameters, `a` and `b`, and returns their sum. It uses the basic addition operator (`+`) to perform the calculation. The function is straightforward and directly returns the result of the expression `a + b`.

```python
# The function adds 'a' and 'b' and returns the result.
return a + b
```

## Usage Notes

- The function is designed for numeric types like integers and floats.
- If strings are passed as arguments, the function will perform string concatenation instead of mathematical addition. For example, `num("hello", "world")` would return `"helloworld"`.
- Ensure that both arguments are of types that support the addition (`+`) operator to avoid a `TypeError`.

**Output Example**: A single numeric value representing the sum.

## Example

```python
# Example usage with two integers
result = num(15, 25)
print(result)

# Example usage with a float and an integer
float_result = num(10.5, 5)
print(float_result)
```

**Output:**

```
40
15.5
```

***
## FunctionDef generate_random_integers
# Function: generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]

## Overview

The `generate_random_integers` function creates and returns a list of a specified number of pseudo-random integers within a defined inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | `int` | The total number of integers to generate in the list. |
| `start` | `int` | The inclusive lower bound for the random values. Defaults to `0`. |
| `end` | `int` | The inclusive upper bound for the random values. Defaults to `100`. |

## Description

This function provides a straightforward way to generate a list of random integers. It operates in three main steps:

1.  **Input Validation**: The function first validates the `count` parameter. If `count` is a negative number, it raises a `ValueError` because it's impossible to generate a negative quantity of items.
2.  **Range Correction**: It checks if the `start` value is greater than the `end` value. If this condition is true, it automatically swaps the two values. This ensures that `random.randint` receives a valid range (`start` <= `end`), making the function more robust and user-friendly.
3.  **Generation**: Using a list comprehension, the function iterates `count` times. In each iteration, it calls `random.randint(start, end)` to produce a single integer uniformly sampled from the inclusive range `[start, end]`. These integers are collected into a list, which is the final return value.

This function relies on Python's built-in `random` module.

```python
# Internal logic for generating the list
return [random.randint(start, end) for _ in range(count)]
```

## Usage Notes

- This function requires the `random` module to be imported in the file where it is defined.
- The `count` parameter must be a non-negative integer (`>= 0`). Providing a negative value will result in a `ValueError`.
- Both the `start` and `end` boundaries are inclusive, meaning they can appear in the output list.
- If the provided `start` value is greater than `end`, the function will automatically swap them to form a valid range without raising an error.

**Output Example**: A possible return value for `generate_random_integers(5, 1, 10)`:

```
[3, 9, 1, 7, 5]
```

## Example

```python
import random
from typing import List

# Definition of the function itself
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
random_numbers = generate_random_integers(5, 10, 20)
print(random_numbers)

# Example with default parameters: Generate 3 random integers between 0 and 100
random_defaults = generate_random_integers(3)
print(random_defaults)
```

**Output:**

(Note: The actual output will vary with each execution due to its random nature)

```
[15, 11, 19, 10, 17]
[83, 12, 99]
```

***
## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns one random string from a given list of strings.

## parameters

- `items` (List[str]): A list of strings to choose from. This list must not be empty.

## Description

This function provides a safe way to select a single item at random from a list. The operational logic is as follows:

First, the function performs a validation check on the input `items` list. It uses the condition `if not items:` to determine if the list is empty. If the list is found to be empty, the function raises a `ValueError` with the message "items must not be empty". This
## FunctionDef shuffle_copy
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a new list containing the same elements as the input list but in a randomized order, ensuring the original list is not modified.

## parameters

- **`items`** `List[int]`: A list of integers to be shuffled. The function will not alter this original list.

## Description

This function provides a safe way to shuffle a list without causing side effects. The process is executed in three steps:

1.  A shallow copy of the input `items` list is created using `list(items)`. This new list is assigned to the `copy` variable. This step is crucial as it prevents any modification to the original list provided by the user.
2.  The `random.shuffle()` function is then called on the `copy`. The `random.shuffle()` method shuffles the sequence of elements within the `copy` list in-place, rearranging them into a random permutation.
3.  Finally, the function returns the `copy` list, which now holds the shuffled elements.

```python
# Internal logic breakdown
original_list = [1, 2, 3]
# 1. Create a shallow copy
copy = list(original_list)  # copy is now [1, 2, 3], but a separate object
# 2. Shuffle the copy in-place
random.shuffle(copy)        # copy might become [2, 3, 1]
# 3. Return the shuffled copy
return copy                 # returns [2, 3, 1]
```

## Usage Notes

- **Non-Mutating**: The primary feature of this function is that it does not mutate (change) the input `items` list. It operates on and returns a new list.
- **Random Module**: This function depends on the `random` module from Python's standard library. Ensure that `import random` is present at the top of the script where this function is used.
- **Shallow Copy**: The function creates a shallow copy. For a list of integers (`List[int]`), this is sufficient. If the list were to contain mutable objects (e.g., other lists or dictionaries), changes to the nested objects would be reflected in both the original and the copied lists.

**Output Example**: The function returns a `List[int]` where the order of elements is randomized. For an input of `[1, 2, 3, 4, 5]`, a possible return value could be:

```
[4, 1, 5, 3, 2]
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
original_numbers = [10, 20, 30, 40, 50]
shuffled_numbers = shuffle_copy(original_numbers)

print(f"Original List: {original_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")
```

**Output:**

```
Original List: [10, 20, 30, 40, 50]
Shuffled Copy: [30, 50, 10, 20, 40]
```

***
## FunctionDef fibonacci
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative method.

## parameters

- `n` (int): The 0-indexed position in the Fibonacci sequence for which to find the value.

## Description

This function provides an efficient, iterative way to calculate a Fibonacci number. The logic proceeds as follows:

1.  **Input Validation**: The function first checks if the input `n` is a negative number. Since the Fibonacci sequence is defined for non-negative indices, it raises a `ValueError` if `n` is less than 0.

2.  **Initialization**: Two variables, `a` and `b`, are initialized to `0` and `1` respectively. These represent the first two numbers in the sequence, F₀ and F₁.

3.  **Iteration**: The function iterates `n` times using a `for` loop. In each iteration, it calculates the next number in the sequence.

4.  **Value Swapping**: The core of the calculation is the tuple assignment `a, b = b, a + b`. In each step, the current value of `b` becomes the new `a`, and the sum of the previous `a` and `b` becomes the new `b`. This effectively walks through the sequence:
    - Start: `a=0`, `b=1`
    - After 1st loop: `a=1`, `b=1`
    - After 2nd loop: `a=1`, `b=2`
    - After 3rd loop: `a=2`, `b=3`
    - ...and so on.

5.  **Return Value**: After the loop has completed `n` iterations, the variable `a` holds the nth Fibonacci number. If `n` is `0`, the loop does not run, and the initial value of `a` (`0`) is returned, which is correct.

## Usage Notes

- The input `n` must be a non-negative integer. Providing a negative number will result in a `ValueError`.
- The function uses a 0-indexed sequence. For example, `fibonacci(0)` returns `0`, and `fibonacci(1)` returns `1`.
- This iterative approach is memory-efficient and avoids the recursion depth limits and performance issues associated with naive recursive solutions for large `n`.

**Output Example**: A single integer value.
`34`

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
