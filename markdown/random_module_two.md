## FunctionDef reverse_words(sentence)
# Function: reverse_words(sentence)

## Overview

The `reverse_words` function reverses the order of words within a given string.

## parameters

- **`sentence`** `str`: The input string containing words to be reversed. Words are assumed to be separated by whitespace.

## Description

This function provides a straightforward way to reverse the word order in a sentence. The logic operates in three main steps:

1.  The input `sentence` is first broken down into a list of individual words using the `split()` method. By default, `split()` uses any whitespace as a delimiter, effectively handling single spaces, multiple spaces, tabs, and newlines between words.

2.  The `reversed()` function is then applied to this list of `words`. This creates a reverse iterator that yields the words from the list in the opposite order of their original appearance.

3.  Finally, the `join()` method is called on a space character (`" "`). This method takes all the items from the reverse iterator and concatenates them into a single new string, with each word separated by a single space. The resulting string is then returned.

For example, if the input is `Hello world`, it is first split into `['Hello', 'world']`. This list is then reversed to yield `'world'` followed by `'Hello'`. These are then joined with a space to produce the final output `world Hello`.

## Usage Notes

-   The function treats any sequence of whitespace between words as a single delimiter. For instance, `"word1   word2"` will be correctly processed.
-   Leading and trailing whitespace in the input `sentence` are automatically handled and removed by the `split()` method, so they will not appear in the output.
-   This function only reverses the order of the words themselves, not the characters within each word.

**Output Example**: A string with the words in reverse order.

## Example

```python
# Example usage
input_sentence = "Python is a powerful language"
reversed_sentence = reverse_words(input_sentence)
print(reversed_sentence)
```

**Output:**

```
language powerful a is Python
```

***
## FunctionDef is_armstrong(n)
# Function: is_armstrong(n)

## Overview

The `is_armstrong` function determines if a given integer is an Armstrong number.

## Parameters

*   `n` (int): The integer to be checked.

## Description

This function evaluates whether a number `n` is an Armstrong number (also known as a narcissistic number). An Armstrong number is a number that is equal to the sum of its own digits each raised to the power of the number of digits.

The function operates through the following steps:
1.  It first converts the input integer `n` into a string representation using `digits = str(n)`. This allows for easy iteration over each digit and for counting the total number of digits.
2.  The number of digits is determined by finding the length of the string `digits` and is stored in the `power` variable.
3.  A generator expression, `(int(d)**power for d in digits)`, is used to iterate through each character `d` in the `digits` string. Each character is converted back to an integer and raised to the calculated `power`.
4.  The `sum()` function then calculates the total sum of these powered digits.
5.  Finally, this sum is compared to the original number `n`. The function returns `True` if they are equal, indicating `n` is an Armstrong number, and `False` otherwise.

For example, for the number `153`:
- The number of digits (`power`) is 3.
- The sum is calculated as `1**3 + 5**3 + 3**3`, which equals `1 + 125 + 27 = 153`.
- Since the sum `153` equals the original number `153`, the function returns `True`.

## Usage Notes

- The function is designed to work with non-negative integers. Providing a negative number or a non-integer type may result in unexpected behavior or errors.
- All single-digit numbers (0-9) are considered Armstrong numbers by this definition, as `n**1` is always `n`.

**Output Example**: The function returns a boolean value.
```
True
```

## Example

```python
# Example 1: An Armstrong number
is_armstrong_number = is_armstrong(153)
print(f"Is 153 an Armstrong number? {is_armstrong_number}")

# Example 2: A non-Armstrong number
is_not_armstrong_number = is_armstrong(123)
print(f"Is 123 an Armstrong number? {is_not_armstrong_number}")

# Example 3: A single-digit number
is_single_digit_armstrong = is_armstrong(9)
print(f"Is 9 an Armstrong number? {is_single_digit_armstrong}")
```

**Output:**

```
Is 153 an Armstrong number? True
Is 123 an Armstrong number? False
Is 9 an Armstrong number? True
```

***
