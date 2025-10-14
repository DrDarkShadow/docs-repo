## FunctionDef fibonacci(n)
## Function fibonacci
**fibonacci**: The function of fibonacci is to compute the nth Fibonacci number using an iterative approach.

**parameters**: The parameters of this Function.
· n: An integer representing the 0-indexed position in the Fibonacci sequence for which to compute the value.

**Code Description**: 
The function first checks if the input `n` is a negative number. If it is, a `ValueError` is raised. It then initializes two variables, `a` and `b`, to `0` and `1` respectively, which are the first two numbers in the Fibonacci sequence. The function proceeds to loop `n` times. In each iteration, it updates the values of `a` and `b`: `a` takes the current value of `b`, and `b` takes the sum of the old `a` and `b`. This process effectively steps through the Fibonacci sequence. After the loop completes, the function returns the final value of `a`, which corresponds to the nth Fibonacci number.

**Note**: 
This function calculates the sequence starting from index 0. For example, `fibonacci(0)` returns 0, and `fibonacci(1)` returns 1. The implementation is iterative, making it efficient in terms of memory usage compared to a recursive solution for large values of `n`.

**Output Example**: 
```python
# Calling the function with n = 8
fibonacci(8)

# Expected return value
21
```

---
## FunctionDef invert_dictionary(mapping)
## Function invert_dictionary
**invert_dictionary**: The function of invert_dictionary is to create a new dictionary by swapping the keys and values of a given dictionary, after ensuring all values in the original dictionary are unique.

**parameters**: The parameters of this Function.
· mapping: A dictionary mapping strings to integers (`Dict[str, int]`). The values in this dictionary are expected to be unique.

**Code Description**: 
The function first validates the input dictionary `mapping` to ensure its values are unique. It does this by comparing the number of values (`len(mapping.values())`) with the number of unique values, which is determined by converting the values to a set and checking its length (`len(set(mapping.values()))`). If these two lengths are not equal, it indicates that there are duplicate values, and the function raises a `ValueError` with the message "Values must be unique to invert dictionary".

If all values are unique, the function proceeds to create a new dictionary using a dictionary comprehension. It iterates through each key-value pair of the input `mapping` and constructs a new dictionary where each original value becomes a key and its corresponding original key becomes the value. This inverted dictionary is then returned.

**Note**: 
This function will raise a `ValueError` if the input `mapping` dictionary contains any duplicate values, as an inverted dictionary cannot have duplicate keys.

**Output Example**: 
```python
# Given the input:
mapping = {'apple': 1, 'banana': 2, 'cherry': 3}

# Calling invert_dictionary(mapping) returns:
{1: 'apple', 2: 'banana', 3: 'cherry'}
```

---
## FunctionDef is_palindrome(text)
## Function is_palindrome
**is_palindrome**: The function of is_palindrome is to determine if a given string is a palindrome by ignoring character casing and spaces.

**parameters**: The parameters of this Function.
· text: The string to check.

**Code Description**: 
The function first normalizes the input `text`. It creates a new string called `normalized` by iterating through each character of the input `text`. For each character, it checks if it is a whitespace character. If it is not a space, the character is converted to lowercase and added to the `normalized` string.

After normalization, the function compares the `normalized` string with its reversed version, which is created using the slice notation `[::-1]`. It returns `True` if the normalized string is identical to its reverse, indicating it is a palindrome, and `False` otherwise.

**Note**: 
This function's palindrome check is case-insensitive and ignores all whitespace characters (spaces, tabs, newlines, etc.). It only considers alphabetic and other non-space characters for the comparison.

**Output Example**:
```python
is_palindrome("No lemon no melon")
```
Output:
```
True
```
