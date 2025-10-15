## FunctionDef count_vowels(text)
# Function: count_vowels(text: str)

## Overview

The `count_vowels` function calculates the total number of vowels found within a given input string in a case-insensitive manner.

## parameters

- **`text`** (`str`): The input string that will be scanned for vowels.

## Description

This function provides a straightforward way to count vowel occurrences in a string. Its logic can be broken down into the following steps:

1.  A `set` named `vowels` is initialized with all lowercase and uppercase English vowels (`"aeiouAEIOU"`). Using a `set` is highly efficient for membership testing, offering near-constant time complexity for lookups.

2.  The function then utilizes a generator expression, `(1 for ch in text if ch in vowels)`, to iterate through each character (`ch`) of the input `text`.

3.  For each character, it checks if the character is present in the `vowels` set. If it is, the generator yields the number `1`.

4.  Finally, the built-in `sum()` function is called on the generator. It consumes all the yielded `1`s and adds them together, producing the total count of vowels.

5.  The resulting integer sum is returned.

```python
# Internal logic demonstration
vowels = set("aeiouAEIOU")
text = "Hello"
# The expression becomes sum(1 for 'H' in vowels, 1 for 'e' in vowels, ...)
# This evaluates to sum(1, 1) because only 'e' and 'o' are in the set.
count = sum(1 for ch in text if ch in vowels)
# count is 2
```

## Usage Notes

- **Case-Insensitive**: The function is inherently case-insensitive because the `vowels` set contains both lowercase (`a, e, i, o, u`) and uppercase (`A, E, I, O, U`) vowels.
- **Non-Vowel Characters**: Any characters that are not vowels, including consonants, numbers, whitespace, and punctuation, are ignored and not included in the count.
- **Return Value**: The function always returns an integer (`int`), which will be `0` if no vowels are found in the input string.

**Output Example**: A possible return value for the input `"Test"` would be the integer `1`.

## Example

```python
# Example usage
input_string = "A quick brown fox jumps over the lazy dog."
vowel_count = count_vowels(input_string)
print(f"The sentence has {vowel_count} vowels.")

empty_string = ""
vowel_count_empty = count_vowels(empty_string)
print(f"An empty string has {vowel_count_empty} vowels.")

no_vowels_string = "Rhythm gym fly."
vowel_count_none = count_vowels(no_vowels_string)
print(f"The string '{no_vowels_string}' has {vowel_count_none} vowels.")
```

**Output:**

```
The sentence has 11 vowels.
An empty string has 0 vowels.
The string 'Rhythm gym fly.' has 0 vowels.
```

***
## FunctionDef pairwise_sum(numbers)
# Function: pairwise_sum(numbers: Iterable[float])

## Overview

The `pairwise_sum` function computes the arithmetic sum of an iterable of numbers using the Kahan summation algorithm to minimize floating-point errors and improve numerical precision.

## parameters

*   **`numbers`** (`Iterable[float]`): An iterable collection of numbers (e.g., a list, tuple, or generator) containing floats or integers. Each element will be converted to a float for the summation.

## Description

This function provides a numerically stable method for summing a sequence of floating-point numbers. Standard summation can lead to significant precision loss, especially when adding numbers of widely different magnitudes (e.g., adding a very small number to a very large one). The smaller number's precision can be lost entirely.

To counteract this, `pairwise_sum` implements the Kahan summation algorithm. The logic proceeds as follows:

1.  A `total` variable is initialized to `0.0` to hold the running sum.
2.  A `compensation` variable is also initialized to `0.0`. This variable is crucial for tracking the accumulated round-off error from previous additions.
3.  The function iterates through each `value` in the input `numbers`.
4.  In each iteration, the next `value` is first adjusted by subtracting the `compensation` from the previous step. This creates a corrected value `y`.
5.  This corrected `y` is added to the running `total`, and the result is stored in a temporary variable `t`.
6.  The error introduced in the previous addition is calculated by `(t - total) - y`. This captures the low-order bits that were lost due to floating-point arithmetic limitations. This error becomes the new `compensation`.
7.  The `total` is updated with the value of `t`.

By carrying the "lost" portion of each sum forward via the `compensation` variable, the algorithm ensures that it is incorporated into subsequent calculations, yielding a final `total` that is significantly more accurate than a naive summation.

## Usage Notes

- This function is highly recommended when summing a large set of floating-point numbers or when the numbers vary greatly in magnitude, as it prevents the accumulation of round-off errors.
- The input iterable can contain integers, which will be automatically cast to floats during the computation.
- The function always returns a single `float` value.

**Output Example**: A single `float` value representing the highly precise sum of the input numbers.

## Example

```python
# Example usage with a list of floats and integers
data = [10000000000.0, 3.14159, -10000000000.0, 1, 5.5]

# Calculate the sum using the numerically stable pairwise_sum function
result = pairwise_sum(data)
print(result)

# For comparison, a naive sum might lose precision in some environments,
# though modern Python's sum() is often quite accurate.
# The Kahan algorithm guarantees this high-precision behavior.
naive_sum = sum(data)
print(f"For comparison, naive sum is: {naive_sum}")
```

**Output:**

```
9.64159
For comparison, naive sum is: 9.64159
```

***
## FunctionDef split_into_chunks(text, size)
# Function: split_into_chunks(text: str, size: int)

## Overview

The `split_into_chunks` function divides a given string into a series of smaller, fixed-size substrings.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `text` | str | The input string that needs to be divided into chunks. |
| `size` | int | The desired maximum length for each chunk. This value must be a positive integer. |

## Description

This function provides a mechanism to segment a string into a tuple of smaller strings, each with a specified maximum length.

The function first validates the `size` parameter. If `size` is less than or equal to zero, it raises a `ValueError`, as chunking is not possible with a non-positive length.

If the `size` is valid, the function proceeds to iterate through the input `text` using a generator expression. It generates start indices for each chunk by using `range(0, len(text), size)`. For each start index `i`, it slices the string from that index up to `i + size`. This creates a substring of length `size`. The final substring may be shorter if the total length of the `text` is not perfectly divisible by `size`.

All generated substrings are collected into a tuple, which is the final return value.

```python
# Core logic
tuple(text[i : i + size] for i in range(0, len(text), size))
```

## Usage Notes

- The function will raise a `ValueError` if the `size` parameter is not a positive integer.
- The returned value is a `tuple` of strings, not a list.
- The last chunk in the returned tuple may be shorter than the specified `size` if the input string's length is not a multiple of `size`.

**Output Example**: A typical return value for a string split into chunks of size 10 might look like this:
`('This is a ', 'sample str', 'ing.')`

## Example

```python
# Example usage
input_string = "This is a sample string to demonstrate the chunking function."
chunk_size = 10

try:
    result = split_into_chunks(input_string, chunk_size)
    print(result)
except ValueError as e:
    print(e)

# Example with an invalid size
invalid_size = -5
try:
    result_invalid = split_into_chunks(input_string, invalid_size)
    print(result_invalid)
except ValueError as e:
    print(f"Caught expected error: {e}")
```

**Output:**

```
('This is a ', 'sample str', 'ing to dem', 'onstrate t', 'he chunkin', 'g function', '.')
Caught expected error: size must be positive
```

***
