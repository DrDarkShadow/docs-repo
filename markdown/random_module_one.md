## FunctionDef num(a, b)
# Function: def num(a, b)

## Overview

The `num` function calculates and returns the sum of two provided numbers.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `a` | int / float | The first number to be used in the addition. |
| `b` | int / float | The second number to be used in the addition. |

## Description

This function performs a basic arithmetic addition. It accepts two arguments, `a` and `b`, and computes their sum using the `+` operator. The resulting value is then returned by the function. The function is straightforward and does not contain any complex logic or error handling.

For example, if `a` is `5` and `b` is `10`, the function will compute `5 + 10` and return `15`.

```python
# The core logic is a simple return statement
return a + b
```

## Usage Notes

Important points to consider when using this function:

- The function is designed for numeric types like integers (`int`) and floating-point numbers (`float`).
- If strings are passed as arguments, the function will perform string concatenation instead of arithmetic addition (e.g., `num("hello", "world")` would return `"helloworld"`).
- The order of the parameters `a` and `b` does not affect the result due to the commutative property of addition.

**Output Example**: A single numeric value representing the sum.

## Example

```python
# Example usage with integers
result_int = num(15, 25)
print(result_int)

# Example usage with floating-point numbers
result_float = num(7.5, 2.2)
print(result_float)
```

**Output:**

```
40
9.7
```

***
## FunctionDef generate_random_integers
# Function: generate_random_integers(count: int, start: int = 0, end: int = 100) -> List[int]

## Overview

The `generate_random_integers` function creates and returns a list of a specified number of pseudo-random integers within a given inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | int | The total number of random integers to generate. This value must be non-negative. |
| `start` | int | The inclusive lower bound of the random number range. Defaults to `0`. |
| `end` | int | The inclusive upper bound of the random number range. Defaults to `100`. |

## Description

This function provides a straightforward way to generate a list of random integers. The logic proceeds as follows:

1.  **Input Validation**: The function first checks if the `count` parameter is a non-negative number. If `count` is less than zero, it raises a `ValueError` because it's impossible to generate a negative number of integers.

2.  **Range Correction**: It then compares the `start` and `end` parameters. If `start` is found to be greater than `end`, the function automatically swaps their values. This ensures that `random.randint` receives a valid range (`start` <= `end`) without requiring the user to order the boundary parameters correctly.

3.  **Random Number Generation**: Using a list comprehension, the function calls `random.randint(start, end)` for a total of `count` times. The `random.randint` method generates an integer `x` such that `start <= x <= end`. Each generated integer is collected into a list.

4.  **Return Value**: Finally, the function returns the newly created list containing `count` pseudo-random integers.

```python
# Internal logic for generating the list
return [random.randint(start, end) for _ in range(count)]
```

## Usage Notes

- This function depends on Python's `random` module. Ensure it is imported before calling the function.
- The function gracefully handles cases where `start > end` by swapping the values internally, so the order of these two parameters does not affect the outcome.
- An attempt to generate a negative number of integers (e.g., `count=-1`) will result in a `ValueError`.
- The range defined by `start` and `end` is inclusive, meaning both `start` and `end` are potential values in the output list.

**Output Example**: The function returns a list of integers. For an input of `count=5, start=1, end=10`, a possible output would be:
`[3, 1, 9, 7, 4]`

## Example

```python
import random # This import is necessary for the function to work

# Example: Generate 5 random integers between 50 and 60 (inclusive)
random_list = generate_random_integers(count=5, start=50, end=60)
print(random_list)

# Example: Using default start (0) and end (100) values
random_list_default = generate_random_integers(count=3)
print(random_list_default)
```

**Output:**

```
# The actual numbers will vary with each execution due to their random nature.
[58, 52, 60, 55, 51]
[8, 92, 43]
```

***
## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str]) -> str

## Overview

The `choose_random_item` function selects and returns a single item chosen uniformly at random from a provided list of strings.

## Parameters

*   **`items`** (`List[str]`): A non-empty list of strings from which one item will be randomly selected.

## Description

This function provides a safe way to select a random element from a list. It begins by performing a validation check on the input list `items`. If the list is empty (`if not items`), the function immediately raises a `ValueError` to prevent errors that would occur from attempting to choose an item from an empty sequence.

If the list is not empty, the function proceeds to use `random.choice(items)`. This is a standard library function from Python's `random` module that takes a non-empty sequence and returns a randomly selected element. The selection is uniform, meaning every item in the list has an equal probability of being chosen.

## Usage Notes

*   The function requires the `random` module to be imported to work correctly.
*   Passing an empty list to this function will result in a `ValueError`. Ensure the list contains at least one element before calling.
*   The function is designed for a `List[str]`, but `random.choice` can work with any non-empty sequence (like tuples or other list types).

**Output Example**: A single string from the input list.

```
"apple"
```

## Example

```python
import random
from typing import List

def choose_random_item(items: List[str]) -> str:
    """Choose a single random item from a non-empty sequence.

    Parameters:
        items: A list of strings to choose from.

    Returns:
        A single string chosen uniformly at random.
    """
    if not items:
        raise ValueError("items must not be empty")
    return random.choice(items)

# Example usage
fruit_list = ["apple", "banana", "cherry", "date"]
random_fruit = choose_random_item(fruit_list)
print(f"The chosen fruit is: {random_fruit}")

# Example of error handling
try:
    empty_list = []
    choose_random_item(empty_list)
except ValueError as e:
    print(f"Error: {e}")
```

**Output:**

The output for the successful case will vary with each execution.

```
The chosen fruit is: cherry
Error: items must not be empty
```

***
## FunctionDef shuffle_copy
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a new, randomly shuffled copy of a given list without modifying the original list.

## parameters

- `items` (`List[int]`): The list of integers to be shuffled.

## Description

This function provides a safe way to shuffle a list by ensuring the original data structure remains unchanged. The process is straightforward:

1.  A shallow copy of the input `items` list is created using `copy = list(items)`. This is the key step that prevents mutation of the original list.
2.  The `random.shuffle()` function is then called on this new `copy`. This function shuffles the elements of the list in-place, rearranging them into a random order.
3.  Finally, the shuffled `copy` is returned to the caller, while the original `items` list is left in its initial state.

```python
# The function creates a copy first
copy = list(items)
# Then shuffles the copy in-place
random.shuffle(copy)
# Finally, it returns the shuffled copy
return copy
```

## Usage Notes

- **Non-mutating:** The primary benefit of this function is that it does not alter the original list provided as an argument. This prevents unintended side effects in your code.
- **Dependency:** This function relies on Python's built-in `random` module. You must ensure `import random` is present in your script for the function to work.
- **Type Flexibility:** While the type hint specifies `List[int]`, the function's logic will work correctly with lists containing other data types, such as strings, floats, or objects.

**Output Example**: A new list containing the same elements as the input list, but in a randomized order. For an input of `[1, 2, 3, 4, 5]`, a possible output could be:

```
[4, 1, 5, 2, 3]
```

## Example

The following example demonstrates how to use `shuffle_copy` and confirms that the original list is not modified.

```python
import random
from typing import List

# Assume the function is defined in the current scope
def shuffle_copy(items: List[int]) -> List[int]:
    """Return a shuffled copy of the given list without mutating the input."""
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_numbers = [1, 2, 3, 4, 5]
shuffled_numbers = shuffle_copy(original_numbers)

print(f"Original List (unchanged): {original_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")

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

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative method.

## parameters

- `n` (int): The 0-indexed position in the Fibonacci sequence for which to find the value.

## Description

This function provides an efficient, iterative way to calculate a Fibonacci number.

The function begins by validating the input `n`. If `n` is a negative number, it raises a `ValueError` because the Fibonacci sequence is not defined for negative indices.

It then initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the sequence, F₀ and F₁.

The core logic resides in a `for` loop that iterates `n` times. In each iteration, the values of `a` and `b` are updated simultaneously. The current value of `b` is assigned to `a`, and the sum of the old `a` and `b` is assigned to the new `b`. This process effectively moves one step forward in the sequence:
- Iteration 1: `a` becomes 1, `b` becomes 1 (0+1)
- Iteration 2: `a` becomes 1, `b` becomes 2 (1+1)
- Iteration 3: `a` becomes 2, `b` becomes 3 (1+2)
- and so on...

After the loop completes, the variable `a` holds the nth Fibonacci number, which is then returned. For an input of `n=0`, the loop does not execute, and the initial value of `a` (0) is correctly returned.

## Usage Notes

- The input `n` must be a non-negative integer. Providing a negative integer will result in a `ValueError`.
- This function uses an iterative approach, which is memory-efficient and avoids the recursion depth limits that can affect recursive solutions for large values of `n`.
- The sequence is 0-indexed, meaning `fibonacci(0)` returns the first number (0), `fibonacci(1)` returns the second (1), and so on.

**Output Example**:
```
13
```

## Example

```python
# Example usage: Calculate the 10th Fibonacci number (0-indexed)
index = 10
result = fibonacci(index)
print(f"The Fibonacci number at index {index} is: {result}")

# Example with an edge case
index_zero = 0
result_zero = fibonacci(index_zero)
print(f"The Fibonacci number at index {index_zero} is: {result_zero}")
```

**Output:**

```
The Fibonacci number at index 10 is: 55
The Fibonacci number at index 0 is: 0
```

***
## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str]) -> str

## Overview

The `choose_random_item` function selects and returns a single, random element from a provided list of strings.

## parameters

- `items` (`List[str]`): A list of strings from which a random item will be selected. This list must not be empty.

## Description

This function provides a straightforward way to get a random element from a sequence. The logic proceeds in two steps:

First, it performs a validation check on the input `items` list. The condition `if not items:` evaluates to `True` if the list is empty. In this case, the function raises a `ValueError` to prevent errors in the random selection logic and to enforce the requirement that the input sequence must be non-empty.

```python
# This will raise a ValueError
choose_random_item([]) 
```

If the `items` list is not empty, the function uses `random.choice(items)` to perform the selection. The `random.choice()` method, from Python's standard `random` library, picks a single item from the list with uniform probability, meaning every item has an equal chance of being chosen. The selected string is then returned as the result.

## Usage Notes

- The input list `items` cannot be empty. Passing an empty list will result in a `ValueError`.
- The function relies on Python's built-in `random` module. Ensure this module is imported and available in the execution environment.
- The selection is uniformly random, meaning every string in the `items` list has an equal probability of being returned.

**Output Example**: A single string that was present in the input `items` list. For example, `"apple"`.

## Example

```python
import random

# The function relies on the 'random' module.
# The definition of choose_random_item is assumed to be in the same scope.
def choose_random_item(items: list[str]) -> str:
    if not items:
        raise ValueError("items must not be empty")
    return random.choice(items)

# Example usage
options = ["apple", "banana", "cherry", "date"]
random_fruit = choose_random_item(options)
print(random_fruit)
```

**Output:**

```
cherry
```
*(Note: The actual output will vary with each execution as it is chosen randomly.)*

***
## FunctionDef shuffle_copy
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function creates and returns a new list containing the elements of the input list in a randomized order, leaving the original list unchanged.

## parameters

- **`items`** (`List[int]`): A list of integers to be copied and shuffled.

## Description

This function provides a safe way to shuffle a list without altering the original data structure. The logic proceeds in three steps:

1.  First, a shallow copy of the input `items` list is created using the `list()` constructor. This ensures that any subsequent modifications do not affect the original list provided by the user.
    ```python
    copy = list(items)
    ```
2.  Next, the `random.shuffle()` function is called on the newly created `copy`. The `random.shuffle()` method shuffles the elements of a list "in-place," meaning it directly modifies the `copy` list by rearranging its items into a random order.

3.  Finally, the function returns the shuffled `copy`. The original `items` list remains untouched throughout the process.

## Usage Notes

Important points to consider when using this function:

- **Immutability of Input**: The primary feature of this function is that it is non-mutating. The original list passed as the `items` parameter will not be altered.
- **Random Module Dependency**: This function relies on the `random.shuffle()` method, which is part of Python's standard `random` module. You must ensure that the `random` module is imported into your script before calling this function.
- **Shallow Copy**: The function creates a shallow copy of the list. This is perfectly suitable for a list of integers. However, if the list were to contain mutable objects (like other lists or dictionaries), the nested objects themselves would not be duplicated.

**Output Example**: A possible return value for an input of `[1, 2, 3, 4, 5]` could be `[3, 5, 1, 4, 2]`. The exact order will be random and will vary with each execution.

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
original_numbers = [1, 2, 3, 4, 5, 6, 7]
shuffled_numbers = shuffle_copy(original_numbers)

print(f"Original List (Unchanged): {original_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")

# Another call will produce a different random order
another_shuffled_copy = shuffle_copy(original_numbers)
print(f"Another Shuffled Copy: {another_shuffled_copy}")
```

**Output:**

```
Original List (Unchanged): [1, 2, 3, 4, 5, 6, 7]
Shuffled Copy: [4, 1, 7, 3, 5, 2, 6]
Another Shuffled Copy: [2, 7, 5, 1, 4, 6, 3]
```
*(Note: The actual order of elements in the shuffled lists will vary each time the code is run.)*

***
