## FunctionDef fibonacci(n)
# Function: fibonacci(n: int)

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative approach.

## parameters

- `n`: `int`
  - The 0-indexed position in the Fibonacci sequence for which to find the value.

## Description

This function provides a memory-efficient way to calculate Fibonacci numbers. The logic begins by validating the input `n`. If `n` is a negative number, a `ValueError` is raised, as the Fibonacci sequence is not defined for negative indices.

The function initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the sequence, F(0) and F(1).

It then enters a `for` loop that iterates `n` times. Inside the loop, the core logic `a, b = b, a + b` is executed. This is a tuple assignment that simultaneously updates the values:
1. The current value of `b` is assigned to `a`.
2. The sum of the old `a` and `b` is assigned to `b`.

This process effectively shifts the sequence forward one step in each iteration. For example, if `a=3` and `b=5`, the next iteration will set `a=5` and `b=8`. After the loop completes `n` iterations, the variable `a` will hold the value of the nth Fibonacci number, which is then returned.

```python
# For n = 5, the loop runs 5 times:
# Initial: a = 0, b = 1
# 1. a = 1, b = 1 (0 + 1)
# 2. a = 1, b = 2 (1 + 1)
# 3. a = 2, b = 3 (1 + 2)
# 4. a = 3, b = 5 (2 + 3)
# 5. a = 5, b = 8 (3 + 5)
# The function returns a, which is 5.
```

## Usage Notes

- The input `n` must be a non-negative integer. The function will raise a `ValueError` for negative inputs.
- The function uses a 0-indexed sequence, meaning `fibonacci(0)` returns the first number of the sequence, which is `0`.
- This iterative implementation is efficient in terms of memory and performance for large values of `n` compared to a naive recursive approach, as it avoids redundant calculations and deep recursion stacks.

**Output Example**: A single integer representing the calculated Fibonacci number.
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
## FunctionDef invert_dictionary(mapping)
# Function: invert_dictionary(mapping: Dict[str, int])

## Overview

The `invert_dictionary` function swaps the keys and values of a given dictionary, creating a new dictionary where the original values become keys and the original keys become values.

## parameters

- **`mapping`** (`Dict[str, int]`): A dictionary mapping string keys to integer values. It is critical that all values in this dictionary are unique for the inversion to be successful.

## Description

This function provides a safe way to invert a dictionary by first ensuring the integrity of the operation.

The function's logic proceeds as follows:
1.  **Uniqueness Validation**: It first checks if all values in the input `mapping` are unique. This is accomplished by comparing the total number of values (`len(mapping.values())`) with the number of unique values, which is found by converting the values to a set and checking its length (`len(set(mapping.values()))`).
2.  **Error Handling**: If the counts do not match, it signifies that duplicate values exist. In this case, a `ValueError` is raised with the message "Values must be unique to invert dictionary". This prevents an ambiguous or lossy inversion where multiple keys would map to the same new key.
3.  **Inversion**: If all values are unique, the function uses a dictionary comprehension, `{value: key for key, value in mapping.items()}`, to iterate over each key-value pair in the original `mapping`. It constructs and returns a new dictionary where each original `value` is now a key, and its corresponding `key` is the value.

## Usage Notes

Important points to consider when using this function:

- The primary requirement is that the values of the input `mapping` dictionary must be unique. The function will raise a `ValueError` if this condition is not met.
- The function is non-destructive; it returns a new inverted dictionary and does not modify the original dictionary provided in the `mapping` parameter.
- The type hints specify a `Dict[str, int]` input and `Dict[int, str]` output, but the function will work with any dictionary where both keys and values are hashable types.

**Output Example**: A dictionary where the keys are integers and the values are strings.
```
{10: 'apple', 20: 'banana', 30: 'cherry'}
```

## Example

```python
# Example usage of a valid dictionary
from typing import Dict

def invert_dictionary(mapping: Dict[str, int]) -> Dict[int, str]:
    """Invert a dictionary with unique values.

    Parameters:
        mapping: Dictionary mapping strings to integers with unique values.

    Returns:
        A new dictionary mapping integers to strings.
    """
    if len(mapping.values()) != len(set(mapping.values())):
        raise ValueError("Values must be unique to invert dictionary")
    return {value: key for key, value in mapping.items()}

original_dict = {'user_one': 101, 'user_two': 202, 'user_three': 303}
inverted_dict = invert_dictionary(original_dict)
print(f"Original Dictionary: {original_dict}")
print(f"Inverted Dictionary: {inverted_dict}")

# Example that raises a ValueError
try:
    invalid_dict = {'a': 1, 'b': 2, 'c': 1}
    invert_dictionary(invalid_dict)
except ValueError as e:
    print(f"\nError with invalid dictionary: {e}")
```

**Output:**

```
Original Dictionary: {'user_one': 101, 'user_two': 202, 'user_three': 303}
Inverted Dictionary: {101: 'user_one', 202: 'user_two', 303: 'user_three'}

Error with invalid dictionary: Values must be unique to invert dictionary
```

***
## FunctionDef is_palindrome(text)
# Function: is_palindrome(text: str)

## Overview

The `is_palindrome` function determines if a given string is a palindrome, meaning it reads the same forwards and backwards, after ignoring letter casing and all whitespace characters.

## parameters

- **`text`** (str): The input string to be checked for the palindrome property.

## Description

This function provides a straightforward way to check for palindromes by first normalizing the input string and then comparing it to its reverse.

The core logic operates in two main steps:

1.  **Normalization**: The function first creates a "normalized" version of the input `text`. It iterates through every character (`ch`) in the string. Using a generator expression, it filters out any character that is a whitespace character (like spaces, tabs, or newlines) via the `ch.isspace()` method. For all remaining characters, it converts them to lowercase using `ch.lower()`. The `''.join()` method then combines these filtered, lowercase characters into a new string, `normalized`.

2.  **Comparison**: The function then compares the `normalized` string with its reversed version. The slice notation `normalized[::-1]` efficiently creates a reversed copy of the string. If the `normalized` string is identical to its reversed counterpart, the expression evaluates to `True`, indicating a palindrome. Otherwise, it evaluates to `False`.

For instance, if the input `text` is `"Taco Cat"`, the `normalized` string becomes `"tacocat"`. The function then checks if `"tacocat"` is equal to `"tacocat"[::-1]`, which is also `"tacocat"`. Since they are equal, the function returns `True`.

## Usage Notes

- The function is **case-insensitive**. For example, `is_palindrome("Racecar")` and `is_palindrome("racecar")` will both return `True`.
- All whitespace characters (spaces, tabs, newlines, etc.) are ignored during the check.
- Punctuation, numbers, and other symbols are **not** ignored and are included in the palindrome check. For example, `is_palindrome("A man, a plan, a canal: Panama")` will return `False` because the commas and colon are part of the comparison.

**Output Example**: The function returns a boolean value.

```
True
```

## Example

```python
# Example usage with mixed casing and spaces
text_to_check = "No lemon no melon"
result = is_palindrome(text_to_check)
print(f"Is '{text_to_check}' a palindrome? {result}")

# Example with a non-palindrome
another_text = "hello world"
result_two = is_palindrome(another_text)
print(f"Is '{another_text}' a palindrome? {result_two}")
```

**Output:**

```
Is 'No lemon no melon' a palindrome? True
Is 'hello world' a palindrome? False
```

***
