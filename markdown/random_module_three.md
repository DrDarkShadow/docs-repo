## FunctionDef fibonacci(n)
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative approach.

## parameters

- `n` (int): The 0-indexed position in the Fibonacci sequence for which to find the value. For example, `n=0` corresponds to the first number (0), and `n=1` corresponds to the second number (1).

## Description

This function provides an efficient, iterative method to calculate a specific number in the Fibonacci sequence. The sequence starts with 0 and 1, and each subsequent number is the sum of the two preceding ones (0, 1, 1, 2, 3, 5, ...).

The function begins by validating the input `n`. If `n` is a negative number, it raises a `ValueError` because the Fibonacci sequence is not defined for negative indices.

It initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the sequence, F(0) and F(1).

The core logic resides in a `for` loop that runs `n` times. In each iteration, the values of `a` and `b` are updated using tuple assignment: `a, b = b, a + b`. This simultaneously sets `a` to the current value of `b` and `b` to the sum of the old `a` and `b`. This process effectively steps through the sequence.

After the loop completes, the variable `a` holds the nth Fibonacci number, which is then returned. For an input of `n=0`, the loop does not execute, and the initial value of `a` (0) is correctly returned.

```python
# Initialization for n=5
a, b = 0, 1

# Iteration 1: range(0)
a, b = 1, 0 + 1  # a=1, b=1
# Iteration 2: range(1)
a, b = 1, 1 + 1  # a=1, b=2
# Iteration 3: range(2)
a, b = 2, 1 + 2  # a=2, b=3
# Iteration 4: range(3)
a, b = 3, 2 + 3  # a=3, b=5
# Iteration 5: range(4)
a, b = 5, 3 + 5  # a=5, b=8

# Loop finishes, return a
return 5
```

## Usage Notes

- The function uses a 0-indexed sequence, where `fibonacci(0)` returns 0.
- Inputting a negative integer for `n` will raise a `ValueError`.
- This iterative implementation is memory-efficient compared to a naive recursive approach, as it avoids deep recursion stacks and potential stack overflow errors for large values of `n`.

**Output Example**: The function returns a single integer representing the Fibonacci number at the specified index.

## Example

```python
# Example usage
# Find the 9th Fibonacci number (0-indexed)
index = 9
fib_number = fibonacci(index)
print(f"The Fibonacci number at index {index} is: {fib_number}")

# Example with an edge case
index_zero = 0
fib_zero = fibonacci(index_zero)
print(f"The Fibonacci number at index {index_zero} is: {fib_zero}")
```

**Output:**

```
The Fibonacci number at index 9 is: 34
The Fibonacci number at index 0 is: 0
```

***
## FunctionDef invert_dictionary(mapping)
# Function: invert_dictionary(mapping: Dict[str, int])

## Overview

The `invert_dictionary` function inverts a dictionary by swapping its keys and values, returning a new dictionary.

## parameters

*   **`mapping`** (`Dict[str, int]`): The input dictionary to be inverted. It is essential that all values in this dictionary are unique.

## Description

This function provides a safe way to invert a dictionary mapping strings to integers. The core logic involves two main steps: validation and inversion.

First, it validates that the inversion is possible. In a dictionary, keys must be unique. When a dictionary is inverted, its values become the new keys. Therefore, the original values must also be unique to avoid data loss or ambiguity in the resulting dictionary. The function checks this by comparing the total number of values, `len(mapping.values())`, with the number of unique values, `len(set(mapping.values()))`. If these two counts are not equal, it signifies the presence of duplicate values, and the function raises a `ValueError`.

If all values are unique, the function proceeds to create the inverted dictionary. It uses a dictionary comprehension, `{value: key for key, value in mapping.items()}`, to iterate over each key-value pair of the input `mapping`. For each pair, it constructs a new entry in the output dictionary where the original `value` becomes the new key and the original `key` becomes the new value.

```python
# The function first checks for duplicate values
if len(mapping.values()) != len(set(mapping.values())):
    raise ValueError("Values must be unique to invert dictionary")
# If values are unique, it swaps keys and values
return {value: key for key, value in mapping.items()}
```

## Usage Notes

- The primary requirement for this function is that all values in the input `mapping` dictionary must be unique. If duplicate values are present, the function will raise a `ValueError`.
- The function is non-destructive; it does not modify the original dictionary. It creates and returns a new, inverted dictionary.
- The type hints indicate that the function is designed to convert a `Dict[str, int]` to a `Dict[int, str]`, but the logic will work for any dictionary with hashable keys and unique, hashable values.

**Output Example**: A dictionary where the original integer values are now keys and the original string keys are now values.
```
{101: 'user_one', 205: 'user_two', 310: 'user_three'}
```

## Example

```python
# Example usage with a valid dictionary
user_ids = {'user_one': 101, 'user_two': 205, 'user_three': 310}
id_to_user = invert_dictionary(user_ids)
print(id_to_user)

# Example that would raise a ValueError
try:
    invalid_ids = {'user_a': 100, 'user_b': 200, 'user_c': 100}
    invert_dictionary(invalid_ids)
except ValueError as e:
    print(f"Error: {e}")
```

**Output:**

```
{101: 'user_one', 205: 'user_two', 310: 'user_three'}
Error: Values must be unique to invert dictionary
```

***
## FunctionDef is_palindrome(text)
# Function: is_palindrome(text: str)

## Overview

The `is_palindrome` function checks if a given string is a palindrome, disregarding character casing and whitespace.

## parameters

- `text` (`str`): The input string to check.

## Description

This function determines if a string reads the same forwards and backwards by performing a normalized comparison.

The logic proceeds in two main steps:
1.  **Normalization**: The function first processes the input `text` to create a new string, `normalized`. It iterates through every character (`ch`) of the input. If a character is not a whitespace character (as determined by `ch.isspace()`), it is converted to lowercase via `ch.lower()` and included in the `normalized` string. This effectively removes all spaces and makes the comparison case-insensitive.

    ```python
    normalized = ''.join(ch.lower() for ch in text if not ch.isspace())
    ```

2.  **Comparison**: The function then compares the `normalized` string with its reverse. The reverse is created using Python's slice notation `[::-1]`. If the `normalized` string is identical to its reversed version, the function returns `True`, indicating it is a palindrome. Otherwise, it returns `False`.

    ```python
    return normalized == normalized[::-1]
    ```

## Usage Notes

- The function is case-insensitive. For example, "Racecar" and "racecar" are treated identically.
- All whitespace characters (spaces, tabs, newlines, etc.) are removed from the string before the palindrome check.
- Punctuation marks and other symbols are **not** removed and are considered part of the string during the comparison. For instance, `is_palindrome("Eva, can I see bees in a cave?")` will evaluate `ev,caniseebeesinacave?`, which is not a palindrome.

**Output Example**: The function returns a boolean value.

```
True
```

## Example

```python
# Example 1: A classic palindrome with mixed casing and spaces
result1 = is_palindrome("Taco cat")
print(f"'Taco cat' is a palindrome: {result1}")

# Example 2: A non-palindrome string
result2 = is_palindrome("Hello World")
print(f"'Hello World' is a palindrome: {result2}")

# Example 3: A string with punctuation, which results in False
result3 = is_palindrome("No 'x' in Nixon")
print(f"'No 'x' in Nixon' is a palindrome: {result3}")
```

**Output:**

```
'Taco cat' is a palindrome: True
'Hello World' is a palindrome: False
'No 'x' in Nixon' is a palindrome: False
```

***
