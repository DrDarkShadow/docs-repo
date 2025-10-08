## FunctionDef count_vowels(text)
count_vowels: The function of count_vowels is to count the number of vowels (a, e, i, o, u) in a given string, case-insensitively.
parameters: The parameters of this Function.
· text: Input string to scan.
Code Description: The code first defines a set of vowels, both lowercase and uppercase. Then, it iterates through the input string `text`, checking if each character is present in the `vowels` set. If a character is a vowel, the sum is incremented by 1. Finally, the function returns the total count of vowels found in the string.
Note: The function considers both uppercase and lowercase vowels.

## FunctionDef pairwise_sum(numbers)
pairwise_sum: The function of pairwise_sum is to compute the sum of numbers from an iterable in a numerically stable way, using Kahan summation to reduce floating-point errors.
parameters: The parameters of this Function.
· numbers: Any iterable of floats or ints.
Code Description: The function `pairwise_sum` takes an iterable of numbers (floats or ints) as input. It initializes `total` and `compensation` to 0.0. It then iterates through the input `numbers`. In each iteration, it converts the current `value` to a float, calculates `y` as the difference between the float value and the current `compensation`. It then calculates a tentative sum `t` as the sum of `total` and `y`. The `compensation` is updated to correct for floating-point errors. Finally, the `total` is updated to the tentative sum `t`. The function returns the final `total`, which represents the numerically stable sum of the input numbers.
Note: The function uses Kahan summation to improve the accuracy of the sum, especially when dealing with a large number of floating-point values that may have varying magnitudes. This approach reduces the accumulation of rounding errors that can occur with naive summation.

## FunctionDef split_into_chunks(text, size)
split_into_chunks: The function of split_into_chunks is to split a given string into fixed-size chunks and return them as a tuple.
parameters: The parameters of this Function.
· text: The string to be split into chunks.
· size: The desired length of each chunk.
Code Description: The function `split_into_chunks` takes a string `text` and an integer `size` as input. It first checks if the `size` is positive. If `size` is not positive, it raises a ValueError. Otherwise, it uses a generator expression with string slicing to split the input `text` into chunks of the specified `size`. The `range` function with a step of `size` is used to iterate through the string, and each chunk `text[i : i + size]` is extracted. Finally, the generator expression is converted into a tuple, which is then returned. The last chunk may be shorter than `size` if the length of the input string is not a multiple of `size`.
Note: The `size` parameter must be a positive integer. If it is not, a ValueError is raised. The function returns a tuple of strings.
END DOCUMENTATION FOR: split_into_chunks

