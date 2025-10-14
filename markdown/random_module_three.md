## FunctionDef fibonacci(n)
**fibonacci**: The function of fibonacci is to compute the nth Fibonacci number using an iterative approach.

**parameters**: The parameters of this Function.
· n: An integer representing the 0-indexed position in the Fibonacci sequence to be computed.

**Code Description**:
The function begins by checking if the input `n` is a negative number. If it is, a `ValueError` is raised with the message "n must be non-negative".
Next, two variables, `a` and `b`, are initialized to 0 and 1, respectively. These represent the first two numbers in the Fibonacci sequence.
The code then enters a `for` loop that iterates `n` times. In each iteration, the values of `a` and `b` are updated simultaneously: `a` takes the current value of `b`, and `b` takes the sum of the current `a` and `b`. This process effectively steps through the Fibonacci sequence.
After the loop has completed `n` iterations, the variable `a` holds the nth Fibonacci number. The function concludes by returning the value of `a`.

**Note**:
The function is 0-indexed, meaning `fibonacci(0)` returns the first number in the sequence (0). It only accepts non-negative integers as input.

**Output Example**:
Calling `fibonacci(9)` returns `34`.
## FunctionDef invert_dictionary(mapping)
**invert_dictionary**: The function of invert_dictionary is to create a new dictionary by swapping the keys and values of an input dictionary, after validating that all values in the input are unique.

**parameters**: The parameters of this Function.
· mapping: A dictionary with string keys and integer values, where all values are expected to be unique.

**Code Description**:
The function first validates the input dictionary `mapping` to ensure its values are unique. It does this by comparing the number of values in the dictionary (`len(mapping.values())`) with the number of unique values, which is determined by converting the values to a set and checking its length (`len(set(mapping.values()))`). If these two lengths are not equal, it signifies that there are duplicate values, and the function raises a `ValueError` with the message "Values must be unique to invert dictionary". If all values are unique, the function proceeds to create a new dictionary using a dictionary comprehension. It iterates through each key-value pair of the input `mapping` and constructs a new dictionary where the original value becomes the key and the original key becomes the value. This inverted dictionary is then returned.

**Note**:
This function will raise a `ValueError` if the input dictionary contains any duplicate values. The function relies on the values of the input dictionary being hashable, as they become the keys in the new dictionary.

**Output Example**:
If `mapping` is `{'apple': 1, 'banana': 2, 'cherry': 3}`, the function will return `{1: 'apple', 2: 'banana', 3: 'cherry'}`.
## FunctionDef is_palindrome(text)
**is_palindrome**: The function of is_palindrome is to determine if a given string is a palindrome by comparing a normalized version of the string with its reverse.

**parameters**: The parameters of this Function.
· text: The string to check for palindrome properties.

**Code Description**:
The function first initializes a new string variable named `normalized`. This string is constructed by iterating through each character (`ch`) of the input `text`. For each character, it checks if the character is a whitespace character using `ch.isspace()`. If it is not a space, the character is converted to lowercase and included in the new `normalized` string. The `''.join()` method assembles these filtered and lowercased characters. Finally, the function returns the result of comparing the `normalized` string with its reversed version, which is created using slice notation `[::-1]`.

**Note**:
This function specifically ignores character casing and whitespace. Any other characters, including punctuation and numbers, will be included in the comparison.

**Output Example**:
Calling `is_palindrome("Taco cat")` returns `True`.
