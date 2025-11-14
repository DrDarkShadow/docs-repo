## FunctionDef findMax(arr[], size)
# Function: findMax(int arr[], int size)

## Overview

The `findMax` function iterates through an array of integers to find and return the largest value.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | The array of integers to be searched. |
| `size` | `int` | The total number of elements in the `arr`. |

## Description

This function provides a straightforward method for finding the maximum value within an integer array.

The logic begins by initializing a local variable `max` with the value of the first element in the array, `arr[0]`. This value serves as the initial candidate for the maximum.

Next, the function enters a `for` loop that iterates through the array, starting from the second element (index `1`) up to, but not including, the `size` of the array. In each iteration, it performs a comparison:

```c
if (arr[i] > max)
    max = arr[i];
```

If the current element `arr[i]` is greater than the current value stored in `max`, `max` is updated to this new, larger value. This process ensures that `max` always holds the largest value encountered so far in the traversal.

After the loop completes, having checked every element from the second to the last, the function returns the final value of `max`.

## Usage Notes

- The function assumes the array is not empty. Providing an array with a `size` of 0 or less will result in undefined behavior due to the initial access of `arr[0]`.
- The `size` parameter must accurately represent the number of elements in the `arr`. An incorrect `size` can lead to accessing memory outside the array's bounds, causing unpredictable results or program crashes.
- The function correctly handles arrays containing negative numbers, positive numbers, or a mix of both.

**Output Example**: The function returns a single integer representing the highest value found in the array.

## Example

```c
#include <stdio.h>

// Declaration of the findMax function
int findMax(int arr[], int size);

int main() {
    int numbers[] = {-10, 5, 42, -100, 17, 8, 99, 3};
    int array_size = sizeof(numbers) / sizeof(numbers[0]);
    
    // Call the function to find the maximum value
    int max_value = findMax(numbers, array_size);
    
    printf("The maximum value in the array is: %d\n", max_value);
    
    return 0;
}

// Definition of the findMax function
int findMax(int arr[], int size) {
    if (size <= 0) {
        // It's good practice to handle empty or invalid arrays
        return -1; // Or some other error indicator
    }
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
The maximum value in the array is: 99
```

***
## FunctionDef findMin(arr[], size)
# Function: findMin(int arr[], int size)

## Overview

The `findMin` function iterates through an array of integers to find and return the smallest value.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers from which the minimum value will be found. |
| `size` | `int` | The total number of elements in the `arr` array. |

## Description

This function provides a straightforward method for finding the minimum element in an integer array.

The logic begins by initializing a local variable `min` with the value of the first element of the array, `arr[0]`. This value serves as the initial candidate for the minimum.

Next, the function enters a `for` loop that starts from the second element of the array (index `1`) and continues until it has checked every element up to `size - 1`. Inside the loop, it compares the current element, `arr[i]`, with the value stored in `min`. If `arr[i]` is less than `min`, it means a new, smaller minimum has been found, and `min` is updated to this new value.

After the loop completes, the `min` variable holds the smallest value encountered in the array. The function concludes by returning this final `min` value.

```c
// The function assumes the first element is the minimum
int min = arr[0];

// It then loops from the second element to the end
for (int i = 1; i < size; i++) {
    // If a smaller element is found, it becomes the new minimum
    if (arr[i] < min)
        min = arr[i];
}
// The smallest value found is returned
return min;
```

## Usage Notes

- The function assumes the array is not empty. Calling this function with an empty array (i.e., `size` is 0) will result in undefined behavior due to an out-of-bounds memory access on `arr[0]`.
- The `size` parameter must accurately represent the number of elements in the `arr`. Providing a `size` larger than the actual array length will lead to reading from unallocated memory, causing unpredictable results or program crashes.
- This function is designed for arrays of integers and will work correctly with both positive and negative numbers.

**Output Example**: The function returns a single integer representing the minimum value in the array. For an input array `{10, -5, 20}`, the return value would be `-5`.

## Example

The following C code demonstrates how to use the `findMin` function.

```c
#include <stdio.h>

// Definition of the findMin function
int findMin(int arr[], int size) {
    if (size <= 0) {
        // It's good practice to handle the empty array case.
        // Here we'll return 0 or handle the error as appropriate.
        return 0; 
    }
    int min = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < min)
            min = arr[i];
    }
    return min;
}

int main() {
    int numbers[] = {45, 23, 89, 12, 5, 99, -4};
    int n = sizeof(numbers) / sizeof(numbers[0]);

    int minValue = findMin(numbers, n);

    printf("The array is: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\nThe minimum value is: %d\n", minValue);

    return 0;
}
```

**Output:**

```
The array is: 45 23 89 12 5 99 -4 
The minimum value is: -4
```

***
## FunctionDef calculateAverage(arr[], size)
# Function: calculateAverage(int arr[], int size)

## Overview

The `calculateAverage` function computes the arithmetic mean of the elements in an integer array.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | An array of integers whose average value is to be calculated. |
| `size` | `int` | The number of elements in the `arr` array. |

## Description

This function provides a straightforward way to calculate the average of a set of integers stored in an array.

The logic begins by initializing an integer variable, `sum`, to `0`. This variable serves as an accumulator for the total value of all elements in the array.

The function then iterates through the provided array `arr` using a `for` loop. The loop runs from the first element at index `0` up to the element at index `size - 1`. In each iteration, the value of the current element `arr[i]` is added to the `sum`.

After the loop has processed all elements, the function calculates the final average. To ensure an accurate floating-point result and prevent integer division (which would truncate any decimal part), the accumulated `sum` is explicitly cast to a `double` before being divided by `size`. The resulting `double` value, representing the average, is then returned.

## Usage Notes

- The `size` parameter must accurately reflect the number of elements in the `arr` array. An incorrect `size` can lead to an incomplete calculation or reading from memory outside the array's bounds, causing undefined behavior.
- If `size` is `0`, the function will attempt a division by zero. This is undefined behavior in C and will likely result in a program crash or a non-finite value (`inf` or `NaN`). The caller should ensure the array is not empty.
- For arrays containing very large numbers, the intermediate `sum` variable could potentially overflow the standard `int` type before the final division, leading to an incorrect result.

**Output Example**: The function returns a `double` representing the calculated average. For an input array `{1, 2, 3}`, the return value would be `2.0`.

## Example

```c
#include <stdio.h>

// Definition of the function
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
    int numbers[] = {10, 20, 30, 40, 55};
    int count = 5;
    double average = calculateAverage(numbers, count);
    
    printf("The average is: %f\n", average);
    
    return 0;
}
```

**Output:**

```
The average is: 31.000000
```

***
## FunctionDef stringLength(str[])
# Function: stringLength(char str[])

## Overview

The `stringLength` function calculates the number of characters in a C-style null-terminated string.

## parameters

*   `str`: A character array (`char[]`) that represents the string. This array must be null-terminated.

## Description

This function determines the length of a string by iterating through its characters until it encounters the null terminator (`\0`).

The function initializes an integer counter, `length`, to `0`. It then enters a `while` loop that continues as long as the character at the current index, `str[length]`, is not the null character `\0`. Inside the loop, the `length` variable is incremented for each character encountered. This variable serves as both the index for the array and the running count of characters.

When the loop terminates upon reaching the null character, the final value of `length` is equal to the number of characters in the string, excluding the null terminator itself. The function then returns this `length` value.

```c
// The loop continues until the null terminator is found.
while (str[length] != '\0') {
    // The counter is incremented for each character.
    length++;
}
```

## Usage Notes

- The input character array `str` **must** be properly null-terminated. Failure to provide a null-terminated string will cause the function to read beyond the bounds of the array, leading to undefined behavior and potential program crashes.
- The length returned by the function does not include the null terminator `\0`.
- The function does not modify the input string; it is a read-only operation.

**Output Example**: The function returns an integer. For the input string `"example"`, the return value would be `7`.

## Example

```c
#include <stdio.h>

// The function to be documented
int stringLength(char str[]) {
    int length = 0;
    while (str[length] != '\0') {
        length++;
    }
    return length;
}

// Example usage in a main function
int main() {
    char myString[] = "Hello, World!";
    int len = stringLength(myString);
    printf("The length of \"%s\" is: %d\n", myString, len);

    char emptyString[] = "";
    int emptyLen = stringLength(emptyString);
    printf("The length of an empty string is: %d\n", emptyLen);
    
    return 0;
}
```

**Output:**

```
The length of "Hello, World!" is: 13
The length of an empty string is: 0
```

***
## FunctionDef getRandom(min, max)
# Function: getRandom

## Overview

The `getRandom` function generates a pseudo-random integer within a specified inclusive range.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `min` | `int` | The lower bound of the random number range (inclusive). |
| `max` | `int` | The upper bound of the random number range (inclusive). |

## Description

This function provides a reliable way to obtain a random integer between two boundary values, `min` and `max`.

Initially, the function checks if `min` is greater than `max`. If this condition is true, it means the parameters were passed in the wrong order. The function gracefully handles this by swapping the values of `min` and `max`, ensuring that `min` is always the lower bound and `max` is the upper bound.

The core logic for generating the random number is in the return statement: `return min + rand() % (max - min + 1);`. This expression works as follows:
1.  `rand()`: This standard C library function is called to produce a pseudo-random integer between `0` and `RAND_MAX`.
2.  `(max - min + 1)`: This calculates the size of the desired range. For example, for a range from 5 to 10, the size is `10 - 5 + 1 = 6`.
3.  `rand() % (max - min + 1)`: The modulo operator (`%`) scales the number from `rand()` to a value within the range of `0` to `(max - min)`.
4.  `min + ...`: The result is then shifted by adding `min`, which adjusts the range to be from `min` to `max`, inclusive.

## Usage Notes

- This function relies on the C standard library's `rand()` function. For `rand()` to produce different sequences of numbers each time the program is run, the random number generator must be seeded. It is best practice to seed it once at the beginning of the program using `srand(time(NULL))`. This requires including the `<time.h>` header.
- The function is inclusive, meaning the returned value can be equal to `min` or `max`.
- The function automatically corrects for cases where the `min` parameter is larger than the `max` parameter by swapping them internally.

**Output Example**: A single random integer within the specified range. For `getRandom(1, 100)`, a possible output is:
```
42
```

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

    int min_val = 1;
    int max_val = 10;

    // Generate and print a random number between 1 and 10
    int random_number = getRandom(min_val, max_val);
    printf("A random number between %d and %d is: %d\n", min_val, max_val, random_number);

    return 0;
}
```

**Output:**

```
A random number between 1 and 10 is: 7
```
(Note: The actual output will vary with each execution.)

***
## FunctionDef isPrime(n)
# Function: isPrime(int n)

## Overview

The `isPrime` function determines whether a given integer is a prime number.

## Parameters

- `n`: The integer to be checked for primality.

## Description

This function provides an efficient method to check if an integer `n` is a prime number.

The logic begins by handling the base cases. According to the definition of prime numbers, any integer less than or equal to 1 is not prime. The function first checks if `n <= 1` and returns `false` if this condition is met.

If `n` is greater than 1, the function proceeds to check for divisors. It iterates through integers starting from `i = 2` up to the square root of `n`. The loop condition `i * i <= n` is an optimization that significantly improves performance, as any factor of `n` larger than its square root would have a corresponding factor smaller than the square root.

Inside the loop, it uses the modulo operator (`%`) to check if `n` is evenly divisible by the current integer `i`. If `n % i == 0` is true at any point, it means a factor has been found, and `n` is not a prime number. In this case, the function immediately returns `false`.

If the loop completes without finding any factors, it confirms that `n` has no divisors other than 1 and itself, meaning it is a prime number. The function then returns `true`.

```c
// Example of the core logic
if (n <= 1)
    return false; // 1 and non-positive numbers are not prime
for (int i = 2; i * i <= n; i++) {
    if (n % i == 0)
        return false; // Found a divisor, not prime
}
return true; // No divisors found, it is prime
```

## Usage Notes

- The function correctly handles edge cases, returning `false` for all integers less than or equal to 1.
- The implementation is optimized for performance by only checking for divisors up to the square root of the input number `n`.
- The return type is `bool`, which will be `true` if the number is prime and `false` otherwise.

**Output Example**: The function returns a boolean value. For a prime number like 7, the output is `true`. For a non-prime number like 8, the output is `false`.

## Example

```c
#include <stdio.h>
#include <stdbool.h>

// Definition of the isPrime function
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
    int num2 = 15;

    // Using a ternary operator to print the result as a string
    printf("Is %d a prime number? %s\n", num1, isPrime(num1) ? "true" : "false");
    printf("Is %d a prime number? %s\n", num2, isPrime(num2) ? "true" : "false");

    return 0;
}
```

**Output:**

```
Is 29 a prime number? true
Is 15 a prime number? false
```

***
## FunctionDef main
# Function: main

## Overview

The `main` function serves as the entry point of the program, demonstrating the usage of three utility functions: `findMax`, `stringLength`, and `isPrime`.

## parameters

This function does not accept any parameters.

## Description

The `main` function executes a sequence of operations to showcase the functionality of other helper functions within the program.

1.  **Find Maximum in an Array**:
    *   An integer array `nums` is initialized with the values `{5, 12, 3, 19, 7}`.
    *   The variable `size` is calculated by dividing the total size of the `nums` array by the size of a single element, effectively determining the number of elements in the array.
    *   It then calls the `findMax` function, passing `nums` and `size` as arguments.
    *   The result, which is the largest number in the array, is printed to the console.

    ```c
    int nums[] = {5, 12, 3, 19, 7};
    int size = sizeof(nums) / sizeof(nums[0]);
    printf("Maximum number: %d\n", findMax(nums, size));
    ```

2.  **Calculate String Length**:
    *   A character array `name` is initialized with the string literal "Prateek".
    *   It calls the `stringLength` function with `name` as the argument.
    *   The returned length of the string is printed to the console.

    ```c
    char name[] = "Prateek";
    printf("Length of '%s': %d\n", name, stringLength(name));
    ```

3.  **Check for Prime Number**:
    *   An integer variable `number` is initialized to `17`.
    *   The `isPrime` function is called with `number` as the argument.
    *   An `if-else` statement checks the boolean result from `isPrime`. It prints a message to the console indicating whether `17` is a prime number or not.

    ```c
    int number = 17;
    if (isPrime(number))
        printf("%d is a prime number.\n", number);
    else
        printf("%d is not a prime number.\n", number);
    ```

Finally, the function returns `0`, signaling that the program has executed successfully.

## Usage Notes

- This function is the primary entry point for the C program.
- It relies on the external functions `findMax`, `stringLength`, and `isPrime`. These functions must be defined and linked for the program to compile and run correctly.
- All results are printed to the standard output (the console).

**Output Example**: The function will print the following lines to the console.

```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

## Example

The `main` function is not called by user code; it is the starting point of the program's execution. To run this code, you would compile the source file (e.g., `program.c`) and then execute the resulting binary.

**Compilation and Execution (using GCC):**

```bash
# Compile the C source file
gcc program.c -o program

# Run the compiled executable
./program
```

**Output:**

```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

***
