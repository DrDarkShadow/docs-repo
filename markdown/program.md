## FunctionDef findMax(arr[], size)
# Function: findMax(int arr[], int size)

## Overview

The `findMax` function iterates through an array of integers to find and return the largest value.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers from which the maximum value will be found. |
| `size` | `int` | The total number of elements in the `arr`. |

## Description

This function provides a straightforward method for identifying the maximum value within an integer array.

The process begins by initializing a variable `max` with the value of the first element of the array, `arr[0]`. This sets an initial benchmark for comparison.

Next, the function enters a `for` loop that iterates through the array, starting from the second element (at index `1`) up to the element just before the specified `size`. Inside the loop, each element `arr[i]` is compared to the current value of `max`. If `arr[i]` is found to be greater than `max`, the `max` variable is updated with the value of this new larger element.

After the loop completes, having checked all elements from the second to the last, the `max` variable holds the largest value found in the array. This final value is then returned by the function.

## Usage Notes

- The caller is responsible for providing an accurate `size` that matches the actual number of elements in `arr`. An incorrect size can lead to out-of-bounds memory access and undefined behavior.
- This function assumes the array is not empty (i.e., `size` is at least 1). Calling it with an empty array (`size = 0`) will cause an attempt to access `arr[0]`, resulting in undefined behavior.
- The function correctly handles arrays containing both positive and negative integers.

**Output Example**: A single integer representing the maximum value.

## Example

The following C code demonstrates how to use the `findMax` function.

```c
#include <stdio.h>

// Assuming findMax is defined in the same file or included
int findMax(int arr[], int size);

int main() {
    int numbers[] = {-10, 5, 100, -2, 50, 99};
    int array_size = 6;
    int result = findMax(numbers, array_size);
    printf("The maximum value is: %d\n", result);
    return 0;
}

// Definition of the findMax function
int findMax(int arr[], int size) {
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max)
            max = arr[i];
    }
    return max;
}
```

**Output:**

```
The maximum value is: 100
```

***
## FunctionDef findMin(arr[], size)
# Function: findMin(int arr[], int size)

## Overview

The `findMin` function iterates through an array of integers to find and return the smallest value.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers from which to find the minimum value. |
| `size` | `int` | The number of elements in the array `arr`. |

## Description

This function provides a straightforward method for finding the minimum element within an integer array.

The logic begins by initializing a local variable `min` with the value of the first element of the array, `arr[0]`. This variable acts as a temporary placeholder for the smallest value found so far.

The function then enters a `for` loop that iterates through the array, starting from the second element (`i = 1`) and continuing until it has checked all elements up to the index `size - 1`. Inside the loop, each element `arr[i]` is compared to the current value of `min`. If `arr[i]` is less than `min`, it means a new, smaller value has been found, and `min` is updated to `arr[i]`.

After the loop has finished iterating through all the elements, the final value stored in the `min` variable is the smallest integer in the entire array. This value is then returned by the function.

## Usage Notes

- The array `arr` should not be empty. The function accesses `arr[0]` without checking if `size` is greater than 0. Passing an empty array (with `size` as 0) will result in undefined behavior.
- The `size` parameter must accurately represent the number of elements in the array. Providing a `size` larger than the actual array length will cause the function to read from memory outside the array's bounds.
- The function is designed to work with both positive and negative integers.

**Output Example**: The function returns a single integer representing the minimum value found. For an input array `{5, 12, 2, 8}`, the output would be `2`.

## Example

The following C code demonstrates how to use the `findMin` function.

```c
#include <stdio.h>

// Assuming findMin is defined in the same file or included
int findMin(int arr[], int size) {
    int min = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < min)
            min = arr[i];
    }
    return min;
}

int main() {
    int numbers[] = {45, 21, 8, 97, 12, -5, 34};
    int array_size = sizeof(numbers) / sizeof(numbers[0]);
    
    int minimum_value = findMin(numbers, array_size);
    
    printf("The minimum value in the array is: %d\n", minimum_value);
    
    return 0;
}
```

**Output:**

```
The minimum value in the array is: -5
```

***
## FunctionDef calculateAverage(arr[], size)
# Function: calculateAverage(int arr[], int size)

## Overview

The `calculateAverage` function computes the arithmetic mean of the elements in a given integer array.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers for which the average will be calculated. |
| `size` | `int` | The total number of elements in the `arr` array. |

## Description

This function provides a straightforward way to calculate the average of a set of integers. The logic operates in a few key steps:

1.  A local integer variable `sum` is initialized to `0`. This variable will be used to accumulate the total sum of all array elements.
2.  The function then enters a `for` loop, which iterates from `i = 0` up to, but not including, the `size` of the array. This ensures that every element is processed.
3.  Inside the loop, the value of the current element `arr[i]` is added to the `sum`.
4.  After the loop completes, `sum` holds the total of all integers in the array.
5.  The function returns the final average by dividing the `sum` by the `size`. Crucially, the `sum` is cast to a `double` using `(double)sum` before the division. This forces a floating-point division, ensuring that the result is a precise decimal value rather than an integer, which would truncate any fractional part.

```c
// The core calculation logic
return (double)sum / size;
```

## Usage Notes

- The `size` parameter must accurately reflect the number of elements in the `arr`. Providing a `size` larger than the array's capacity will result in reading from out-of-bounds memory, leading to undefined behavior.
- If `size` is `0`, the function will perform a division by zero. This is undefined behavior in C and can cause a program crash. The caller should ensure the array is not empty before calling this function.
- The function returns a `double` to maintain precision. The variable receiving the result should also be of a floating-point type (e.g., `double` or `float`) to correctly store the value.

**Output Example**: A floating-point number representing the average. For an input array `{2, 3, 5, 7}`, the sum is 17 and the size is 4, so the output would be `4.25`.

## Example

```c
#include <stdio.h>

double calculateAverage(int arr[], int size) {
    if (size == 0) {
        return 0.0; // Handle empty array case
    }
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return (double)sum / size;
}

int main() {
    int numbers[] = {2, 3, 5, 7, 11};
    int count = sizeof(numbers) / sizeof(numbers[0]);
    
    double average = calculateAverage(numbers, count);
    
    printf("The average is: %f\n", average);
    
    return 0;
}
```

**Output:**

```
The average is: 5.600000
```

***
## FunctionDef stringLength(str[])
# Function: stringLength(char str[])

## Overview

The `stringLength` function calculates and returns the length of a null-terminated string.

## parameters

- **`str`** (`char[]`): A character array representing the string whose length is to be calculated. This array must be terminated with a null character (`\0`).

## Description

This function provides a manual implementation for determining the length of a string in C. The core logic relies on the C language convention that strings are sequences of characters stored in an array, with the end of the string marked by a special null character, `\0`.

The function initializes an integer variable `length` to `0`. This variable serves a dual purpose: it acts as a counter for the string's length and as an index to access characters within the `str` array.

A `while` loop is used to iterate through the array. The loop's condition, `str[length] != '\0'`, checks if the character at the current index is the null terminator. As long as the character is not `\0`, the loop continues. Inside the loop, the `length` variable is incremented with `length++`. This process effectively counts each character in the string.

When the loop encounters the null terminator, the condition becomes false, and the loop terminates. At this point, the value of `length` is equal to the number of characters that were traversed before reaching the end of the string. This final count, which is the length of the string, is then returned by the function.

## Usage Notes

- The input character array `str` must be properly null-terminated. Failure to do so will result in the function reading beyond the array's bounds, leading to undefined behavior.
- The length returned by the function does not include the final null terminator character (`\0`).
- The function provides a read-only operation and does not modify the input string.

**Output Example**: The function returns an integer representing the number of characters in the string. For the input `"Hello"`, the function would return:
`5`

## Example

```c
#include <stdio.h>

/*
  stringLength function definition.
*/
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
    printf("The length of the string \"%s\" is %d.\n", myString, len);

    char emptyString[] = "";
    len = stringLength(emptyString);
    printf("The length of an empty string is %d.\n", len);

    return 0;
}
```

**Output:**

```
The length of the string "Hello, World!" is 13.
The length of an empty string is 0.
```

***
## FunctionDef getRandom(min, max)
# Function: getRandom(int min, int max)

## Overview

The `getRandom` function generates a pseudo-random integer within a specified inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `min` | int | The minimum possible value for the random number. |
| `max` | int | The maximum possible value for the random number. |

## Description

This function calculates and returns a pseudo-random integer that falls between the `min` and `max` values, inclusive.

The function first checks if the `min` parameter is greater than the `max` parameter. If it is, the values are swapped to ensure that `min` is always the lower bound and `max` is the upper bound. This makes the function robust against incorrect argument order.

The core of the function is the expression `min + rand() % (max - min + 1)`. Let's break it down:
1.  `rand()`: This is a standard C library function that returns a pseudo-random integer.
2.  `(max - min + 1)`: This calculates the size of the desired range. For example, if `min` is 5 and `max` is 10, the range size is `10 - 5 + 1 = 6`.
3.  `rand() % (max - min + 1)`: The modulo operator (`%`) constrains the result of `rand()` to a number between `0` and `max - min`.
4.  `min + ...`: This result is then added to `min`, effectively shifting the range to start at `min`. This ensures the final number is within the `[min, max]` inclusive range.

```c
// If min = 10 and max = 20
// The range size is (20 - 10 + 1) = 11
// rand() % 11 produces a number from 0 to 10
// 10 + (a number from 0 to 10) produces a result from 10 to 20
return 10 + rand() % 11;
```

## Usage Notes

- This function relies on the standard C library function `rand()`. For the sequence of random numbers to be different on each program execution, the pseudo-random number generator must be seeded. This is typically done once at the beginning of the program using `srand(time(NULL))`.
- The function gracefully handles cases where `min` is greater than `max` by swapping the values internally.
- You must include the `<stdlib.h>` header to use the `rand()` and `srand()` functions. For seeding with `time()`, `<time.h>` is also required.

**Output Example**: A pseudo-random integer between `min` and `max` (inclusive).

## Example

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// The function to be documented
int getRandom(int min, int max) {
    if (min > max) {
        int temp = min;
        min = max;
        max = temp;
    }
    return min + rand() % (max - min + 1);
}

int main() {
    // Seed the random number generator once at the start of the program
    srand(time(NULL));

    // Example usage: Get a random number between 1 and 100
    int randomNumber = getRandom(1, 100);
    printf("A random number between 1 and 100: %d\n", randomNumber);

    // Example with swapped arguments
    int anotherRandomNumber = getRandom(50, 20);
    printf("A random number between 20 and 50: %d\n", anotherRandomNumber);

    return 0;
}
```

**Output:**

(Note: The actual output will vary with each execution)
```
A random number between 1 and 100: 42
A random number between 20 and 50: 35
```

***
## FunctionDef isPrime(n)
# Function: isPrime

## Overview

The `isPrime` function determines whether a given integer is a prime number.

## parameters

- `n`: An `int` representing the integer to be checked for primality.

## Description

This function provides an efficient method to check if an integer `n` is a prime number.

The logic begins by handling the base cases. According to the definition of prime numbers, any integer less than or equal to 1 is not prime. The function first checks if `n <= 1` and, if this condition is true, it immediately returns `false`.

If `n` is greater than 1, the function proceeds to check for factors. It iterates through integers starting from `i = 2` up to the square root of `n`. The loop condition `i * i <= n` is an optimization that avoids redundant checks; if a number `n` has a factor larger than its square root, it must also have a corresponding factor smaller than its square root.

Inside the loop, the modulo operator (`%`) is used to check if `n` is evenly divisible by the current integer `i`. If `n % i == 0` is true, it means a factor has been found, and `n` cannot be prime. In this case, the function returns `false` and terminates.

If the loop completes without finding any factors, it confirms that `n` is not divisible by any integer between 2 and its square root. Therefore, `n` is a prime number, and the function returns `true`.

## Usage Notes

- The function returns a boolean value: `true` if the number is prime, and `false` otherwise.
- Integers less than or equal to 1 (e.g., 1, 0, -10) are not considered prime and will result in a `false` return value.
- This implementation is efficient for checking primality of moderately large integers.

**Output Example**: The function returns a `bool` value. For a prime number input, the output would be:
`true`

## Example

```c
#include <stdio.h>
#include <stdbool.h>

// Definition of isPrime function
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
    int number1 = 29;
    int number2 = 10;

    // Using a ternary operator to print the result
    printf("%d is prime? %s\n", number1, isPrime(number1) ? "true" : "false");
    printf("%d is prime? %s\n", number2, isPrime(number2) ? "true" : "false");

    return 0;
}
```

**Output:**

```
29 is prime? true
10 is prime? false
```

***
## FunctionDef main
# Function: main

## Overview

The `main` function serves as the entry point for the C program, demonstrating the usage of three distinct utility functions: `findMax`, `stringLength`, and `isPrime`.

## parameters

This function does not accept any parameters.

## Description

The `main` function executes a sequence of operations to showcase other functions' capabilities. Its logic is as follows:

1.  **Find Maximum in an Array**:
    *   An integer array named `nums` is initialized with the values `{5, 12, 3, 19, 7}`.
    *   The number of elements in the array is calculated and stored in the `size` variable. This is achieved by dividing the total size of the array (`sizeof(nums)`) by the size of a single element (`sizeof(nums[0])`).
    *   It calls the `findMax` function, passing the `nums` array and its `size`. The returned maximum value is then printed to the console.

    ```c
    int nums[] = {5, 12, 3, 19, 7};
    int size = sizeof(nums) / sizeof(nums[0]);
    printf("Maximum number: %d\n", findMax(nums, size));
    ```

2.  **Calculate String Length**:
    *   A character array `name` is initialized with the string "Prateek".
    *   It calls the `stringLength` function with the `name` array. The returned length is then printed to the console.

    ```c
    char name[] = "Prateek";
    printf("Length of '%s': %d\n", name, stringLength(name));
    ```

3.  **Check for Prime Number**:
    *   An integer variable `number` is initialized with the value `17`.
    *   The `isPrime` function is called with `number` to determine if it is a prime number.
    *   An `if-else` block checks the boolean result from `isPrime` and prints a message to the console, indicating whether `17` is prime or not.

    ```c
    int number = 17;
    if (isPrime(number))
        printf("%d is a prime number.\n", number);
    else
        printf("%d is not a prime number.\n", number);
    ```

Finally, the function returns `0`, signaling successful execution to the operating system.

## Usage Notes

- This function is the standard entry point for execution in a C program.
- It depends on the external functions `findMax`, `stringLength`, and `isPrime`. These functions must be defined and linked for the program to compile and run successfully.
- The program requires the `<stdio.h>` header for the `printf` function to be available.

**Output Example**: The function prints its results directly to the standard output (the console). A typical run would display:
```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

## Example

The provided code is a complete, self-contained example of the `main` function's usage.

```c
#include <stdio.h>

// Assume findMax, stringLength, and isPrime are defined elsewhere
int findMax(int arr[], int size);
int stringLength(char str[]);
int isPrime(int n);

int main() {
    int nums[] = {5, 12, 3, 19, 7};
    int size = sizeof(nums) / sizeof(nums[0]);
    
    printf("Maximum number: %d\n", findMax(nums, size));
    
    char name[] = "Prateek";
    printf("Length of '%s': %d\n", name, stringLength(name));
    
    int number = 17;
    if (isPrime(number))
        printf("%d is a prime number.\n", number);
    else
        printf("%d is not a prime number.\n", number);

    return 0;
}
```

**Output:**

Assuming the helper functions are implemented correctly, the output will be:

```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

***
