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
## FunctionDef binary_search(arr, target)
# Function: binary_search(arr, target)

## Overview

The `binary_search` function efficiently finds the index of a target value within a sorted list by repeatedly dividing the search interval in half.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `list` | The sorted list of elements to search through. The elements can be of any comparable type (e.g., integers, strings). |
| `target` | `any` | The value to search for within the `arr`. This should be the same type as the elements in the list. |

## Description

This function implements the classic binary search algorithm. It operates on the principle of "divide and conquer" to find a target value in a sorted array.

The search begins by initializing two pointers, `left` and `right`, to the start and end of the array, respectively. A `while` loop continues as long as the `left` pointer is less than or equal to the `right` pointer, indicating there is still a valid search space.

Inside the loop, a `mid` index is calculated as the floor of the average of `left` and `right`. The element at `arr[mid]` is then compared to the `target`:
- If `arr[mid]` is equal to the `target`, the search is successful, and the function returns the `mid` index.
- If `arr[mid]` is less than the `target`, it means the target must lie in the right half of the current search space. The `left` pointer is then updated to `mid + 1` to discard the left half.
- If `arr[mid]` is greater than the `target`, the target must be in the left half. The `right` pointer is updated to `mid - 1` to discard the right half.

If the `while` loop completes without finding the target (i.e., `left` becomes greater than `right`), it means the target is not in the array. In this case, the function returns `-1`.

```python
# Example of internal logic
left, right = 0, 9  # For an array of size 10
target = 23
# Loop 1: mid = 4, arr[4] = 16. 16 < 23, so left becomes 5.
# Loop 2: mid = 7, arr[7] = 56. 56 > 23, so right becomes 6.
# Loop 3: mid = 5, arr[5] = 23. 23 == 23, return 5.
```

## Usage Notes

- The input list `arr` **must** be sorted in ascending order for the algorithm to function correctly. Searching an unsorted list will produce incorrect and unpredictable results.
- The function returns the zero-based index of the first occurrence of the `target` if found. Note that if there are duplicate values, which specific index is returned is not guaranteed, only that it will be one of the valid indices.
- If the `target` is not present in the list, the function returns `-1`.
- The time complexity of this algorithm is O(log n), making it extremely efficient for searching large datasets compared to a linear search (O(n)).

**Output Example**: The function returns an integer representing the index or `-1`.

## Example

```python
# Example usage
sorted_numbers = [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]

# Case 1: Target is found
target_value = 23
result_found = binary_search(sorted_numbers, target_value)
print(f"Searching for {target_value}: Index = {result_found}")

# Case 2: Target is not found
target_value_absent = 15
result_not_found = binary_search(sorted_numbers, target_value_absent)
print(f"Searching for {target_value_absent}: Index = {result_not_found}")
```

**Output:**

```
Searching for 23: Index = 5
Searching for 15: Index = -1
```

***
