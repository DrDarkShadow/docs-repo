## FunctionDef fibonacci(n)
# Function: fibonacci(n: int) -> int

## Overview

The `fibonacci` function computes the nth number in the Fibonacci sequence using an iterative approach.

## parameters

- **`n`** (int): The 0-indexed position in the Fibonacci sequence for which to compute the value.

## Description

This function calculates the nth Fibonacci number, where the sequence starts with 0 and 1. It operates based on an iterative algorithm, which is efficient in both time and memory.

The function first validates the input `n`. If `n` is a negative number, it raises a `ValueError` because the Fibonacci sequence is not defined for negative indices.

It initializes two variables, `a` and `b`, to `0` and `1` respectively. These represent the first two numbers in the sequence (F₀ and F₁).

The function then enters a `for` loop that iterates `n` times. In each iteration, the values of `a` and `b` are updated simultaneously. The current value of `b` is assigned to `a`, and the sum of the previous `a` and `b` is assigned to `b`. This process effectively generates the next number in the sequence in each step.

```python
# Inside the loop
a, b = b, a + b
```

After the loop completes `n` iterations, the variable `a` holds the nth Fibonacci number, which is then returned. For an input of `n=0`, the loop does not run, and the initial value of `a` (0) is correctly returned.

## Usage Notes

- The input `n` must be a non-negative integer. Providing a negative integer will result in a `ValueError`.
- The function uses a 0-indexed sequence. For example, `fibonacci(0)` returns `0`, `fibonacci(1)` returns `1`, and `fibonacci(2)` returns `1`.
- The iterative approach is memory-efficient and avoids the recursion depth limits that can be an issue with naive recursive solutions, making it suitable for calculating large Fibonacci numbers.

**Output Example**: The function returns a single integer value.

## Example

```python
# Example usage of the fibonacci function
# Calculate the 9th Fibonacci number (0-indexed)
n_value = 9
result = fibonacci(n_value)
print(f"The Fibonacci number at index {n_value} is: {result}")

# Example with a smaller index
n_value_small = 5
result_small = fibonacci(n_value_small)
print(f"The Fibonacci number at index {n_value_small} is: {result_small}")

# Example with the base case n=0
result_zero = fibonacci(0)
print(f"The Fibonacci number at index 0 is: {result_zero}")
```

**Output:**

```
The Fibonacci number at index 9 is: 34
The Fibonacci number at index 5 is: 5
The Fibonacci number at index 0 is: 0
```

***
## FunctionDef invert_dictionary(mapping)
# Function: invert_dictionary(mapping: Dict[str, int]) -> Dict[int, str]

## Overview

The `invert_dictionary` function swaps the keys and values of a given dictionary, creating a new inverted dictionary.

## parameters

- `mapping` (`Dict[str, int]`): A dictionary mapping string keys to integer values. It is critical that all values in this dictionary are unique.

## Description

This function takes a dictionary as input and returns a new dictionary where the keys and values have been swapped.

The function first validates the input `mapping` to ensure that all its values are unique. It does this by comparing the number of values (`len(mapping.values())`) with the number of unique values (`len(set(mapping.values()))`). If these counts are not equal, it indicates the presence of duplicate values, and the function raises a `ValueError` with the message "Values must be unique to invert dictionary".

If all values are unique, the function proceeds to create the inverted dictionary using a dictionary comprehension: `{value: key for key, value in mapping.items()}`. This expression iterates through each key-value pair of the input `mapping` and constructs a new dictionary where the original `value` becomes the new key and the original `key` becomes the new value.

```python
# Validation check
if len(mapping.values()) != len(set(mapping.values())):
    raise ValueError("Values must be unique to invert dictionary")
# Inversion using dictionary comprehension
return {value: key for key, value in mapping.items()}
```

## Usage Notes

- This function requires that all values in the input `mapping` dictionary be unique. Attempting to invert a dictionary with duplicate values will result in a `ValueError`.
- The original dictionary passed as the `mapping` argument is not modified.
- The keys of the returned dictionary will be the values from the input dictionary, and the values will be the keys from the input dictionary.

**Output Example**: A dictionary where the keys are integers and the values are strings.
```python
{1: 'apple', 2: 'banana', 3: 'cherry'}
```

## Example

```python
# Example 1: Successful inversion with unique values
original_dict = {'a': 1, 'b': 2, 'c': 3}
inverted_dict = invert_dictionary(original_dict)
print(f"Original: {original_dict}")
print(f"Inverted: {inverted_dict}")

# Example 2: Attempting to invert with duplicate values
try:
    non_unique_dict = {'a': 1, 'b': 2, 'c': 1}
    invert_dictionary(non_unique_dict)
except ValueError as e:
    print(f"\nError with non-unique values: {e}")
```

**Output:**

```
Original: {'a': 1, 'b': 2, 'c': 3}
Inverted: {1: 'a', 2: 'b', 3: 'c'}

Error with non-unique values: Values must be unique to invert dictionary
```

***
## FunctionDef is_palindrome(text)
# Function: is_palindrome(text: str)

## Overview

The `is_palindrome` function checks if a given string is a palindrome, meaning it reads the same forwards and backwards, while ignoring character casing and spaces.

## parameters

- `text`: `str`
  - The input string to be checked for palindrome properties.

## Description

This function determines if a string is a palindrome through a two-step process: normalization and comparison.

First, the function normalizes the input `text`. It iterates through every character of the string. For each character, it checks if it is a whitespace character using `ch.isspace()`. If it is not a whitespace character, it is converted to lowercase using `ch.lower()`. All resulting characters are then joined together to form a new string called `normalized`. This step effectively removes all spaces and makes the comparison case-insensitive.

For example, the input `"Taco cat"` would be normalized to `"tacocat"`.

```python
normalized = ''.join(ch.lower() for ch in text if not ch.isspace())
```

Second, the function compares the `normalized` string with its reverse. The reversal is achieved using the Python slice notation `[::-1]`. If the normalized string is identical to its reversed version, the function returns `True`; otherwise, it returns `False`.

```python
return normalized == normalized[::-1]
```

## Usage Notes

- **Case-Insensitive**: The comparison ignores the original casing of the letters. For example, `is_palindrome("Racecar")` and `is_palindrome("racecar")` both return `True`.
- **Whitespace Handling**: All whitespace characters (spaces, tabs, newlines, etc.) are removed before the check. `is_palindrome("taco cat")` will evaluate the string `tacocat`.
- **Punctuation and Symbols**: The function does not filter out punctuation or symbols. These characters are included in the normalized string and will affect the outcome. For instance, `is_palindrome("madam, I'm adam")` will return `False` because the normalized string `"madam,i'madam"` is not a palindrome.

**Output Example**: The function returns a boolean value.

```
True
```

## Example

```python
# Example 1: A classic palindrome with varied casing and spaces
result1 = is_palindrome("A man a plan a canal Panama")
print(f"'A man a plan a canal Panama' is a palindrome: {result1}")

# Example 2: A simple non-palindrome string
result2 = is_palindrome("Hello World")
print(f"'Hello World' is a palindrome: {result2}")

# Example 3: A palindrome with numbers (which are not affected by .lower())
result3 = is_palindrome("1 2 3 2 1")
print(f"'1 2 3 2 1' is a palindrome: {result3}")

# Example 4: A string with punctuation that fails the check
result4 = is_palindrome("Don't nod.")
print(f"'Don't nod.' is a palindrome: {result4}")
```

**Output:**

```
'A man a plan a canal Panama' is a palindrome: True
'Hello World' is a palindrome: False
'1 2 3 2 1' is a palindrome: True
'Don't nod.' is a palindrome: False
```

***
