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

The logic begins by initializing a local integer variable `max` with the value of the first element of the array, `arr[0]`. This variable serves as a temporary placeholder for the largest value found so far.

The function then enters a `for` loop that iterates through the array, starting from the second element (index `1`) up to the element at index `size - 1`. In each iteration, it performs a comparison:

```c
if (arr[i] > max)
    max = arr[i];
```

If the current element `arr[i]` is greater than the current value stored in `max`, `max` is updated to the value of `arr[i]`. This ensures that `max` always holds the largest value encountered in the portion of the array that has been scanned.

After the loop has finished iterating through all the elements, the function returns the final value of `max`.

## Usage Notes

- The input array `arr` must not be empty (i.e., `size` must be at least 1). The function directly accesses `arr[0]` without any bounds checking, which will lead to undefined behavior for an empty array.
- The `size` parameter must accurately reflect the number of elements in `arr`. An incorrect `size` can lead to either missing elements or reading out of the array's bounds.
- The function correctly handles arrays containing negative numbers, positive numbers, or a mix of both.

**Output Example**: The function returns a single integer value.
`100`

## Example

```c
#include <stdio.h>

// Assuming the findMax function is defined here or included
int findMax(int arr[], int size) {
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max)
            max = arr[i];
    }
    return max;
}

int main() {
    int numbers[] = {10, 5, 42, 8, 99, 12};
    int count = sizeof(numbers) / sizeof(numbers[0]);
    
    int maxValue = findMax(numbers, count);
    
    printf("The maximum value in the array is: %d\n", maxValue);
    
    return 0;
}
```

**Output:**

```
The maximum value in the array is: 99
```

***
## FunctionDef findMin(arr[], size)
# Function: findMin(int arr[], int size)

## Overview

The `findMin` function finds and returns the minimum value in an array of integers.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers to be searched. |
| `size` | `int` | The number of elements in the array `arr`. |

## Description

This function provides a straightforward way to find the smallest integer within an array. The logic begins by assuming the first element of the array, `arr[0]`, is the minimum value and storing it in a local variable named `min`.

It then iterates through the rest of the array elements, starting from the second element at index `1` up to the last element specified by the `size` parameter. In each iteration, it compares the current element `arr[i]` with the value stored in `min`. If the current element `arr[i]` is less than `min`, the function updates `min` to the value of `arr[i]`.

After the loop has traversed all the elements, the `min` variable will hold the absolute smallest value found in the entire array. This final value is then returned by the function.

## Usage Notes

- The array `arr` should not be empty. The function accesses `arr[0]` without checking if the `size` is greater than zero, which could lead to undefined behavior for an empty array.
- The `size` parameter must accurately represent the number of elements in the array. An incorrect `size` can cause the function to miss elements or read beyond the array's bounds.
- The function returns a single integer, which is the smallest value found in the array.

**Output Example**: A single integer representing the minimum value.

## Example

```c
int numbers[] = {25, 10, 5, 88, 12};
int array_size = 5;
int result = findMin(numbers, array_size);
// result now holds the value 5
```

**Output:**

```
5
```

***
## FunctionDef calculateAverage(arr[], size)
# Function: calculateAverage(int arr[], int size)

## Overview

The `calculateAverage` function computes the arithmetic mean of the elements in an integer array.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers for which the average will be calculated. |
| `size` | `int` | The number of elements in the `arr` array. |

## Description

This function provides a straightforward way to calculate the average of a list of integers. It operates by first initializing an integer variable `sum` to `0`.

It then enters a `for` loop that iterates from `i = 0` up to, but not including, the `size` of the array. In each iteration, the value of the current element `arr[i]` is added to the `sum`.

After the loop has processed all elements, the function calculates the final average. To ensure a precise floating-point result and avoid integer division, the accumulated `sum` is explicitly cast to a `double` before being divided by the `size`. The resulting `double` value is then returned.

```c
// The core calculation logic
return (double)sum / size;
```

## Usage Notes

- The `size` parameter must accurately represent the number of elements in the `arr`. Providing a `size` larger than the array's actual capacity will lead to reading from unallocated memory, resulting in undefined behavior.
- If `size` is `0`, the function will attempt to divide by zero. This is undefined behavior in C and can lead to a program crash or non-sensical return values like `inf` or `nan`. It is the caller's responsibility to handle empty arrays.
- The function returns a `double` to accurately represent averages that are not whole numbers (e.g., the average of `[1, 2]` is `1.5`).

**Output Example**: The function returns a single floating-point number. For an input array `{10, 20, 30}`, the return value would be `20.000000`.

## Example

```c
#include <stdio.h>

// Definition of the function
double calculateAverage(int arr[], int size) {
    if (size == 0) {
        return 0.0; // Handle division by zero
    }
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return (double)sum / size;
}

int main() {
    int numbers[] = {5, 10, 15, 20, 25};
    int count = sizeof(numbers) / sizeof(numbers[0]);
    
    double average = calculateAverage(numbers, count);
    
    printf("The array is: [5, 10, 15, 20, 25]\n");
    printf("The average is: %f\n", average);
    
    return 0;
}
```

**Output:**

```
The array is: [5, 10, 15, 20, 25]
The average is: 15.000000
```

***
## FunctionDef stringLength(str[])
# Function: stringLength(char str[])

## Overview

The `stringLength` function calculates the length of a C-style null-terminated string.

## parameters

- `str` (`char[]`): The input character array (string). This string must be terminated by a null character (`\0`).

## Description

This function provides a manual implementation for determining the length of a string in C. It operates by iterating through the characters of the input array `str` until it encounters the null terminator character (`\0`), which signifies the end of a C-string.

The function initializes an integer counter, `length`, to `0`. It then enters a `while` loop that checks the character at the current index, `str[length]`. The loop continues as long as the character is not the null terminator. Inside the loop, the `length` counter is incremented for each character.

When the loop terminates (upon finding `\0`), the final value of `length` represents the total number of characters in the string, excluding the null terminator itself. This value is then returned.

```c
// The loop continues until the null terminator is found.
while (str[length] != '\0') {
    // The counter is incremented for each character.
    length++;
}
// The final count is returned.
return length;
```

## Usage Notes

- The input character array `str` **must** be null-terminated. Failure to provide a null-terminated string will cause the function to read beyond the buffer's boundary, leading to undefined behavior.
- The returned length does not include the null terminator character `\0`. For example, the string `"cat"` has a length of 3, but it occupies 4 bytes of memory (`'c'`, `'a'`, `'t'`, `'\0'`).
- This function does not modify the input string.

**Output Example**: The function returns an integer representing the number of characters. For the input `"Hello"`, the return value would be `5`.

## Example

```c
#include <stdio.h>

/*
  The stringLength function calculates the length of a null-terminated string.
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
    printf("The length of the string is: %d\n", len);
    return 0;
}
```

**Output:**

```
The length of the string is: 13
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

This function provides a reliable way to obtain a random integer between two boundary values, `min` and `max`, inclusive.

The function first checks if the `min` value is greater than the `max` value. If this condition is true, it means the parameters were likely passed in the wrong order. The function handles this gracefully by swapping the values of `min` and `max` using a temporary variable. This ensures the logic for generating the random number works correctly regardless of the parameter order.

The core of the function is the return statement: `return min + rand() % (max - min + 1);`. This expression works as follows:
1.  `rand()`: This is a standard C library function that returns a pseudo-random integer between `0` and `RAND_MAX`.
2.  `(max - min + 1)`: This calculates the total number of possible integer values in the desired range. For example, if `min` is 5 and `max` is 10, the range size is `10 - 5 + 1 = 6` (for the numbers 5, 6, 7, 8, 9, 10).
3.  `rand() % (max - min + 1)`: The modulo operator (`%`) scales the large random number from `rand()` down to a value between `0` and `(max - min)`.
4.  `min + ...`: This result is then added to `min`, effectively shifting the random number range from `[0, max - min]` to `[min, max]`.

## Usage Notes

- This function relies on the C standard library function `rand()`. For `rand()` to produce different sequences of numbers each time the program is run, it must be seeded. It is common practice to seed the random number generator once at the beginning of the program using `srand(time(NULL))`. This requires including the `<time.h>` header.
- The range is inclusive, meaning both the `min` and `max` values are possible results.
- The function automatically corrects for cases where `min` is greater than `max` by swapping them internally.

**Output Example**: A single integer value between `min` and `max` (inclusive).

## Example

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
    // Seed the random number generator once
    srand(time(NULL));

    // Generate a random number between 1 and 100
    int randomNumber = getRandom(1, 100);

    printf("The random number is: %d\n", randomNumber);

    // Example with swapped parameters, which the function handles
    int anotherRandomNumber = getRandom(50, 20);
    printf("Another random number (from swapped 50, 20) is: %d\n", anotherRandomNumber);

    return 0;
}
```

**Output:**

```
The random number is: 73
Another random number (from swapped 50, 20) is: 35
```

***
## FunctionDef isPrime(n)
# Function: isPrime

## Overview

The `isPrime` function checks if a given integer is a prime number.

## parameters

- `n`: `int` - The integer to be checked for primality.

## Description

This function provides an efficient method to determine if an integer `n` is a prime number.

The logic begins by handling the base cases. By definition, a prime number must be greater than 1. The initial check `if (n <= 1)` correctly identifies that any number less than or equal to 1 is not prime, and the function returns `false`.

For numbers greater than 1, the function employs a `for` loop to search for divisors. The loop starts from `i = 2`, as 1 is a divisor for all integers. The loop's continuation condition, `i * i <= n`, is a crucial optimization. It leverages the mathematical property that if a number `n` has a divisor larger than its square root, it must also have a corresponding divisor smaller than its square root. Therefore, checking for divisors only up to the square root of `n` is sufficient. Using `i * i <= n` is computationally more efficient than calculating `i <= sqrt(n)`.

Inside the loop, the modulo operator (`%`) is used in the condition `if (n % i == 0)`. If `n` is perfectly divisible by `i`, it means `n` has a factor other than 1 and itself, so it cannot be a prime number. In this case, the function immediately returns `false`.

If the loop completes without finding any divisors, it confirms that `n` is only divisible by 1 and itself. The function then returns `true`, indicating that `n` is a prime number.

## Usage Notes

- The function returns a `bool` value: `true` if the number is prime, and `false` otherwise. In C, this corresponds to `1` and `0` respectively.
- The algorithm is optimized for performance by only checking divisors up to the square root of the input number.
- The function correctly handles edge cases such as `0`, `1`, and negative numbers, all of which are not prime.

**Output Example**: The function returns a boolean value.
```c
// For a prime number like 7
true 

// For a non-prime number like 8
false
```

## Example

```c
#include <stdio.h>
#include <stdbool.h>

// The isPrime function definition
bool isPrime(int n) {
    if (n <= 1)
        return false;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0)
            return false;
    }
    return true;
}

// Example usage in a main function
int main() {
    int number1 = 29;
    bool result1 = isPrime(number1);
    printf("Is %d a prime number? %s\n", number1, result1 ? "true" : "false");

    int number2 = 10;
    bool result2 = isPrime(number2);
    printf("Is %d a prime number? %s\n", number2, result2 ? "true" : "false");

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

The `main` function serves as the entry point for the C program, demonstrating the usage of several utility functions: `findMax`, `stringLength`, and `isPrime`.

## parameters

This function does not accept any parameters. It is the standard entry point for a C program without command-line arguments.

## Description

The `main` function orchestrates a series of operations to showcase different functionalities.

1.  **Find Maximum in an Array**:
    - An integer array `nums` is initialized with the values `{5, 12, 3, 19, 7}`.
    - The size of the array is calculated by dividing the total size of the array in bytes (`sizeof(nums)`) by the size of a single integer element (`sizeof(nums[0])`).
    - It then calls the `findMax` function, passing the `nums` array and its `size`. The returned maximum value is printed to the console.

2.  **Calculate String Length**:
    - A character array `name` is initialized with the string literal "Prateek".
    - The `stringLength` function is called with `name` as its argument. The function's return value, which is the length of the string, is then printed.

3.  **Check for Prime Number**:
    - An integer variable `number` is declared and initialized to `17`.
    - The `isPrime` function is called with `number`. An `if-else` block checks the boolean result to determine if the number is prime and prints the appropriate message to the console.

Finally, the function returns `0`, which is a standard convention to indicate that the program has executed successfully without errors.

## Usage Notes

- This function is the designated start of execution for the program.
- It depends on three external functions: `findMax`, `stringLength`, and `isPrime`. These functions must be defined and linked for the program to compile and run correctly.
- All output is directed to the standard output (the console).

**Output Example**: The console output generated by running this function will look like this:
```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

## Example

The `main` function is the program's entry point and is not called by user code. To run it, you compile the source file and execute the resulting program.

Assuming the code is in a file named `program.c` and all dependent functions are included:

```c
// 1. Compile the code using a C compiler like GCC
gcc program.c -o executable_name

// 2. Run the compiled executable from the terminal
./executable_name
```

**Output:**

```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

***
