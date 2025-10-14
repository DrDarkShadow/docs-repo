## FunctionDef count_vowels(text)
# count_vowels

### Overview
The `count_vowels` function counts the total number of vowels within a given string in a case-insensitive manner.

### Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `text` | `str` | The input string in which to count vowels. |

### Description
This function provides an efficient way to determine the number of vowels (a, e, i, o, u) in a string.

The core logic begins by defining a `set` named `vowels` that contains all lowercase and uppercase vowels. Using a `set` for this purpose allows for very fast membership testing (i.e., checking if a character is a vowel), which is more performant than searching through a list or string, especially for large inputs.

The function then iterates through each character (`ch`) of the input `text`. For each character, it checks if `ch` is present in the `vowels` set. A generator expression, `(1 for ch in text if ch in vowels)`, yields the number `1` for every character that is a vowel.

Finally, the built-in `sum()` function is called on this generator. It consumes the generated `1`s and adds them together, producing the final count of all vowels found in the string.

### Usage Notes
- The vowel check is **case-insensitive** because the `vowels` set includes both `aeiou` and `AEIOU`.
- Characters that are not vowels, including consonants, numbers, whitespace, and symbols, are ignored and not included in the count.
- The function returns an integer `0` if the input string is empty or contains no vowels.

**Output Example**: The function returns an integer representing the total vowel count.
```
5
```

### Example
```python
# Example usage of count_vowels

# A simple string with mixed case vowels
sample_text = "Hello World! This is an Example."
vowel_count = count_vowels(sample_text)

print(f"The string is: '{sample_text}'")
print(f"The number of vowels is: {vowel_count}")

# An example with no vowels
no_vowel_text = "Rhythm, fly, myrrh."
no_vowel_count = count_vowels(no_vowel_text)
print(f"\nThe string is: '{no_vowel_text}'")
print(f"The number of vowels is: {no_vowel_count}")
```

#### Output
```
The string is: 'Hello World! This is an Example.'
The number of vowels is: 9

The string is: 'Rhythm, fly, myrrh.'
The number of vowels is: 0
```
## FunctionDef pairwise_sum(numbers)
### Overview
The `pairwise_sum` function computes the sum of an iterable of numbers using the Kahan summation algorithm, a numerically stable approach that minimizes floating-point errors.

---
### parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `numbers` | Iterable[float] | An iterable collection of numbers (e.g., a list, tuple) to be summed. The elements can be floats or integers, as they will be cast to floats internally. |

---
### Description
This function provides a high-precision method for summing a sequence of floating-point numbers. Unlike a naive summation loop, which can accumulate significant rounding errors, `pairwise_sum` implements the Kahan summation algorithm. This algorithm is particularly effective when the numbers being summed have widely different magnitudes.

The core of the algorithm involves a `compensation` variable that tracks the "lost" low-order precision from each addition.

The logic proceeds as follows for each number in the input iterable:
1.  A corrected value `y` is calculated by subtracting the `compensation` from the previous step from the current `value`.
2.  This corrected value `y` is added to the running `total`, creating a provisional sum `t`.
3.  The `compensation` for the next iteration is calculated. It captures the rounding error that occurred in the previous addition. This is done by computing `(t - total) - y`. In perfect arithmetic, this would be zero, but in floating-point math, it isolates the part of `y` that was lost when added to `total`.
4.  The running `total` is updated to the provisional sum `t`.

By repeatedly carrying over the rounding error via the `compensation` variable, the function maintains a much higher degree of precision in the final sum.

---
### Usage Notes
- This function is highly recommended over a standard `sum()` or a simple loop when accuracy is critical, especially when summing a large quantity of floating-point numbers or numbers with varying scales (e.g., adding a very small number to a very large one).
- The input `numbers` can be any iterable, including lists, tuples, and generators.
- Although the function is named `pairwise_sum`, the algorithm implemented is the Kahan summation algorithm, not a recursive pairwise summation method.

**Output Example**:
The function returns a single floating-point number representing the precise sum of the input values.
```
2.0
```

---
### Example
The following example demonstrates how `pairwise_sum` can produce a correct result where a naive summation might fail due to floating-point precision loss.

```python
# Example usage
# A naive sum(data) would likely result in 0.0 due to precision loss
# when adding 1.0 to 1e100 and then subtracting 1e100.
data = [1.0, 1e100, 1.0, -1e100]
result = pairwise_sum(data)
print(result)
```

#### Output
```
2.0
```
## FunctionDef split_into_chunks(text, size)
# split_into_chunks

### Overview
The `split_into_chunks` function divides a given string into a sequence of smaller strings, each of a specified maximum length.

### Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `text` | `str` | The input string that needs to be divided into chunks. |
| `size` | `int` | The desired length for each chunk. This value must be a positive integer. |

### Description
This function provides a straightforward way to segment a string into fixed-size pieces.

The function first validates the `size` parameter. It checks if `size` is a positive number. If `size` is zero or negative, it raises a `ValueError` to prevent invalid operations, as chunking requires a positive length.

The core logic is implemented using a generator expression combined with string slicing. The `range(0, len(text), size)` function generates a sequence of starting indices for each chunk (e.g., `0`, `size`, `2*size`, ...). For each starting index `i`, a slice `text[i : i + size]` is taken from the original string. This slice represents one chunk.

Finally, all the generated chunks are collected into a `tuple` and returned. The last chunk in the tuple will be shorter than the specified `size` if the total length of the input `text` is not an even multiple of `size`.

```python
# Internal logic breakdown
def split_into_chunks(text: str, size: int) -> Tuple[str, ...]:
    # 1. Validate the size parameter
    if size <= 0:
        raise ValueError("size must be positive")
    
    # 2. Generate chunks using a generator expression and slicing
    #    range(0, len(text), size) creates the start indices for each slice.
    #    text[i : i + size] extracts the substring for each chunk.
    chunks_generator = (text[i : i + size] for i in range(0, len(text), size))
    
    # 3. Convert the generator to a tuple and return
    return tuple(chunks_generator)
```

### Usage Notes
- The `size` parameter must be a positive integer. Providing a value of `0` or less will result in a `ValueError`.
- The final element in the returned tuple may have a length less than `size` if the input string's length is not perfectly divisible by `size`.

**Output Example**: The function returns a tuple of strings.
```
('chu', 'nk1', 'chu', 'nk2', 'end')
```

### Example
```python
# Example usage
long_string = "This is a sample string to be split into chunks."
chunk_size = 10

# Split the string into chunks of 10 characters
result = split_into_chunks(long_string, chunk_size)
print(result)

# Example with a string length not divisible by the chunk size
short_string = "abcdefgh"
result_short = split_into_chunks(short_string, 3)
print(result_short)
```

#### Output
```
('This is a ', 'sample str', 'ing to be ', 'split into', ' chunks.')
('abc', 'def', 'gh')
```
