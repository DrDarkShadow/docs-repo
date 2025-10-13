## FunctionDef count_vowels(text)
Doc is waiting to be generated...
## FunctionDef pairwise_sum(numbers)
**pairwise_sum**: The function of pairwise_sum is to compute the sum of numbers from an iterable using Kahan summation for improved numerical stability.

**parameters**: The parameters of this Function.
· numbers: Any iterable of floats or ints.

**Code Description**: 
The function `pairwise_sum` calculates the sum of a sequence of numbers in a way that minimizes floating-point errors. It initializes `total` and `compensation` to 0.0. It then iterates through each `value` in the input `numbers` iterable. Inside the loop, it converts the current `value` to a float and subtracts the `compensation` from it, storing the result in `y`. It then adds `y` to the current `total` and stores the result in `t`. The `compensation` is updated to correct for the floating-point error introduced in the addition. Finally, the `total` is updated with the value of `t`. After processing all numbers, the function returns the final `total`.

**Note**: This function uses Kahan summation to reduce the accumulation of floating-point errors, which can be significant when summing a large number of values with varying magnitudes.

**Output Example**: Calling pairwise_sum([1.0, 1.0e10, 1.0, -1.0e10]) returns 2.0, whereas a naive sum might return 0.0 due to floating point precision issues.

## FunctionDef split_into_chunks(text, size)
**split_into_chunks**: The function of split_into_chunks is to split a given string into a tuple of fixed-size substrings (chunks).

**parameters**: The parameters of this Function.
· text: The string to be split into chunks.
· size: The desired length of each chunk.

**Code Description**: 
The function first checks if the provided `size` is a positive number. If `size` is not positive, it raises a ValueError. Otherwise, it uses a generator expression and string slicing to create substrings of length `size` from the input `text`. The generator expression iterates through the `text` with a step of `size`, creating slices from `i` to `i + size`. Finally, the function converts the generated sequence of substrings into a tuple and returns it. The last chunk may be shorter than `size` if the length of the input `text` is not a multiple of `size`.

**Note**: 
The function raises a ValueError if the size is not positive. The last chunk in the tuple may be shorter than the specified size if the input string's length is not a multiple of the size.

**Output Example**: Calling split_into_chunks("abcdefgh", 3) returns ('abc', 'def', 'gh').

