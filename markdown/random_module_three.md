## FunctionDef fibonacci(n)
**fibonacci**: The function of fibonacci is to compute the nth Fibonacci number using an iterative approach.

**parameters**: The parameters of this Function.
· n: An integer representing the 0-indexed position of the desired Fibonacci number.

**Code Description**:
The function begins by checking if the input `n` is a negative number. If it is, a `ValueError` is raised. Two variables, `a` and `b`, are initialized to 0 and 1, respectively, which are the first two numbers in the Fibonacci sequence. The function then enters a `for` loop that iterates `n` times. In each iteration, the values of `a` and `b` are simultaneously updated: `a` takes the current value of `b`, and `b` is updated to the sum of the previous `a` and `b`. This process effectively generates the next number in the sequence. After the loop finishes, the function returns the final value of `a`, which represents the nth Fibonacci number.

**Note**:
The function calculates the sequence starting from a 0-based index, where `fibonacci(0)` is 0. It raises a `ValueError` for any negative input `n`. This iterative method is efficient in terms of memory usage compared to a recursive approach, especially for large values of `n`.

**Output Example**:
Calling `fibonacci(8)` returns `21`.
## FunctionDef invert_dictionary(mapping)
**invert_dictionary**: The function of invert_dictionary is to create a new dictionary by swapping the keys and values of a given dictionary, after ensuring all values are unique.

**parameters**: The parameters of this Function.
· mapping: A dictionary with string keys and integer values, where all values are expected to be unique.

**Code Description**:
The function first validates the input dictionary `mapping`. It compares the number of values in the dictionary with the number of unique values by converting the values to a set. If the counts are not equal, it indicates that the original dictionary contains duplicate values, and the function raises a `ValueError` with the message "Values must be unique to invert dictionary". If all values are unique, the function proceeds to create a new dictionary using a dictionary comprehension. It iterates through each key-value pair of the input `mapping` and constructs the new dictionary by making each original value a key and each original key its corresponding value. This inverted dictionary is then returned.

**Note**:
This function will raise a `ValueError` if the input dictionary contains duplicate values, as a dictionary cannot have duplicate keys, which the values would become after inversion.

**Output Example**:
If `mapping` is `{'apple': 1, 'banana': 2}`, the function returns `{1: 'apple', 2: 'banana'}`.
## FunctionDef is_palindrome(text)
**is_palindrome**: The function of is_palindrome is to determine if a given string is a palindrome by ignoring character casing and spaces.

**parameters**: The parameters of this Function.
· text: The string to check for palindrome properties.

**Code Description**:
The function first creates a "normalized" version of the input `text`. It does this by iterating through each character of the `text` string. For every character that is not a whitespace character (as determined by `ch.isspace()`), it converts the character to lowercase and includes it in a new string called `normalized`. After processing all characters, the function compares the `normalized` string with its reversed version, which is created using the slice notation `[::-1]`. The function returns `True` if the normalized string is identical to its reverse, and `False` otherwise.

**Note**:
This function is case-insensitive and ignores all whitespace characters, including spaces, tabs, and newlines, when performing the palindrome check.

**Output Example**:
Calling `is_palindrome("Taco cat")` returns `True`.
