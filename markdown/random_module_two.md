## FunctionDef reverse_words(sentence)
# Function: reverse_words(sentence)

## Overview

The `reverse_words` function reverses the order of words within a given string sentence.

## parameters

- **`sentence`** (str): The input string containing words to be reversed.

## Description

This function provides a straightforward way to reverse the word order in a string. The logic operates in three main steps:

1.  The input `sentence` is first broken down into a list of individual words using the `sentence.split()` method. This method, by default, splits the string at any whitespace character (like spaces, tabs, or newlines).

2.  The `reversed()` built-in function is then applied to the list of `words`. This creates a reverse iterator that yields the words from the list in the opposite order of their original appearance.

3.  Finally, the ` " ".join()` method is used to concatenate the words from the reverse iterator back into a single string. Each word is separated by a single space `" "`, forming the final reversed sentence which is then returned.

```python
# For an input "Python is fun"
words = "Python is fun".split()  # Becomes ['Python', 'is', 'fun']
reversed_words_iterator = reversed(words) # An iterator for ['fun', 'is', 'Python']
result = " ".join(reversed_words_iterator) # Becomes "fun is Python"
```

## Usage Notes

- The function splits the string by any amount of whitespace but joins the reversed words with only a single space. For example, an input of `"Hello   world"` will result in `"world Hello"`.
- Leading and trailing whitespace in the input `sentence` will be removed in the output. For example, `"  leading space"` becomes `"space leading"`.
- If an empty string `""` is provided as input, an empty string `""` will be returned.

**Output Example**: A string with the words in reversed order. For the input `"this is a test"`, the output would look like:

```
"test a is this"
```

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

This function determines if a number is an Armstrong number by performing a calculation and comparing the result to the original number.

The logic proceeds as follows:
1.  The input integer `n` is first converted into a string, `digits = str(n)`, to easily count and iterate through its individual digits.
2.  The number of digits is calculated by finding the length of the string `digits` and storing it in the `power` variable.
3.  The function then calculates the sum of each digit raised to the power of the total number of digits. This is achieved using a generator expression: `sum(int(d)**power for d in digits)`.
4.  Finally, it returns a boolean value by comparing the calculated sum with the original number `n`. If they are equal, the function returns `True`; otherwise, it returns `False`.

For example, for the number `153`:
- The number of digits (`power`) is 3.
- The calculation is `1**3 + 5**3 + 3**3`, which equals `1 + 125 + 27 = 153`.
- Since `153 == 153`, the function returns `True`.

```python
# Internal logic for n = 153
digits = "153"
power = 3
# sum(int('1')**3, int('5')**3, int('3')**3)
# sum(1, 125, 27) -> 153
# return 153 == 153 -> True
```

## Usage Notes

- The function is designed to work with non-negative integers. Providing a negative number will result in a `ValueError` because the negative sign cannot be converted to an integer.
- The function returns a boolean value: `True` if the number is an Armstrong number, and `False` otherwise.

**Output Example**:
```
True
```

## Example

```python
# Example 1: A number that is an Armstrong number
is_armstrong_number = is_armstrong(153)
print(f"Is 153 an Armstrong number? {is_armstrong_number}")

# Example 2: A number that is not an Armstrong number
is_not_armstrong_number = is_armstrong(123)
print(f"Is 123 an Armstrong number? {is_not_armstrong_number}")

# Example 3: A single-digit number (all single-digit numbers are Armstrong numbers)
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
## FunctionDef is_palindrome(s)
# Function: is_palindrome(s)

## Overview

The `is_palindrome` function checks if a given string is a palindrome, ignoring case and spaces.

## parameters

- `s` (str): The input string to be checked for palindrome properties.

## Description

This function determines if a string reads the same forwards as it does backwards. The process involves two main steps: normalization and comparison.

First, the function normalizes the input string `s` to ensure a fair comparison. It converts all characters to lowercase using `s.lower()` to make the check case-insensitive. Immediately after, it removes all space characters from the string by calling `.replace(" ", "")`. This cleaned-up version of the string is then reassigned to the variable `s`.

```python
s = s.lower().replace(" ", "")
```

Second, the function compares the normalized string `s` with its reverse. The reverse of the string is obtained using Python's slice notation `s[::-1]`. If the normalized string is identical to its reversed version, the expression `s == s[::-1]` evaluates to `True`, indicating it is a palindrome. Otherwise, it evaluates to `False`. The function returns this boolean result.

## Usage Notes

- The function is case-insensitive. For example, `is_palindrome('Racecar')` will return `True`.
- All space characters are ignored. For example, `is_palindrome('taco cat')` will return `True`.
- The function does not remove punctuation or other non-alphanumeric characters. A string like `'A man, a plan, a canal: Panama'` will return `False` because the punctuation is included in the comparison.

**Output Example**: The function returns a boolean value.
`True`

## Example

```python
# Example 1: A palindrome with mixed case and spaces
result1 = is_palindrome("A man a plan a canal Panama")
print(f"'A man a plan a canal Panama' is a palindrome: {result1}")

# Example 2: A simple non-palindrome
result2 = is_palindrome("hello world")
print(f"'hello world' is a palindrome: {result2}")

# Example 3: A palindrome with mixed case
result3 = is_palindrome("TacoCat")
print(f"'TacoCat' is a palindrome: {result3}")
```

**Output:**

```
'A man a plan a canal Panama' is a palindrome: True
'hello world' is a palindrome: False
'TacoCat' is a palindrome: True
```

***
