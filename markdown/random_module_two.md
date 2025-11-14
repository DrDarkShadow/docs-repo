## FunctionDef reverse_words(sentence)
# Function: reverse_words(sentence)

## Overview

The `reverse_words` function reverses the order of words within a given string.

## parameters

- `sentence` (str): The input string containing words to be reversed. It is expected to be a sentence or a series of words separated by spaces.

## Description

This function takes a single string argument, `sentence`, and returns a new string where the sequence of words is inverted. The logic operates in two main steps:

1.  The input `sentence` is first broken down into a list of individual words using the `split()` method. This method, by default, splits the string at any whitespace character (spaces, tabs, newlines).
2.  The `reversed()` function is then applied to this list of words, creating an iterator that yields the words in the reverse order.
3.  Finally, the `join()` method is called on a space character (`" "`) to concatenate the words from the reversed iterator back into a single string, with each word separated by a single space.

For example, if the input is `"hello world"`, it is first split into `['hello', 'world']`. This list is then reversed to `['world', 'hello']`, and finally joined back together to produce the string `"world hello"`.

```python
# Internal logic breakdown
input_sentence = "Python is fun"
# 1. Split the sentence into a list of words
words_list = input_sentence.split()  # Result: ['Python', 'is', 'fun']

# 2. Reverse the order of the list
reversed_list_iterator = reversed(words_list) # An iterator for ['fun', 'is', 'Python']

# 3. Join the reversed words with a space
final_string = " ".join(reversed_list_iterator) # Result: "fun is Python"
```

## Usage Notes

- The function splits the string by any whitespace and rejoins with single spaces. This means multiple spaces or other whitespace characters between words in the input will be normalized to a single space in the output.
- Punctuation attached to words (e.g., "world.") will remain attached to those words in the reversed output (e.g., "test. a is This"). The function does not separate punctuation from words.
- The function is case-sensitive and preserves the original casing of each word.

**Output Example**: A string with the words in reverse order.

## Example

```python
# Example usage
original_sentence = "The quick brown fox jumps over the lazy dog"
reversed_sentence = reverse_words(original_sentence)
print(reversed_sentence)
```

**Output:**

```
dog lazy the over jumps fox brown quick The
```

***
## FunctionDef is_armstrong(n)
# Function: is_armstrong(n)

## Overview

The `is_armstrong` function checks if a given integer is an Armstrong number (a number that is equal to the sum of its own digits each raised to the power of the number of digits).

## parameters

- **`n`** (`int`): The non-negative integer to be checked.

## Description

This function determines if a number is an Armstrong number by performing a series of calculations.

First, the input integer `n` is converted into a string, `digits`, to easily access its individual digits and count them. The length of this string, which represents the total number of digits in `n`, is stored in the `power` variable.

Next, the function iterates through each character in the `digits` string. For each digit character, it converts it back to an integer and raises it to the power of `power`. A generator expression `(int(d)**power for d in digits)` is used for this calculation.

Finally, the `sum()` function calculates the total sum of these powered digits. This sum is then compared to the original input number `n`. If the sum and `n` are equal, the function returns `True`; otherwise, it returns `False`.

For example, for the number `153`:
1. The number of digits (`power`) is 3.
2. The sum is calculated as `1**3 + 5**3 + 3**3`, which equals `1 + 125 + 27 = 153`.
3. Since the sum `153` is equal to the original number `153`, the function returns `True`.

```python
# Internal logic for n = 153
digits = "153"
power = 3
# sum(int('1')**3, int('5')**3, int('3')**3)
# sum(1, 125, 27) -> 153
# return 153 == 153 -> True
```

## Usage Notes

- The function is designed to work with non-negative integers.
- Providing a negative number, a float, or a string containing non-digit characters will result in a `ValueError` because the `int()` conversion will fail on non-digit characters like `-` or `.`.

**Output Example**: The function returns a boolean value.
`True`

## Example

```python
# Example 1: Check an Armstrong number
is_armstrong_number = is_armstrong(153)
print(f"Is 153 an Armstrong number? {is_armstrong_number}")

# Example 2: Check a non-Armstrong number
is_not_armstrong_number = is_armstrong(123)
print(f"Is 123 an Armstrong number? {is_not_armstrong_number}")

# Example 3: Check a single-digit number (all are Armstrong numbers)
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
