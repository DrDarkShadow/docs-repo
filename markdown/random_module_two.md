## FunctionDef count_vowels(text)
**count_vowels**: The function of count_vowels is to count the number of vowels in a given string, regardless of case.

**parameters**: The parameters of this Function.
· text: Input string to scan.

**Code Description**: 
The function `count_vowels` takes a string `text` as input. It initializes a set called `vowels` containing both lowercase and uppercase vowels. It then iterates through each character `ch` in the input `text`. For each character, it checks if the character is present in the `vowels` set. If it is, the sum increments by 1. Finally, the function returns the total count of vowels found in the input string.

**Note**: The function uses a set for efficient vowel checking. The case-insensitive counting is achieved by including both lowercase and uppercase vowels in the `vowels` set.

**Output Example**: Calling count_vowels("Hello, World!") returns 3.

## FunctionDef pairwise_sum(numbers)
**pairwise_sum**: The function of pairwise_sum is to compute the sum of numbers from an iterable using a numerically stable Kahan summation algorithm.

**parameters**: The parameters of this Function.
· numbers: Any iterable of floats or ints.

**Code Description**: 
The function `pairwise_sum` calculates the sum of a sequence of numbers in a way that minimizes floating-point errors. It initializes `total` and `compensation` to 0.0. It then iterates through each `value` in the input `numbers` iterable. Inside the loop, it converts the current `value` to a float and subtracts the `compensation` from it, storing the result in `y`. It then adds `y` to the current `total` and stores the result in `t`. The `compensation` is updated to correct for the floating-point error introduced in the addition. Finally, the updated `total` is assigned back to `total`. After processing all numbers, the function returns the final `total`.

**Note**: This function uses Kahan summation to improve the accuracy of summing floating-point numbers, which is especially useful when dealing with a large number of values or values with varying magnitudes.

**Output Example**: Calling pairwise_sum([1.0, 2.0, 3.0]) returns 6.0. Calling pairwise_sum([1e9, 1.0, -1e9]) returns 1.0 (instead of 0.0, which might occur with naive summation).

## FunctionDef split_into_chunks(text, size)
**split_into_chunks**: The function of split_into_chunks is to split a given string into a tuple of substrings (chunks) of a specified size.

**parameters**: The parameters of this Function.
· text: The string that will be split into chunks.
· size: The desired length of each chunk.

**Code Description**: 
The function first checks if the `size` parameter is positive. If `size` is not positive, it raises a ValueError. Otherwise, it uses a generator expression with string slicing to create substrings of length `size` from the input `text`. The generator expression iterates through the `text` string with a step of `size`, creating substrings from index `i` to `i + size`. Finally, the function converts the generated sequence of substrings into a tuple and returns it.

**Note**: 
If the length of the input `text` is not a multiple of `size`, the last chunk in the tuple will be shorter than `size`.

**Output Example**: Calling split_into_chunks("abcdefgh", 3) returns ('abc', 'def', 'gh').

