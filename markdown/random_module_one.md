## FunctionDef num(a, b)
# Function: def num(a, b)

## Overview

The `num` function calculates and returns the sum of two input numbers.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | int / float | The first number to be added. |
| `b` | int / float | The second number to be added. |

## Description

This function provides a straightforward way to perform addition. It accepts two arguments, `a` and `b`, which are expected to be numerical values (integers or floating-point numbers). The core logic of the function is the addition operator (`+`), which is used to sum `a` and `b`. The resulting sum is then returned by the function.

For example, if `a` is `5` and `b` is `10`, the function will compute `5 + 10` and return `15`.

```python
# The function returns the result of a + b
return a+b
```

## Usage Notes

- This function is designed for numeric types. If strings are passed as arguments, the function will perform string concatenation instead of mathematical addition (e.g., `num("hello", "world")` would return `"helloworld"`).
- Providing incompatible types (e.g., an integer and a string) will raise a `TypeError`.

**Output Example**: A numeric value representing the sum.

```
15
```

## Example

```python
# Example usage with integers
result_int = num(5, 10)
print(result_int)

# Example usage with floating-point numbers
result_float = num(3.14, 2.71)
print(result_float)
```

**Output:**

```
15
5.85
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

1.  **Input Validation**: The function first checks if the `count` parameter is a negative number. If `count` is less than zero, it is an invalid input for generating a list, so the function raises a `ValueError` with the message "count must be non-negative".

2.  **Range Correction**: It then compares the `start` and `end` parameters. If `start` is found to be greater than `end`, the function automatically swaps their values. This ensures that the range is always valid for the `random.randint` method, which requires the lower bound to be less than or equal to the upper bound.

3.  **List Generation**: Using a list comprehension, the function iterates `count` times. In each iteration, it calls `random.randint(start, end)` to produce a single integer uniformly sampled from the inclusive range `[start, end]`. These integers are collected into a list, which is the final return value.

```python
# Internal logic for generating the list
return [random.randint(start, end) for _ in range(count)]
```

## Usage Notes

- This function requires the `random` module to be imported in your script.
- Providing a negative value for the `count` parameter will result in a `ValueError`.
- The function is flexible with range definition; if `start` is greater than `end`, the values will be swapped internally to prevent errors.
- The returned integers are sampled uniformly from the inclusive range `[start, end]`, meaning both `start` and `end` can appear in the output.

**Output Example**: A list of integers.

```
[45, 8, 99, 23, 67]
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

(Note: The actual output will vary with each execution due to the random nature of the function.)
```
[12, 18, 10, 15, 20]
```

***
## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns a single random string from a non-empty list of strings.

## parameters

- `items` (List[str]): A list of strings from which one item will be chosen randomly. This list must not be empty.

## Description

This function provides a safe way to choose a random element from a list. The logic proceeds as follows:

1.  The function first performs a validation check on the input `items` list using the condition `if not items:`. This check evaluates to `True` if the list is empty.
2.  If the list is empty, a `ValueError` is raised with the message "items must not be empty". This prevents errors in the subsequent step and clearly informs the user about the invalid input.
3.  If the list is not empty, the function calls `random.choice(items)`. This standard library function takes a non-empty sequence and returns a single item chosen with uniform probability, meaning every item has an equal chance of being selected.
4.  The randomly selected string is then returned as the result of the function.

```python
# Conceptual example of the function's core operation
import random

items_list = ["option A", "option B", "option C"]
if not items_list:
    raise ValueError("items must not be empty")
else:
    selected_item = random.choice(items_list)
    # selected_item will be one of "option A", "option B", or "option C"
```

## Usage Notes

- The input list provided to the `items` parameter cannot be empty. An empty list will cause the function to raise a `ValueError`.
- This function depends on Python's `random` module. Ensure that `import random` is present at the top of your script.
- The selection is uniformly random, meaning each item in the list has an equal probability of being chosen.

**Output Example**: A single string element from the input list.

```
"banana"
```

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
available_fruits = ["apple", "banana", "cherry", "date"]
random_fruit = choose_random_item(available_fruits)
print(random_fruit)
```

**Output:**

```
cherry
```
*(Note: The output is random and will be one of the items from the list on each execution.)*

***
## FunctionDef shuffle_copy
# Function: shuffle_copy

## Overview

The `shuffle_copy` function returns a new, randomly shuffled copy of a given list without altering the original list.

## parameters

- `items` (`List[int]`): The input list of integers that will be copied and shuffled.

## Description

This function provides a non-mutating way to shuffle a list, ensuring that the original data structure passed as an argument remains unchanged.

The logic proceeds in three steps:
1.  A shallow copy of the input `items` list is created using `copy = list(items)`. This is a crucial step that isolates the shuffling operation from the original list.
2.  The `random.shuffle()` function is then called on this `copy`. The `random.shuffle()` method shuffles the elements of a list *in-place*, meaning it modifies the `copy` directly.
3.  Finally, the function returns the `copy`, which now contains the same elements as the original `items` list but in a new, random order.

```python
# Internal logic
copy = list(items)
random.shuffle(copy)
return copy
```

## Usage Notes

- The primary benefit of this function is that it is non-destructive; the original input list is not modified.
- This function depends on Python's built-in `random` module. Ensure `import random` is present at the top of the file where this function is used.
- While the type hint specifies `List[int]`, the function's logic will correctly shuffle a list containing elements of any data type (e.g., strings, floats, or other objects).

**Output Example**: A new list with the same elements as the input list, but in a random order.
```
[5, 1, 4, 2, 3]
```

## Example

```python
import random
from typing import List

# The function must be defined or imported to be used
def shuffle_copy(items: List[int]) -> List[int]:
    """Return a shuffled copy of the given list without mutating the input."""
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_list = [1, 2, 3, 4, 5]
shuffled_list = shuffle_copy(original_list)

print(f"Original List (unchanged): {original_list}")
print(f"Shuffled Copy: {shuffled_list}")

```

**Output:**

```
Original List (unchanged): [1, 2, 3, 4, 5]
Shuffled Copy: [3, 5, 1, 2, 4]
# Note: The order of elements in the shuffled copy will be random on each execution.
```

***
## FunctionDef fibonacci
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative approach.

## parameters

*   `n`: (Type: `int`) The 0-indexed position of the desired Fibonacci number in the sequence.

## Description

This function provides a memory-efficient way to calculate a Fibonacci number. The logic proceeds as follows:

1.  **Input Validation**: The function first checks if the input `n` is a non-negative integer. If `n` is less than 0, it raises a `ValueError`, as the Fibonacci sequence is not defined for negative indices.

2.  **Initialization**: Two variables, `a` and `b`, are initialized to `0` and `1` respectively. These represent the first two numbers in the Fibonacci sequence (F₀ and F₁).

    ```python
    a, b = 0, 1
    ```

3.  **Iteration**: The function iterates `n` times using a `for` loop. In each iteration, it calculates the next number in the sequence.

4.  **Sequence Calculation**: Inside the loop, the values of `a` and `b` are simultaneously updated. The current value of `b` is assigned to `a`, and the sum of the old `a` and `b` is assigned to `b`. This tuple unpacking (`a, b = b, a + b`) elegantly advances the sequence one step at a time.

5.  **Return Value**: After the loop completes, the variable `a` holds the value of the nth Fibonacci number. If `n` is `0`, the loop does not run, and the initial value of `a` (`0`) is correctly returned.

## Usage Notes

Important points to consider when using this function:

- The index `n` is 0-based. For example, `fibonacci(0)` returns the first number (0), and `fibonacci(1)` returns the second number (1).
- The function will raise a `ValueError` if a negative integer is provided as an argument.
- This iterative implementation is efficient in terms of memory and performance for large values of `n` compared to a naive recursive solution.

**Output Example**: The function returns a single integer value.
`55`

## Example

```python
# Example usage
# Calculate the 10th Fibonacci number (0-indexed)
fib_number = fibonacci(10)
print(fib_number)
```

**Output:**

```
55
```

***
