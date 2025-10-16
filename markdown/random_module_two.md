## FunctionDef choose_random_item(items)
# Function: choose_random_item(items: List[str]) -> str

## Overview

The `choose_random_item` function selects and returns a single, uniformly random item from a given list of strings.

## parameters

- **items** (`List[str]`): A list of strings from which to choose a random item. This list must not be empty.

## Description

This function provides a safe way to select a random element from a list. The core logic is divided into two main steps: validation and selection.

First, the function validates the input list `items` by checking if it is empty with the condition `if not items:`. If the list is empty, it is impossible to choose an item, so the function raises a `ValueError` with the message "items must not be empty". This prevents potential errors from occurring in the selection process.

If the list is not empty, the function proceeds to the selection step. It utilizes the `random.choice()` method from Python's `random` module to pick a single element from the `items` list. The `random.choice()` method ensures that each item in the list has an equal probability of being selected. The chosen string is then returned as the result.

```python
# Internal logic example
import random

def choose_random_item(items: List[str]) -> str:
    # 1. Validate that the list is not empty
    if not items:
        raise ValueError("items must not be empty")
    # 2. Return a random choice from the list
    return random.choice(items)
```

## Usage Notes

- The input list `items` must not be empty. Providing an empty list will result in a `ValueError`.
- This function depends on Python's `random` module. Ensure it is available in the environment.
- The selection is uniformly random, meaning every item in the provided list has an equal chance of being chosen.

**Output Example**: The function returns a single string that was present in the input `items` list. For an input of `['red', 'green', 'blue']`, a possible return value is `'green'`.

## Example

```python
# Example usage
import random # This import is necessary for the function to work

fruit_list = ["apple", "banana", "cherry", "date"]
random_fruit = choose_random_item(fruit_list)
print(f"The randomly chosen fruit is: {random_fruit}")

# Example of what happens with an empty list
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
(Note: The chosen fruit in the first line of the output is random and will vary with each execution.)

***
## FunctionDef shuffle_copy(items)
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function creates and returns a new list containing the elements of the input list in a randomized order, without altering the original list.

## parameters

- **`items`** (List[int]): A list of integers to be shuffled.

## Description

This function provides a safe way to get a shuffled version of a list while preserving the original. The process is as follows:

1.  A shallow copy of the input `items` list is created using `copy = list(items)`. This is a crucial step to prevent modification of the original list that was passed as an argument.
2.  The `random.shuffle()` function is then called on the `copy`. This function shuffles the elements of the `copy` list in-place, rearranging them into a random sequence.
3.  Finally, the function returns the modified `copy`, which is now a shuffled version of the original `items` list.

```python
# Internal logic for an input of [1, 2, 3]
original_list = [1, 2, 3]
copy_of_list = list(original_list) # copy_of_list is now [1, 2, 3]
# random.shuffle(copy_of_list) modifies it in-place, e.g., to [3, 1, 2]
# The function then returns the shuffled copy_of_list
```

## Usage Notes

- **Non-Mutating:** The primary feature of this function is that it does not change the input `items` list. It operates on a copy, leaving the original data intact.
- **Random Module Dependency:** This function depends on Python's built-in `random` module. Ensure it is imported (e.g., `import random`) in the file where this function is used.
- **Shallow Copy:** The function creates a shallow copy. If the list contains mutable objects (like other lists or dictionaries), the objects themselves are not duplicated, only their references. For a list of simple types like integers, this behaves as a full, independent copy.

**Output Example**: A possible return value for an input of `[1, 2, 3, 4, 5]` could be:

```
[3, 5, 1, 4, 2]
```

## Example

```python
import random
from typing import List

def shuffle_copy(items: List[int]) -> List[int]:
    """Return a shuffled copy of the given list without mutating the input."""
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_numbers = [10, 20, 30, 40, 50]
shuffled_numbers = shuffle_copy(original_numbers)

print(f"Original List: {original_numbers}")
print(f"Shuffled Copy: {shuffled_numbers}")

# The original list remains unchanged
assert original_numbers == [10, 20, 30, 40, 50]
```

**Output:**

```
Original List: [10, 20, 30, 40, 50]
Shuffled Copy: [40, 10, 50, 20, 30]
```
*(Note: The actual order of the "Shuffled Copy" will vary with each execution due to its random nature.)*

***
