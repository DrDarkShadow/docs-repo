## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns a single random item from a given list of strings.

## parameters

- `items`: `List[str]` - A list of strings from which a single item will be randomly selected.

## Description

This function provides a simple way to get a random element from a list. The core logic is built around Python's standard `random` module.

First, the function validates the input `items` list. It checks if the list is empty using the condition `if not items:`. If the list is found to be empty, the function immediately stops execution and raises a `ValueError` with the message "items must not be empty". This check is crucial to prevent errors from the underlying `random.choice` function, which cannot operate on an empty sequence.

If the list is not empty, the function proceeds to call `random.choice(items)`. This method from the `random` library takes a non-empty sequence as an argument and returns a single item chosen uniformly at random. The selected string is then returned as the result of the `choose_random_item` function.

```python
# Internal logic for choosing an item
import random
# Assuming items = ['apple', 'banana', 'cherry']
chosen_item = random.choice(items)
# chosen_item will be one of 'apple', 'banana', or 'cherry'
```

## Usage Notes

- The input list `items` must not be empty. Providing an empty list will result in a `ValueError`.
- This function depends on Python's built-in `random` module. Ensure it is imported in the script where this function is called.
- The selection is uniformly random, meaning every item in the list has an equal probability of being chosen.

**Output Example**: A single string from the input list. For an input list `['apple', 'banana', 'cherry']`, a possible output is `'banana'`.

## Example

```python
import random
from typing import List

def choose_random_item(items: List[str]) -> str:
    """Choose a single random item from a non-empty sequence."""
    if not items:
        raise ValueError("items must not be empty")
    return random.choice(items)

# Example usage
fruits = ["apple", "banana", "cherry", "date", "elderberry"]
random_fruit = choose_random_item(fruits)
print(f"The randomly chosen fruit is: {random_fruit}")

# Example of error handling
try:
    choose_random_item([])
except ValueError as e:
    print(f"Error: {e}")
```

**Output:**

```
The randomly chosen fruit is: cherry
Error: items must not be empty
```
(Note: The specific fruit chosen in the output will vary with each execution due to its random nature.)

***
## FunctionDef shuffle_copy
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a shuffled copy of a given list without modifying the original input list.

## parameters

*   `items` (`List[int]`): A list of integers to be copied and shuffled.

## Description

This function provides a non-destructive way to shuffle the elements of a list. The internal logic operates in three steps:

1.  First, it creates a shallow copy of the input `items` list by calling `list(items)`. This ensures that any subsequent modifications do not affect the original list provided by the user.
2.  Next, it uses the `random.shuffle()` method to shuffle the newly created `copy` list. The `random.shuffle()` function modifies the sequence in-place, rearranging its elements into a random order.
3.  Finally, the function returns the `copy`, which now contains the same elements as the original `items` list but in a new, randomized order.

```python
# Internal logic example
import random
original_list = [10, 20, 30]
copy = list(original_list) # copy is [10, 20, 30]
random.shuffle(copy)       # copy might become [20, 30, 10]
# The function returns the 'copy'
```

## Usage Notes

- This function is guaranteed not to mutate the original `items` list. It is a "safe" operation for shuffling.
- The function requires the `random` module to be imported in the script where it is used.
- Although the type hint specifies `List[int]`, the function works correctly with lists containing elements of any data type (e.g., `str`, `float`, objects).

**Output Example**: The returned list will have the same length and elements as the input list. For an input of `[1, 2, 3]`, a possible output is `[3, 1, 2]`.

## Example

```python
import random

# Define the function (assuming it's in the same file or imported)
def shuffle_copy(items: list) -> list:
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_numbers = [1, 2, 3, 4, 5, 6]
print(f"Original list: {original_numbers}")

shuffled_list = shuffle_copy(original_numbers)
print(f"Shuffled copy: {shuffled_list}")

print(f"Original list after function call: {original_numbers}")
```

**Output:**

```
Original list: [1, 2, 3, 4, 5, 6]
Shuffled copy: [4, 1, 6, 3, 5, 2]
Original list after function call: [1, 2, 3, 4, 5, 6]
```
*(Note: The order of elements in "Shuffled copy" will vary with each execution due to its random nature.)*

***
