## FunctionDef count_vowels(text)
**count_vowels**: The function of count_vowels is to count the number of vowels in a given string, ignoring case.

**parameters**: The parameters of this Function.
· text: Input string to scan.

**Code Description**: 
The function `count_vowels` takes a string `text` as input. It initializes a set called `vowels` containing both lowercase and uppercase vowels. It then iterates through each character `ch` in the input `text`. For each character, it checks if the character is present in the `vowels` set. If it is, the function increments a counter (implicitly done using `sum` with a generator expression). Finally, the function returns the total count of vowels found in the input string.

**Note**: 
The function uses a set for efficient vowel checking. The case-insensitive counting is achieved by including both lowercase and uppercase vowels in the `vowels` set.

**Output Example**: Calling count_vowels("Hello, World!") returns 3.

## FunctionDef pairwise_sum(numbers)
**pairwise_sum**: The function of pairwise_sum is to compute the sum of numbers from an iterable in a numerically stable way using Kahan summation.

**parameters**: The parameters of this Function.
· numbers: Any iterable of floats or ints.

**Code Description**: 
The function `pairwise_sum` takes an iterable of numbers as input. It initializes `total` and `compensation` to 0.0. It then iterates through each `value` in the input `numbers`. Inside the loop, it converts the `value` to a float and subtracts the `compensation` from it, storing the result in `y`. It then adds `y` to the current `total` and stores the result in `t`. The `compensation` is updated to correct for floating-point errors. Finally, the updated `total` is assigned back to `total`. After iterating through all the numbers, the function returns the final `total`.

**Note**: 
This function uses Kahan summation to minimize floating-point errors, which can be significant when summing a large number of values with varying magnitudes.

**Output Example**: Calling pairwise_sum([1.0, 1e10, 1.0, -1e10]) returns 2.0.

## FunctionDef split_into_chunks(text, size)
**split_into_chunks**: The function of split_into_chunks is to split a given string into a tuple of fixed-size substrings (chunks).

**parameters**: The parameters of this Function.
· text: The string to split.
· size: The chunk length; must be positive.

**Code Description**: 
The function `split_into_chunks` takes a string `text` and an integer `size` as input. It first checks if the `size` is positive. If `size` is not positive, it raises a ValueError. Otherwise, it uses a generator expression and the `tuple()` constructor to split the input string `text` into chunks of length `size`. The generator expression `text[i : i + size] for i in range(0, len(text), size)` iterates through the string `text` with a step of `size`, creating substrings (chunks) starting from index `i` up to (but not including) index `i + size`. The resulting substrings are then converted into a tuple, which is returned. The last chunk may be shorter than `size` if the length of the input string is not a multiple of `size`.

**Note**: 
The function raises a ValueError if the size is not positive. The last chunk in the tuple may be shorter than the specified size if the input string's length is not a multiple of the size.

**Output Example**: Calling split_into_chunks("abcdefgh", 3) returns ('abc', 'def', 'gh').

