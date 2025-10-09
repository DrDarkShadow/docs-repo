## FunctionDef count_vowels(text)
**count_vowels**: The function of count_vowels is to count the number of vowels in a given string.

**parameters**: The parameters of this Function.
· text: Input string to scan.

**Code Description**: 
The function `count_vowels` takes a string `text` as input. It initializes a set called `vowels` containing both lowercase and uppercase vowels. It then iterates through each character `ch` in the input `text`. For each character, it checks if the character is present in the `vowels` set. If it is, the sum is incremented by 1. Finally, the function returns the total count of vowels found in the input string.

**Note**: 
The function performs a case-insensitive vowel count by including both lowercase and uppercase vowels in the `vowels` set. The use of a set for `vowels` allows for efficient checking of vowel membership.

**Output Example**: Calling count_vowels("Hello, World!") returns 3.

## FunctionDef pairwise_sum(numbers)
**pairwise_sum**: The function of pairwise_sum is to compute the sum of numbers from an iterable using Kahan summation for improved numerical stability.

**parameters**: The parameters of this Function.
· numbers: Any iterable of floats or ints.

**Code Description**: 
The function `pairwise_sum` takes an iterable of numbers (floats or ints) as input. It initializes `total` and `compensation` to 0.0. It then iterates through each `value` in the input `numbers`. Inside the loop, it converts the `value` to a float and subtracts the `compensation` from it, storing the result in `y`. It then adds `y` to the current `total` and stores the result in `t`. The `compensation` is updated to correct for floating-point errors. Finally, the function returns the accumulated `total`.

**Note**: This function uses Kahan summation to minimize floating-point errors, which can be significant when summing a large number of values with varying magnitudes.

**Output Example**: Calling pairwise_sum([1.0, 1e100, 1.0, -1e100]) returns 2.0.

## FunctionDef split_into_chunks(text, size)
**split_into_chunks**: The function of split_into_chunks is to split a given string into a tuple of substrings (chunks) of a specified size.

**parameters**: The parameters of this Function.
· text: The string that will be split into chunks.
· size: The desired length of each chunk.

**Code Description**: 
The function `split_into_chunks` takes a string `text` and an integer `size` as input. It first checks if the `size` is a positive number. If `size` is not positive, it raises a ValueError. If the size is valid, it uses a generator expression with string slicing to create chunks of the specified `size` from the input `text`. The generator expression iterates through the string `text` with a step of `size`, creating substrings from index `i` to `i + size`. Finally, it converts the generated sequence of substrings into a tuple and returns it. The last chunk may be shorter than `size` if the length of the input string is not a multiple of `size`.

**Note**: 
The function raises a ValueError if the provided size is not positive. The last element of the returned tuple may have a length less than size, if the original string's length is not a multiple of size.

**Output Example**: Calling split_into_chunks("abcdefgh", 3) returns ('abc', 'def', 'gh').

