## FunctionDef num(a, b)
# Function: def num(a, b)

## Overview

The `num` function returns the result of applying the addition operator (`+`) to two input arguments.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | `int`, `float`, `str` | The first operand for the addition operation. |
| `b` | `int`, `float`, `str` | The second operand for the addition operation. |

## Description

This function performs a simple addition operation on its two input parameters, `a` and `b`. It directly returns the output of the expression `a + b`. The behavior of the `+` operator is dependent on the data types of the provided arguments. For numeric types like integers or floats, it performs arithmetic addition. For sequence types like strings, it performs concatenation.

The core logic is a single return statement:
```python
return a+b
```

## Usage Notes

- While the function is named `num`, it can also be used to concatenate strings or other compatible types that support the `+` operator.
- Ensure that both parameters are of compatible types. For instance, attempting to add an integer to a string (e.g., `num(5, "hello")`) will raise a `TypeError`.

**Output Example**: A sample return value for numeric input:
`15`

## Example

```python
# Example 1: Adding two integers
result_sum = num(5, 10)
print(result_sum)

# Example 2: Concatenating two strings
result_concat = num("hello", " world")
print(result_concat)
```

**Output:**

```
15
hello world
```

***
## FunctionDef generate_random_integers(count, start, end)
# Function: generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]

## Overview

The `generate_random_integers` function creates and returns a list of a specified number of pseudo-random integers within a given inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | int | The total number of integers to generate in the list. |
| `start` | int | The inclusive lower bound for the random values. Defaults to `0`. |
| `end` | int | The inclusive upper bound for the random values. Defaults to `100`. |

## Description

This function provides a robust way to generate a list of random integers. The logic proceeds as follows:

1.  **Input Validation**: The function first checks if the `count` parameter is a negative number. If it is, a `ValueError` is raised, as it's impossible to generate a negative number of items.

    ```python
    if count < 0:
        raise ValueError("count must be non-negative")
    ```

2.  **Range Correction**: It then compares the `start` and `end` parameters. If `start` is found to be greater than `end`, the function automatically swaps their values. This ensures that `random.randint` receives a valid range where the lower bound is not greater than the upper bound.

    ```python
    if start > end:
        start, end = end, start
    ```

3.  **List Generation**: A list comprehension is used to efficiently generate the list of random integers. The loop runs `count` times, and in each iteration, `random.randint(start, end)` is called to produce a single integer uniformly sampled from the inclusive range `[start, end]`.

    ```python
    return [random.randint(start, end) for _ in range(count)]
    ```

The final list containing `count` random integers is then returned.

## Usage Notes

- The function requires the `random` module to be imported to work correctly.
- A `ValueError` will be raised if a negative value is provided for the `count` parameter.
- If the `start` value is greater than the `end` value, the function will automatically swap them to create a valid range, so you don't need to order them manually.
- Both `start` and `end` values are inclusive, meaning they can appear in the generated list of random integers.

**Output Example**: A call like `generate_random_integers(5, 1, 10)` would return a list similar to this:

```
[3, 9, 1, 7, 5]
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

# Example with swapped start and end values
result_swapped = generate_random_integers(3, 50, 40)
print(result_swapped)
```

**Output:**

```
# The output will vary due to the random nature of the function.
# A possible output for the first call:
[15, 11, 20, 18, 12]

# A possible output for the second call (range is corrected to 40-50):
[43, 49, 41]
```

***
## FunctionDef fibonacci(n)
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth Fibonacci number using an iterative approach.

## parameters

- `n` (int): The 0-indexed index of the Fibonacci number to be computed.

## Description

This function calculates a number in the Fibonacci sequence based on its index `n`. The Fibonacci sequence starts with 0 and 1, and each subsequent number is the sum of the two preceding ones (e.g., 0, 1, 1, 2, 3, 5, 8...).

The function first validates the input `n`. If `n` is a negative number, it raises a `ValueError` because the Fibonacci sequence is not defined for negative indices.

It initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the sequence.

The function then enters a `for` loop that iterates `n` times. In each iteration, it performs a tuple assignment: `a, b = b, a + b`. This simultaneously updates `a` to the current value of `b` and `b` to the sum of the old `a` and `b`. This process effectively steps through the Fibonacci sequence.

After the loop completes, the variable `a` holds the nth Fibonacci number, which is then returned. For `n=0`, the loop does not run, and the initial value of `a` (0) is correctly returned.

```python
# Initialization
a, b = 0, 1

# For n = 3, the loop runs 3 times:
# 1. a becomes 1, b becomes 0 + 1 = 1
# 2. a becomes 1, b becomes 1 + 1 = 2
# 3. a becomes 2, b becomes 1 + 2 = 3

# The function returns a, which is 2 (the 3rd Fibonacci number is 2)
```

## Usage Notes

- The index `n` is 0-based. For example, `fibonacci(0)` returns `0`, and `fibonacci(1)` returns `1`.
- The function only accepts non-negative integers for the parameter `n`. Providing a negative integer will result in a `ValueError`.
- This iterative implementation is efficient in terms of memory usage and avoids the recursion depth limits that can be an issue with naive recursive solutions for large `n`.

**Output Example**: The function returns a single integer value. For an input of `9`, the output would look like this:
`34`

## Example

```python
# Example usage
# Calculate the 9th Fibonacci number (0-indexed)
n_index = 9
result = fibonacci(n_index)
print(f"The Fibonacci number at index {n_index} is: {result}")
```

**Output:**

```
The Fibonacci number at index 9 is: 34
```

***
## FunctionDef choose_random_item(items)
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns a single, uniformly random item from a given list of strings.

## parameters

- **`items`** (`List[str]`): A non-empty list of strings from which a random item will be selected.

## Description

This function provides a safe way to choose a random element from a list. It first performs a validation check to ensure the input list is not empty.

- The function begins by evaluating `if not items:`. This condition checks if the provided `items` list has zero elements.
- If the list is empty, the function raises a `ValueError` with the message "items must not be empty" to prevent errors in the subsequent step and to inform the user of the invalid input.
- If the list is not empty, the function proceeds to call `random.choice(items)`. This is a standard library function that takes a non-empty sequence and returns a randomly selected element. The selection is uniform, meaning every item in the list has an equal probability of being chosen.

```python
# Example of internal logic
import random

my_items = ["option A", "option B", "option C"]

# The function checks if my_items is empty (it's not)
# Then it executes the equivalent of:
selected_item = random.choice(my_items) 
# selected_item will be "option A", "option B", or "option C" with equal probability
```

## Usage Notes

- The input list `items` must not be empty. Providing an empty list will cause the function to raise a `ValueError`.
- This function relies on Python's built-in `random` module. Ensure it is imported in the scope where the function is defined.
- The function is type-hinted to accept a list of strings (`List[str]`), but the underlying `random.choice` method will work with any non-empty sequence (e.g., a tuple or a list of integers).

**Output Example**: A single string from the input list. For an input of `["red", "green", "blue"]`, a possible return value is:
`green`

## Example

```python
# Example usage
import random # This import is necessary for the function to work

# Define a list of strings
options = ["alpha", "beta", "gamma", "delta"]

# Call the function with the list
try:
    chosen_option = choose_random_item(options)
    print(f"The chosen option is: {chosen_option}")
except ValueError as e:
    print(e)

# Example with an empty list
empty_options = []
try:
    chosen_option = choose_random_item(empty_options)
    print(f"The chosen option is: {chosen_option}")
except ValueError as e:
    print(f"Error: {e}")
```

**Output:**

```
The chosen option is: gamma
Error: items must not be empty
```
(Note: The first line of the output is random and will vary with each execution.)

***
## FunctionDef shuffle_copy(items)
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a shuffled copy of a given list of integers without modifying the original list.

## parameters

- `items` (List[int]): The list of integers to be shuffled.

## Description

This function provides a safe way to shuffle a list by operating on a copy rather than the original data. The process is as follows:

1.  A shallow copy of the input `items` list is created using the `list()` constructor. This new list is assigned to the `copy` variable. This step ensures that any subsequent modifications do not affect the original list passed to the function.
2.  The `random.shuffle()` function is then called on the `copy`. This function shuffles the elements of the `copy` list in-place, rearranging them into a random order.
3.  Finally, the function returns the modified `copy`, which now contains the same elements as the original list but in a new, randomized sequence.

```python
# Internal logic breakdown
original_list = [1, 2, 3]
# 1. Create a copy
copy = list(original_list)  # copy is [1, 2, 3]
# 2. Shuffle the copy in-place
random.shuffle(copy)       # copy might become [2, 3, 1]
# 3. Return the shuffled copy
return copy
```

## Usage Notes

- The primary benefit of this function is that it is non-mutating; the original list you pass as an argument will remain unchanged.
- This function depends on Python's built-in `random` module. Ensure this module is imported in the file where `shuffle_copy` is used.
- The order of the elements in the returned list is non-deterministic and will likely be different each time the function is called.

**Output Example**: A list containing the same integers as the input `items` list, but in a random order.

```
[4, 1, 5, 3, 2]
```

## Example

```python
import random
from typing import List

def shuffle_copy(items: List[int]) -> List[int]:
    """Return a shuffled copy of the given list without mutating the input.

    Parameters:
        items: A list of integers.

    Returns:
        A new list containing the same integers in random order.
    """
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_numbers = [1, 2, 3, 4, 5]
shuffled_numbers = shuffle_copy(original_numbers)

print(f"Original List: {original_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")
```

**Output:**

```
Original List: [1, 2, 3, 4, 5]
Shuffled Copy: [3, 5, 1, 2, 4]
```

***
