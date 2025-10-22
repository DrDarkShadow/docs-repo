## FunctionDef findMax(arr[], size)
# Function: findMax(int arr[], int size)

## Overview

The `findMax` function iterates through an array of integers to find and return the largest value.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers from which the maximum value will be found. |
| `size` | `int` | The total number of elements in the `arr` array. |

## Description

This function provides a straightforward way to determine the maximum value within an integer array.

The logic begins by initializing a local integer variable, `max`, with the value of the first element of the input array, `arr[0]`. This value serves as the initial benchmark for comparison.

Next, the function enters a `for` loop that iterates through the array, starting from the second element (at index `1`) up to the element just before the specified `size`. Inside the loop, each element `arr[i]` is compared to the current value stored in `max`. If the current element `arr[i]` is greater than `max`, the `max` variable is updated to hold this new, larger value.

After the loop completes, having checked all elements from the second to the last, the function returns the final value of `max`. This returned value is the largest integer found in the entire array.

## Usage Notes

- The input array `arr` must not be empty (i.e., `size` must be at least 1). The function assumes `arr[0]` is a valid element to initialize the `max` value. Passing an empty array will result in undefined behavior.
- The `size` parameter must accurately reflect the number of elements in the array to prevent out-of-bounds memory access and ensure correct results.

**Output Example**: The function returns a single integer representing the maximum value found in the array. For an input array `{10, 5, 45, 12, 8}`, the output would be `45`.

## Example

```python
#include <stdio.h>

// The findMax function definition
int findMax(int arr[], int size) {
    if (size <= 0) {
        // Handle empty or invalid array size
        return -1; // Or some other error indicator
    }
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max)
            max = arr[i];
    }
    return max;
}

// Example usage in a main function
int main() {
    int numbers[] = {10, 5, 45, 12, 8};
    int n = sizeof(numbers) / sizeof(numbers[0]);
    
    int maxValue = findMax(numbers, n);
    
    printf("The maximum value is: %d\n", maxValue);
    
    return 0;
}
```

**Output:**

```
The maximum value is: 45
```

***
## FunctionDef stringLength(str[])
# Function: stringLength

## Overview

The `stringLength` function calculates the length of a null-terminated string, excluding the final null character.

## parameters

- **`str`** `char[]`: The input character array (string) that must be null-terminated.

## Description

The `stringLength` function provides a manual implementation for determining the length of a C-style string. It operates by iterating through the characters of the input array until it finds the null terminator character (`'\0'`).

The function begins by initializing an integer variable `length` to `0`. This variable serves a dual purpose: it acts as an index to access characters in the `str` array and as a counter for the string's length.

A `while` loop forms the core of the function. The loop's condition checks if the character at the current index, `str[length]`, is not the null terminator `'\0'`.
- If the character is not `'\0'`, the loop body executes, incrementing `length` by one.
- This process continues, moving to the next character in the array in each iteration.

When the loop finally encounters the null terminator `'\0'`, the condition `str[length] != '\0'` becomes false, and the loop terminates. At this point, the value of `length` is equal to the number of characters that were read before the null terminator.

Finally, the function returns the integer value of `length`.

```c
// The loop iterates until the null character is found.
while (str[length] != '\0') {
    // The length counter is incremented for each character.
    length++;
}
// The final count is returned.
return length;
```

## Usage Notes

- The input array `str` **must** be a valid null-terminated string. Failure to provide a null terminator will cause the function to read beyond the buffer's boundary, leading to undefined behavior.
- The returned length does not include the null terminator character `'\0'`. For example, the string `"hi"` has a length of 2, but it occupies 3 bytes in memory (`'h'`, `'i'`, `'\0'`).
- An empty string `""` will correctly return a length of `0`.

**Output Example**: An integer representing the number of characters in the string. For the input `"example"`, the output would be `7`.

## Example

The following C code demonstrates how to use the `stringLength` function.

```c
#include <stdio.h>

// Assuming stringLength function is defined in the same file or included
int stringLength(char str[]) {
    int length = 0;
    while (str[length] != '\0') {
        length++;
    }
    return length;
}

int main() {
    char myString[] = "Hello, World!";
    int len = stringLength(myString);
    printf("The length of the string is: %d\n", len);

    char emptyString[] = "";
    int emptyLen = stringLength(emptyString);
    printf("The length of the empty string is: %d\n", emptyLen);

    return 0;
}
```

**Output:**

```
The length of the string is: 13
The length of the empty string is: 0
```

***
## FunctionDef getRandom(min, max)
# Function: getRandom(int min, int max)

## Overview

The `getRandom` function generates a pseudo-random integer within a specified inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `min` | int | The minimum possible value for the random number (inclusive). |
| `max` | int | The maximum possible value for the random number (inclusive). |

## Description

This function provides a reliable way to obtain a random integer between two boundary values, `min` and `max`.

The function first ensures that the range is valid. It checks if `min` is greater than `max`. If this condition is true, it swaps the values of `min` and `max` internally. This makes the function robust, as it will work correctly even if the arguments are passed in the wrong order.

The core logic for generating the random number is in the return statement: `return min + rand() % (max - min + 1);`.
- `rand()`: This standard C library function returns a pseudo-random integer.
- `(max - min + 1)`: This expression calculates the size of the desired range. For example, for a range from 5 to 10, this evaluates to `10 - 5 + 1 = 6`.
- `rand() % (max - min + 1)`: The modulo operator (`%`) constrains the result of `rand()` to a number between `0` and `max - min`.
- `min + ...`: This adds the `min` value to the result, effectively shifting the range from `[0, max - min]` to `[min, max]`.

## Usage Notes

- The range is inclusive, meaning both the `min` and `max` values are potential return values.
- The function automatically handles cases where `min > max` by swapping the values.
- For `rand()` to produce different sequences of numbers each time the program runs, it must be seeded. This is typically done once at the start of the program (e.g., in `main`) by calling `srand(time(NULL))`. You must include the `<stdlib.h>` and `<time.h>` headers for this.

**Output Example**: A single integer value within the specified range. For `getRandom(1, 100)`, a possible output is `42`.

## Example

The following C code demonstrates how to use the `getRandom` function. It includes the necessary seeding for the random number generator.

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Definition of the getRandom function
int getRandom(int min, int max) {
    if (min > max) {
        int temp = min;
        min = max;
        max = temp;
    }
    return min + rand() % (max - min + 1);
}

int main() {
    // Seed the random number generator once at the beginning
    srand(time(NULL));

    int min_val = 1;
    int max_val = 10;

    // Generate and print a random number between 1 and 10
    int random_number = getRandom(min_val, max_val);
    printf("A random number between %d and %d is: %d\n", min_val, max_val, random_number);

    return 0;
}
```

**Output:**

(The actual output will vary on each execution)
```
A random number between 1 and 10 is: 7
```

***
## FunctionDef isPrime(n)
# Function: isPrime(int n)

## Overview

The `isPrime` function determines whether a given integer is a prime number.

## Parameters

- `n`: The integer to be checked for primality.

## Description

This function provides an efficient method to check if an integer `n` is a prime number.

The logic begins by handling the base cases. According to the definition of prime numbers, any integer less than or equal to 1 is not prime. The function first checks if `n <= 1` and, if this condition is met, it immediately returns `false`.

If `n` is greater than 1, the function proceeds to check for factors. It iterates through integers starting from `i = 2` up to the square root of `n`. The loop condition `i * i <= n` is an optimization that avoids checking divisors beyond the square root of `n`, as any factor larger than the square root would have a corresponding factor smaller than it.

Inside the loop, it uses the modulo operator (`%`) to check if `n` is perfectly divisible by the current integer `i`. If `n % i == 0` is true, it means a factor other than 1 and `n` has been found, so `n` is not a prime number. In this case, the function returns `false` and terminates.

If the loop completes without finding any factors, it confirms that `n` is only divisible by 1 and itself, thus it is a prime number, and the function returns `true`.

## Usage Notes

- Numbers less than or equal to 1 will always return `false`.
- The function returns a boolean value: `true` if the number is prime, and `false` otherwise.
- This implementation is optimized to check for divisors only up to the square root of the input number, making it efficient.

**Output Example**: The function returns a boolean value, which in C might be represented as `1` (for true) or `0` (for false) when printed or used in integer contexts.

## Example

```c
#include <stdio.h>
#include <stdbool.h>

// Assuming the isPrime function is defined here or included
bool isPrime(int n) {
    if (n <= 1)
        return false;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0)
            return false;
    }
    return true;
}

int main() {
    int num1 = 29;
    int num2 = 10;

    bool result1 = isPrime(num1);
    bool result2 = isPrime(num2);

    printf("Is %d a prime number? %s\n", num1, result1 ? "true" : "false");
    printf("Is %d a prime number? %s\n", num2, result2 ? "true" : "false");

    return 0;
}
```

**Output:**

```
Is 29 a prime number? true
Is 10 a prime number? false
```

***
## FunctionDef main
# Function: main

## Overview

The `main` function serves as the entry point for the program, demonstrating the usage of several utility functions to find a maximum value in an array, calculate string length, and determine if a number is prime.

## parameters

This function does not take any parameters.

## Description

The `main` function executes a sequence of demonstrations for other utility functions.

1.  **Find Maximum in Array**:
    - An integer array `nums` is initialized with the values `{5, 12, 3, 19, 7}`.
    - The `size` of the array is calculated by dividing the total size of the array in bytes (`sizeof(nums)`) by the size of a single integer element (`sizeof(nums[0])`).
    - The `findMax` function is called with `nums` and `size` as arguments. The returned value, which is the largest number in the array, is then printed to the console.

2.  **Calculate String Length**:
    - A character array `name` is initialized with the string `"Prateek"`.
    - The `stringLength` function is called with the `name` array. The function returns the number of characters in the string, which is then printed.

3.  **Prime Number Check**:
    - An integer variable `number` is initialized with the value `17`.
    - The `isPrime` function is called with `number`. The function returns a boolean-like value (true or false).
    - An `if-else` block checks the return value and prints a message indicating whether `17` is a prime number or not.

Finally, the function returns `0` to the operating system, which conventionally signifies that the program executed successfully without errors.

## Usage Notes

- This `main` function is a driver function, designed to showcase the functionality of `findMax`, `stringLength`, and `isPrime`.
- For this code to compile and run, the implementations for `findMax`, `stringLength`, and `isPrime` must be available and linked.
- The program requires the `<stdio.h>` header for the `printf` function.

**Output Example**: A possible console output from running the program.

```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

## Example

The `main` function is the entry point of a C program and is not called by other functions within the code. It is executed when the compiled program is run. To use it, you would compile the source file and run the resulting executable.

```c
// Assuming the code is in a file named 'program.c'
// and the helper functions are also defined.

// 1. Compile the code using a C compiler like GCC
// > gcc program.c -o program

// 2. Run the executable
// > ./program
```

**Output:**

```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

***
