## FunctionDef count_vowels(text)
# count_vowels

## Overview

The `count_vowels` function counts the total number of vowels within a given string in a case-insensitive manner.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `text` | `str` | The input string in which to count the vowels. |

## Description

This function provides a straightforward way to determine the number of vowels in a string. The core logic operates as follows:

- A `set` named `vowels` is initialized with all lowercase and uppercase vowel characters (`a, e, i, o, u, A, E, I, O, U`). Using a set allows for highly efficient membership checking, which is faster than searching through a list or string repeatedly.

- The function then iterates through each character (`ch`) of the input `text`.

- For each character, it checks if the character exists within the `vowels` set.

- A generator expression, `(1 for ch in text if ch in vowels)`, yields the number `1` for every character that is confirmed to be a vowel.

- The built-in `sum()` function is used to consume the values from the generator, effectively adding up all the `1`s to produce a final count of the vowels.

- The function returns this final sum as an integer. Characters that are not vowels, such as consonants, numbers, whitespace, and symbols, are ignored.

```python
# Internal logic breakdown
vowels = set("aeiouAEIOU")
# For an input "Hello", the generator would be equivalent to (1, 1)
# sum((1 for ch in "Hello" if ch in vowels)) would calculate sum((1, 1)) which is 2
return sum(1 for ch in text if ch in vowels)
```

## Usage Notes

- The function is **case-insensitive**. It will count both 'a' and 'A' as one vowel.
- Any characters that are not vowels (including consonants, numbers, punctuation, and whitespace) are ignored and not included in the count.
- The function always returns an integer. If no vowels are found, it will return `0`.

**Output Example**:
A possible return value for an input string is an integer representing the total vowel count.
```
7
```

## Example

```python
# Example usage
# Define an input string with a mix of cases, spaces, and punctuation.
input_string = "This is an Example String."

# Call the function to count the vowels.
vowel_count = count_vowels(input_string)

# Print the result.
print(f"The input string is: '{input_string}'")
print(f"The number of vowels is: {vowel_count}")
```

**Output:**
```
The input string is: 'This is an Example String.'
The number of vowels is: 7
```

---
## FunctionDef pairwise_sum(numbers)
# pairwise_sum

## Overview

The `pairwise_sum` Function computes the sum of a sequence of numbers using the Kahan summation algorithm to achieve higher numerical precision.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `numbers` | `Iterable[float]` | An iterable collection of numbers (e.g., a list, tuple) to be summed. The elements can be floats or integers, as they will be cast to floats internally. |

## Description

This function provides a numerically stable method for summing floating-point numbers, which is crucial for avoiding precision errors that can occur with standard summation, especially when dealing with a large set of numbers or numbers of vastly different magnitudes.

The function implements the **Kahan summation algorithm**. This algorithm works by maintaining a running `compensation` variable that accumulates the round-off error from each addition.

The process for each number in the input `numbers` is as follows:
1.  A corrected value `y` is calculated by subtracting the `compensation` from the previous iteration's error from the current `value`.
2.  This corrected value `y` is added to the running `total`, storing the result in a temporary variable `t`.
3.  The new round-off error is calculated. In an ideal scenario, `(t - total)` would be exactly equal to `y`. However, due to floating-point limitations, there's often a small difference. This difference, `(t - total) - y`, represents the error (the "lost" low-order bits) from the addition. This error is stored in the `compensation` variable for the next iteration.
4.  The main `total` is updated with the value of `t`.

By carrying the round-off error from one step to the next, the algorithm significantly reduces the total accumulated error, yielding a more accurate final sum.

```python
# Kahan summation for improved precision
total = 0.0
compensation = 0.0
for value in numbers:
    y = float(value) - compensation
    t = total + y
    compensation = (t - total) - y
    total = t
return total
```

## Usage Notes

- This function is particularly useful when summing a large number of floating-point values or when the values have widely varying magnitudes, where the standard built-in `sum()` might suffer from significant precision loss.
- The input iterable can contain integers; each value is explicitly cast to a `float` before being processed.

**Output Example**: The function returns a single floating-point number representing the accurate sum.
```
10000000000.000001
```

## Example

```python
# Example usage
# A naive sum of [1e10, 1.0, -1e10] might result in 0.0 due to floating-point precision loss
# when the small number '1.0' is added to the large number '1e10'.
# The Kahan summation algorithm correctly computes the sum as 1.0.

numbers_to_sum = [10000000000.0, 1.0, -10000000000.0]
result = pairwise_sum(numbers_to_sum)
print(f"The pairwise_sum result is: {result}")

# For comparison, let's see the naive sum
naive_result = sum(numbers_to_sum)
print(f"The naive sum() result is: {naive_result}")
```

**Output:**
```
The pairwise_sum result is: 1.0
The naive sum() result is: 0.0
```

---
## FunctionDef split_into_chunks(text, size)
# split_into_chunks

## Overview

The `split_into_chunks` function splits a given string into a series of smaller, fixed-size substrings or 'chunks'.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `text` | `str` | The input string that needs to be divided into chunks. |
| `size` | `int` | The desired length for each chunk. This value must be a positive integer. |

## Description

This function provides a straightforward way to partition a string into multiple segments of a specified length.

The function first validates the `size` parameter. It checks if `size` is a positive number. If `size` is zero or negative, the function will raise a `ValueError` to prevent invalid operations, as chunking requires a positive length.

The core logic uses a generator expression combined with string slicing. It iterates through the input `text` using a `range` that starts at index `0` and increments by the given `size`. In each step, it slices the string from the current index `i` to `i + size`. This creates a sequence of substrings. Finally, this sequence is converted into a tuple and returned.

If the length of the input `text` is not a multiple of `size`, the last chunk in the sequence will contain the remaining characters and will therefore be shorter than the specified `size`.

## Usage Notes

- The `size` parameter must be a positive integer. Providing a value of `0` or less will result in a `ValueError`.
- The last element in the returned tuple may be shorter than `size` if the total length of the `text` is not perfectly divisible by `size`.
- The function returns a `tuple` of strings, which is an immutable sequence.

**Output Example**: A possible return value for this function would look like this:
```
('chunk1', 'chunk2', 'chunk3', '...')
```

## Example

```python
# Example usage
input_string = "This is a sample string to be chunked."
chunk_size = 5

# Split the string into chunks of size 5
result = split_into_chunks(input_string, chunk_size)
print(result)

# Example that results in a shorter final chunk
another_string = "abcdefgh"
result_short = split_into_chunks(another_string, 3)
print(result_short)

# Example of invalid size
try:
    split_into_chunks("some text", 0)
except ValueError as e:
    print(e)
```

**Output:**
```
('This ', 'is a ', 'sampl', 'e str', 'ing t', 'o be ', 'chunk', 'ed.')
('abc', 'def', 'gh')
size must be positive
```
