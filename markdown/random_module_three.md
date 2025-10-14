## FunctionDef fibonacci(n)
# fibonacci

## Overview

The `fibonacci` function computes the nth Fibonacci number using an iterative approach.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `n` | `int` | The 0-indexed position in the Fibonacci sequence for which to find the number. This must be a non-negative integer. |

## Description

The `fibonacci` function provides an efficient, iterative method to calculate a number in the Fibonacci sequence. The sequence starts with 0 and 1, and each subsequent number is the sum of the two preceding ones (0, 1, 1, 2, 3, 5, ...).

The function's logic proceeds as follows:
1.  **Input Validation**: It first checks if the input `n` is a negative number. Since the Fibonacci sequence is defined for non-negative indices, the function raises a `ValueError` if `n` is less than 0.
2.  **Initialization**: Two variables, `a` and `b`, are initialized to `0` and `1` respectively. These represent the first two numbers in the sequence, F₀ and F₁.
3.  **Iteration**: The function then enters a `for` loop that iterates `n` times. This loop is the core of the calculation.
4.  **Calculation**: Inside the loop, the values of `a` and `b` are updated in each iteration. The statement `a, b = b, a + b` simultaneously assigns the current value of `b` to `a` and the sum of `a` and `b` to `b`. This effectively advances the sequence by one step.
5.  **Return Value**: After the loop completes, the variable `a` holds the nth Fibonacci number. For `n=0`, the loop does not run, and the initial value of `a` (0) is correctly returned. For any `n > 0`, the loop runs `n` times, and `a` will hold the desired value.

This iterative approach is memory-efficient and avoids the performance issues of deep recursion found in naive recursive implementations, making it suitable for calculating larger Fibonacci numbers.

## Usage Notes

- The input `n` must be a non-negative integer. Providing a negative number will result in a `ValueError`.
- The function is 0-indexed, meaning `fibonacci(0)` returns the first number in the sequence, which is `0`.
- The iterative implementation is highly efficient and is preferred over simple recursive solutions for performance reasons, as it avoids redundant calculations and has a linear time complexity O(n).

**Output Example**:
The function returns a single integer value. For an input of `10`, the output would look like this:
```
55
```

## Example

```python
# Example usage of the fibonacci function

# Calculate the 10th Fibonacci number (0-indexed)
n_value = 10
result = fibonacci(n_value)
print(f"The Fibonacci number at index {n_value} is: {result}")

# Calculate the 0th Fibonacci number
result_zero = fibonacci(0)
print(f"The Fibonacci number at index 0 is: {result_zero}")

# Calculate the 1st Fibonacci number
result_one = fibonacci(1)
print(f"The Fibonacci number at index 1 is: {result_one}")
```

**Output:**
```
The Fibonacci number at index 10 is: 55
The Fibonacci number at index 0 is: 0
The Fibonacci number at index 1 is: 1
```

---
## FunctionDef invert_dictionary(mapping)
# invert_dictionary

## Overview

The `invert_dictionary` function inverts a dictionary by swapping its keys and values, provided that all values in the original dictionary are unique.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `mapping` | `Dict[str, int]` | A dictionary mapping string keys to integer values. All values in this dictionary must be unique. |

## Description

This function provides a safe way to invert a dictionary where string keys are mapped to integer values. The core logic involves two main steps:

1.  **Uniqueness Validation**: Before performing the inversion, the function first validates that all values in the input `mapping` are unique. It achieves this by comparing the number of values (`len(mapping.values())`) with the number of unique values, which is determined by converting the values to a `set` and checking its length (`len(set(mapping.values()))`). If these counts do not match, it indicates that duplicate values are present. In this case, the function raises a `ValueError` to prevent data loss, as multiple original keys would otherwise map to the same new key during inversion.

2.  **Inversion**: If all values are confirmed to be unique, the function proceeds to create a new dictionary. It uses a dictionary comprehension, `{value: key for key, value in mapping.items()}`, to iterate through the key-value pairs of the original `mapping`. For each pair, it creates a new entry in the new dictionary where the original `value` becomes the key and the original `key` becomes the value.

The resulting inverted dictionary, which maps integers to strings, is then returned.

## Usage Notes

- This function strictly requires that all values in the input `mapping` dictionary be unique. If duplicate values are found, a `ValueError` will be raised.
- The original dictionary passed as the `mapping` argument is not modified. The function creates and returns a new, inverted dictionary.

**Output Example**: A dictionary where the keys are integers and the values are strings.
```python
{
    1: "key_one",
    2: "key_two"
}
```

## Example

```python
# Example usage with a valid dictionary
original_dict = {'alpha': 10, 'beta': 20, 'gamma': 30}
inverted_dict = invert_dictionary(original_dict)
print(inverted_dict)

# The following example would raise an error because the value '10' is duplicated.
# To handle this, you would use a try-except block.
#
# try:
#     invalid_dict = {'alpha': 10, 'beta': 20, 'delta': 10}
#     invert_dictionary(invalid_dict)
# except ValueError as e:
#     print(e)
#
# Output of the error case:
# Values must be unique to invert dictionary
```

**Output:**
```
{10: 'alpha', 20: 'beta', 30: 'gamma'}
```

---
## FunctionDef is_palindrome(text)
# is_palindrome

## Overview

The `is_palindrome` function checks if a given string is a palindrome, ignoring letter casing and whitespace characters.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `text` | `str` | The input string to be checked. |

## Description

The `is_palindrome` function determines if a string reads the same forwards and backwards by following a two-step process: normalization and comparison.

First, the function normalizes the input `text`. It iterates through each character of the string, discards any whitespace characters (like spaces, tabs, or newlines) using `ch.isspace()`, and converts all remaining characters to lowercase using `ch.lower()`. These processed characters are then joined together to form a new, "normalized" string.

```python
normalized = ''.join(ch.lower() for ch in text if not ch.isspace())
```

Second, the function compares the `normalized` string with its reversed version. The reversal is efficiently achieved using Python's slice notation `[::-1]`. If the normalized string is identical to its reverse, the function returns `True`, indicating that the original text is a palindrome. Otherwise, it returns `False`.

```python
return normalized == normalized[::-1]
```

## Usage Notes

- The function is **case-insensitive**. For example, "Racecar" is treated the same as "racecar".
- All whitespace characters are ignored. This includes spaces, tabs (`\t`), and newlines (`\n`).
- Punctuation, numbers, and other symbols are **not** ignored and are included in the palindrome check. For instance, `is_palindrome("madam.")` will return `False` because the normalized string "madam." is not identical to its reverse ".madam".

**Output Example**: The function returns a boolean value.
```
True
```

## Example

```python
# Example 1: A classic palindrome with mixed casing and spaces
result1 = is_palindrome("A man a plan a canal Panama")
print(f"'A man a plan a canal Panama' is a palindrome: {result1}")

# Example 2: A simple palindrome
result2 = is_palindrome("Racecar")
print(f"'Racecar' is a palindrome: {result2}")

# Example 3: A string that is not a palindrome
result3 = is_palindrome("hello world")
print(f"'hello world' is a palindrome: {result3}")

# Example 4: A string with punctuation that makes it not a palindrome
result4 = is_palindrome("Was it a car or a cat I saw?")
print(f"'Was it a car or a cat I saw?' is a palindrome: {result4}")
```

**Output:**
```
'A man a plan a canal Panama' is a palindrome: True
'Racecar' is a palindrome: True
'hello world' is a palindrome: False
'Was it a car or a cat I saw?' is a palindrome: False
```

---
