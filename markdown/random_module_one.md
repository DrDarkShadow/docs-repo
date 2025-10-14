## FunctionDef num(a, b)
# Function: num

## Overview

The `num` function calculates and returns the sum of two input values.

## parameters

| Parameter | Type      | Description                |
|-----------|-----------|----------------------------|
| `a`       | int/float | The first number to be added. |
| `b`       | int/float | The second number to be added. |

## Description

This function provides a straightforward way to perform addition. It accepts two parameters, `a` and `b`, and computes their sum using the `+` operator. The result of this operation is then returned by the function. The primary use case is for numeric addition, but it will also work with any data types that support the addition operator, such as string concatenation.

```python
# The function adds 'a' and 'b' and returns the result.
return a + b
```

## Usage Notes

- This function is designed for numeric types like integers (`int`) and floating-point numbers (`float`).
- If strings are passed as arguments, the function will perform string concatenation instead of mathematical addition. For example, `num("hello", " world")` would return `"hello world"`.
- Passing incompatible types (e.g., an integer and a string) will result in a `TypeError`.

**Output Example**: A numeric value representing the sum.
`15`

## Example

```python
# Example usage with integers
result = num(5, 10)
print(result)

# Example usage with floating-point numbers
float_result = num(7.5, 2.2)
print(float_result)
```

**Output:**

```
15
9.7
```

***
## FunctionDef generate_random_integers(count, start, end)
# Function: generate_random_integers

## Overview

The `generate_random_integers` function creates and returns a list of a specified number of pseudo-random integers within a defined inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `count` | int | The number of random integers to generate. This value must be non-negative. |
| `start` | int | The inclusive lower bound for the random number generation. Defaults to `0`. |
| `end` | int | The inclusive upper bound for the random number generation. Defaults to `100`. |

## Description

This function provides a convenient way to generate a list of pseudo-random integers. It takes three parameters: `count`, `start`, and `end`.

The function first validates the `count` parameter. If `count` is a negative number, it raises a `ValueError` because it's not possible to generate a negative quantity of integers.

Next, it ensures the range is valid by comparing `start` and `end`. If the provided `start` value is greater than the `end` value, the function automatically swaps them. This allows the user to specify the range boundaries without concern for their order.

Finally, it uses a list comprehension to call the `random.randint(start, end)` function `count` times. Each call generates a single integer uniformly sampled from the inclusive range `[start, end]`. These integers are collected into a list, which is then returned.

```python
# Internal logic for generating the list
return [random.randint(start, end) for _ in range(count)]
```

## Usage Notes

- The function will raise a `ValueError` if the `count` argument is less than 0.
- If the `start` value is greater than the `end` value, the function will automatically swap them to form a valid range.
- The generated integers are within an inclusive range, meaning both the `start` and `end` values can be present in the output list.
- This function relies on Python's built-in `random` module.

**Output Example**: A list of integers.

```
[45, 8, 92, 33, 67]
```

## Example

```python
# Example: Generate 5 random integers between 10 and 20 (inclusive).
random_numbers = generate_random_integers(5, 10, 20)
print(random_numbers)

# Example: Generate 3 random integers with default range (0 to 100).
random_numbers_default = generate_random_integers(3)
print(random_numbers_default)

# Example: The function automatically corrects the range if start > end.
# This is equivalent to generate_random_integers(4, 50, 60).
random_numbers_swapped = generate_random_integers(4, 60, 50)
print(random_numbers_swapped)
```

**Output:**

```
# The output will be random, but will look similar to this:
[18, 11, 20, 15, 10]
[76, 2, 81]
[55, 59, 51, 58]
```

***
## FunctionDef choose_random_item(items)
# Function: choose_random_item

## Overview

The `choose_random_item` function selects and returns a single random item from a given list of strings.

## parameters

- `items`: `List[str]` - A non-empty list of strings from which to choose a random item.

## Description

This function provides a simple way to get a random element from a list of strings. The core logic relies on Python's built-in `random` module.

First, the function performs a crucial validation check to ensure the input list `items` is not empty. If an empty list is passed (`if not items`), the function immediately raises a `ValueError` to prevent runtime errors and inform the developer of the invalid input.

If the list is valid (i.e., contains at least one element), the function then calls `random.choice(items)`. This standard library method selects a single item from the sequence with uniform probability, meaning every item has an equal chance of being chosen. The selected string is then returned as the result.

```python
# Internal logic for selecting an item
import random
items_list = ["apple", "banana", "cherry"]
# The function effectively does this:
selected_item = random.choice(items_list)
```

## Usage Notes

- The input list `items` must not be empty. Providing an empty list will result in a `ValueError`.
- The function depends on Python's `random` module. Ensure it is available in the execution environment.
- The selection is uniformly random. Each item in the list has an equal probability of being returned.

**Output Example**: A single string from the input list.

```
'banana'
```

## Example

```python
# Example usage
import random # Required for the function to work

# Define a list of items
fruit_options = ["apple", "banana", "cherry", "date"]

# Call the function to get a random fruit
random_fruit = choose_random_item(fruit_options)

print(f"The randomly chosen fruit is: {random_fruit}")
```

**Output:**

```
# The output will vary with each execution. A possible output is:
The randomly chosen fruit is: cherry
```

***
## FunctionDef shuffle_copy(items)
# Function: shuffle_copy

## Overview

The `shuffle_copy` Function returns a new, randomly shuffled copy of a given list, ensuring the original list remains unchanged.

## parameters

- **items** (`List[int]`): A list of integers that will be copied and shuffled.

## Description

This function provides a safe way to shuffle a list without altering the original data structure. The process involves three main steps:

1.  A shallow copy of the input `items` list is created using the `list()` constructor. This new list is assigned to the `copy` variable. This step is critical to ensure that any subsequent modifications do not affect the original list passed to the function.

2.  The `random.shuffle()` function is then called on the `copy`. This function shuffles the elements of the list *in-place*, rearranging them into a random order.

3.  Finally, the function returns the modified `copy`, which now contains the same elements as the original list but in a new, randomized sequence.

```python
# Internal logic demonstration
import random

original_items = [10, 20, 30, 40]

# 1. Create a copy
copy = list(original_items)
# copy is now [10, 20, 30, 40], but is a different object in memory

# 2. Shuffle the copy in-place
random.shuffle(copy)
# copy might now be [30, 10, 40, 20]

# 3. Return the shuffled copy
# The function returns [30, 10, 40, 20]
# The original_items list remains [10, 20, 30, 40]
```

## Usage Notes

- The primary benefit of this function is that it is non-mutating. The original list you pass as an argument will not be changed.
- This function depends on Python's built-in `random` module. Ensure it is available in the environment.
- The returned list is a new list instance, separate from the input list.
- The shuffling is pseudo-random, meaning the sequence is generated by a deterministic algorithm but is practically unpredictable.

**Output Example**: A new list containing the same elements as the input `items` list, but in a random order. For an input of `[1, 2, 3]`, a possible output could be `[2, 3, 1]`.

## Example

```python
import random

# Assume shuffle_copy is defined as in the provided code
def shuffle_copy(items: list) -> list:
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
my_numbers = [1, 2, 3, 4, 5, 6]
shuffled_numbers = shuffle_copy(my_numbers)

print(f"Original List: {my_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")

# Another example
source_data = [100, 200, 300]
randomized_data = shuffle_copy(source_data)

print(f"\nOriginal Data: {source_data}")
print(f"Randomized Data: {randomized_data}")
```

**Output:**

```
Original List: [1, 2, 3, 4, 5, 6]
Shuffled Copy: [4, 1, 6, 3, 5, 2]

Original Data: [100, 200, 300]
Randomized Data: [200, 300, 100]
```
*(Note: The actual output of the shuffled lists will vary with each execution due to the nature of random shuffling.)*

***
