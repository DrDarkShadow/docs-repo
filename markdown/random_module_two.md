## FunctionDef choose_random_item
# Function: choose_random_item(items: List[str])

## Overview

The `choose_random_item` function selects and returns a single random item from a given list of strings.

## parameters

- **`items`** (`List[str]`): A non-empty list of strings from which a random item will be chosen.

## Description

This function provides a simple way to get a random element from a list. The core logic is handled by Python's built-in `random.choice()` method.

Before attempting to select an item, the function first validates the input list `items`. It checks if the list is empty using the condition `if not items:`. If the list is found to be empty, the function immediately raises a `ValueError` with the message "items must not be empty". This prevents runtime errors that would occur if `random.choice()` were called with an empty sequence.

If the list is not empty, the function proceeds to call `random.choice(items)`. This method selects a single item from the list with uniform probability, meaning each item has an equal chance of being chosen. The selected string is then returned as the result.

```python
# Internal logic example
import random

def choose_random_item(items: list[str]) -> str:
    # 1. Check if the list is empty
    if not items:
        # 2. Raise an error if it is
        raise ValueError("items must not be empty")
    # 3. Return a random choice if it's not empty
    return random.choice(items)
```

## Usage Notes

- The input list `items` must not be empty. Providing an empty list will result in a `ValueError`.
- This function relies on Python's `random` module. Ensure it is imported in the environment where the function is used.
- The selection is uniformly random, meaning every item in the list has an equal chance of being chosen on any given call.

**Output Example**: A single string from the input list.

```
"example_string"
```

## Example

```python
# Example usage
import random # This import is necessary for the function to work

# Define a list of options
options = ["apple", "banana", "cherry", "date", "elderberry"]

# Call the function with the list
selected_item = choose_random_item(options)

# Print the result
print(f"The randomly selected item is: {selected_item}")
```

**Output:**

```
The randomly selected item is: cherry
```
*(Note: The actual output will be one of the items from the `options` list, chosen randomly.)*

***
## FunctionDef shuffle_copy
# Function: shuffle_copy(items: List[int])

## Overview

The `shuffle_copy` function returns a new, randomly shuffled copy of a given list, ensuring the original list remains unchanged.

## parameters

- **`items`** (`List[int]`): The list of integers that you want to create a shuffled copy of.

## Description

This function provides a safe way to shuffle a list without altering the original data structure. The process involves three main steps:

1.  A shallow copy of the input `items` list is created using `copy = list(items)`. This is a critical step that isolates the operation from the original list, preventing its mutation.
2.  The `random.shuffle()` method is then called on this `copy`. This function shuffles the elements of the list in-place, rearranging them into a random order.
3.  Finally, the function returns the `copy`, which now contains the same elements as the original `items` list but in a new, randomized sequence.

```python
# Internal logic of the function
import random

# 1. A shallow copy of the input list is created.
copy = list(items)

# 2. The copy is shuffled in-place.
random.shuffle(copy)

# 3. The shuffled copy is returned.
return copy
```

## Usage Notes

- This function is non-mutating. The original list passed as the `items` parameter will not be modified.
- The function requires the `random` module to be imported in the script where it is used.
- The order of elements in the returned list is non-deterministic and will likely be different on each execution.

**Output Example**: A possible return value for an input of `[1, 2, 3]` could be:

```
[2, 1, 3]
```

## Example

```python
import random
from typing import List

# The function must be defined or imported
def shuffle_copy(items: List[int]) -> List[int]:
    """Return a shuffled copy of the given list without mutating the input."""
    copy = list(items)
    random.shuffle(copy)
    return copy

# Example usage
original_list = [10, 20, 30, 40, 50]
shuffled_list = shuffle_copy(original_list)

print(f"Original List: {original_list}")
print(f"Shuffled Copy: {shuffled_list}")
```

**Output:**

```
Original List: [10, 20, 30, 40, 50]
Shuffled Copy: [30, 50, 10, 20, 40]
```

***
