## FunctionDef findMax(arr[], size)
# Function: findMax(int arr[], int size)

## Overview

The `findMax` function iterates through an array of integers to find and return the largest value.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | The input array of integers to be searched. |
| `size` | `int` | The total number of elements in the `arr`. |

## Description

This function provides a straightforward way to determine the maximum value within an integer array.

The logic begins by initializing a variable `max` with the value of the first element of the array, `arr[0]`. It then proceeds to loop through the remaining elements of the array, starting from the second element at index `1` up to the last element specified by `size`.

Inside the loop, each element `arr[i]` is compared to the current `max` value. If the current element `arr[i]` is greater than `max`, the `max` variable is updated with this new, larger value. This process ensures that after each comparison, `max` always holds the largest value found so far.

After the loop completes, the function returns the final `max` value.

```c
int findMax(int arr[], int size) {
    // Assume the first element is the largest
    int max = arr[0];
    
    // Iterate from the second element to the end of the array
    for (int i = 1; i < size; i++) {
        // If a larger element is found, update max
        if (arr[i] > max)
            max = arr[i];
    }
    
    // Return the largest value found
    return max;
}
```

## Usage Notes

Important points to consider when using this function:

- The `size` parameter must accurately reflect the number of elements in the `arr` to prevent out-of-bounds memory access or incorrect results.
- The function assumes the array is not empty. Passing an array with `size` as 0 will result in undefined behavior due to the initial access of `arr[0]`.
- The function works with both positive and negative integers.

**Output Example**: The function returns a single integer representing the maximum value in the array. For an input array `{10, 50, 20}`, the output would be `50`.

## Example

```c
#include <stdio.h>

// Declaration of the function
int findMax(int arr[], int size);

int main() {
    int numbers[] = {15, 98, 23, 4, 55, 76};
    int array_size = 6;
    
    // Call the function to find the maximum value
    int result = findMax(numbers, array_size);
    
    printf("The maximum value in the array is: %d\n", result);
    
    return 0;
}

// Definition of the function
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
The maximum value in the array is: 98
```

***
## FunctionDef findMin(arr[], size)
# Function: findMin(int arr[], int size)

## Overview

The `findMin` function iterates through an array of integers to find and return the smallest value.

## parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `arr` | `int[]` | The array of integers to be searched. |
| `size` | `int` | The number of elements in the `arr` array. |

## Description

The `findMin` function provides a straightforward way to determine the minimum value within an integer array.

The function begins by initializing a local integer variable `min` with the value of the first element of the array, `arr[0]`. This variable serves as the initial candidate for the minimum value.

It then enters a `for` loop that iterates through the array, starting from the second element (index `1`) up to, but not including, the `size` of the array. In each iteration, it compares the current element `arr[i]` with the value stored in `min`.

If the current element `arr[i]` is less than `min`, the value of `min` is updated to `arr[i]`. This process ensures that `min` always holds the smallest value encountered so far. After the loop has traversed all the elements, the function returns the final value of `min`.

## Usage Notes

- The function assumes the array is not empty. Passing an array with `size` as 0 or less will result in undefined behavior due to the initial access of `arr[0]`.
- The `size` parameter must accurately represent the number of elements in `arr`. An incorrect size can lead to either not all elements being checked or reading from memory outside the array's bounds.
- The function correctly handles arrays containing positive, negative, and zero values.

**Output Example**: The function returns a single integer representing the smallest value found in the array. For an input array `{10, -5, 100}`, the output would be `-5`.

## Example

```c
#include <stdio.h>

// Declaration of the function
int findMin(int arr[], int size);

int main() {
    int numbers[] = {42, 15, 7, 99, 23, 3, -10};
    int array_size = 7;
    
    // Call the findMin function
    int result = findMin(numbers, array_size);
    
    printf("The minimum value is: %d\n", result);
    
    return 0;
}

// Definition of the function
int findMin(int arr[], int size) {
    int min = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < min)
            min = arr[i];
    }
    return min;
}
```

**Output:**

```
The minimum value is: -10
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

This function provides a straightforward way to calculate the average of a list of integers. It operates by first initializing an integer variable `sum` to `0`.

It then enters a `for` loop that iterates from `i = 0` up to, but not including, the `size` of the array. In each iteration, the value of the current element `arr[i]` is added to the `sum`.

After the loop has processed all elements, the function calculates the final average. To ensure a precise floating-point result and avoid integer division truncation, the accumulated `sum` is explicitly cast to a `double` before being divided by the `size`. The resulting `double` value, representing the average, is then returned.

```c
// Inside the function
int sum = 0;
for (int i = 0; i < size; i++) {
    sum += arr[i];
}
// The sum is cast to a double for accurate division
return (double)sum / size;
```

## Usage Notes

- The `size` parameter must be greater than zero. Passing `size` as `0` will result in a division-by-zero error, leading to undefined behavior.
- The value of `size` should accurately represent the number of elements in the `arr` array to prevent incorrect calculations or memory access errors.
- The function returns a `double` to accurately represent averages that are not whole numbers.

**Output Example**: A floating-point number representing the calculated average.

## Example

```c
#include <stdio.h>

// Assuming the calculateAverage function is defined here or included
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
    int size = sizeof(numbers) / sizeof(numbers[0]);
    
    double avg = calculateAverage(numbers, size);
    
    printf("The average is: %f\n", avg);
    
    return 0;
}
```

**Output:**

```
The average is: 15.000000
```

***
## FunctionDef stringLength(str[])
# Function: stringLength(char str[])

## Overview

The `stringLength` function calculates the length of a null-terminated string by counting the number of characters before the null terminator.

## parameters

- `str`: A `char[]` array representing the null-terminated string whose length is to be determined.

## Description

This function provides a manual implementation for calculating the length of a C-style string. It operates based on the fundamental principle that strings in C are sequences of characters terminated by a special null character (`\0`).

The function initializes an integer counter, `length`, to `0`. It then enters a `while` loop that iterates through the input character array `str`. The loop's condition, `str[length] != '\0'`, checks if the character at the current index (`length`) is the null terminator.

For each character that is not the null terminator, the `length` counter is incremented. This process continues until the loop encounters the `\0` character, which signifies the end of the string. At this point, the loop terminates, and the function returns the final value of `length`. This value represents the total number of characters in the string, excluding the null terminator itself.

```c
// The core logic iterates until the null terminator is found.
int length = 0;
while (str[length] != '\0') {
    length++;
}
return length;
```

## Usage Notes

- The input array `str` **must** be a valid null-terminated string. If the null terminator `\0` is missing, the function will continue to read beyond the bounds of the array, leading to undefined behavior and potential program crashes.
- The length returned by the function does not include the null terminator `\0` in its count.
- The function does not modify the content of the input string `str`.

**Output Example**: For an input string `"Hello"`, which is stored in memory as `['H', 'e', 'l', 'l', 'o', '\0']`, the function will return `5`.

## Example

```c
#include <stdio.h>

// Definition of the stringLength function
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
    printf("The string is: \"%s\"\n", myString);
    printf("The length of the string is: %d\n", len);

    char emptyString[] = "";
    int emptyLen = stringLength(emptyString);
    printf("The length of an empty string is: %d\n", emptyLen);
    
    return 0;
}
```

**Output:**

```
The string is: "Hello, World!"
The length of the string is: 13
The length of an empty string is: 0
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

The function first ensures that the range boundaries are correctly ordered. It checks if `min` is greater than `max`. If this condition is true, it swaps the two values using a temporary variable `temp`. This makes the function robust, as it will work correctly even if the arguments are passed in the wrong order.

The core of the function is the expression `min + rand() % (max - min + 1)`. Let's break this down:
1.  `rand()`: This is a standard C library function that returns a pseudo-random integer between `0` and `RAND_MAX`.
2.  `(max - min + 1)`: This calculates the total number of possible integer values in the desired range. For example, for a range from 5 to 10, this would be `10 - 5 + 1 = 6`.
3.  `rand() % (max - min + 1)`: The modulo operator (`%`) scales the output of `rand()` to a number within the range of `0` to `max - min`.
4.  `min + ...`: This final addition shifts the generated number, which is in the range `[0, max - min]`, to the desired final range of `[min, max]`.

## Usage Notes

- This function depends on the standard C `rand()` function. For generating different sequences of random numbers across program executions, it is essential to seed the random number generator once at the start of your program using `srand()`. A common practice is to seed it with the current time: `srand(time(NULL));`.
- The range is inclusive, meaning the returned value can be equal to `min` or `max`.
- The function automatically handles cases where `min` is provided as a larger value than `max` by swapping them internally.

**Output Example**: A single integer value between `min` and `max`, inclusive.

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

    int lower_bound = 1;
    int upper_bound = 100;

    // Get a random number between 1 and 100
    int random_number = getRandom(lower_bound, upper_bound);

    printf("A random number between %d and %d is: %d\n", lower_bound, upper_bound, random_number);

    return 0;
}
```

**Output:**

```
A random number between 1 and 100 is: 42
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

The logic begins by handling the base cases. According to the definition of prime numbers, any integer less than or equal to 1 is not prime. The function reflects this by immediately returning `false` if `n <= 1`.

For numbers greater than 1, the function iterates from `i = 2` up to the square root of `n`. The condition `i * i <= n` is an optimization that avoids checking divisors beyond the square root of `n`, as any factor larger than the square root would have a corresponding factor smaller than it.

Inside the loop, it uses the modulo operator (`%`) to check if `n` is perfectly divisible by the current iterator `i`. If `n % i == 0` is true, it means a divisor has been found, proving that `n` is not a prime number. In this case, the function immediately returns `false`.

If the loop completes without finding any divisors, it confirms that `n` is only divisible by 1 and itself, thus it is a prime number, and the function returns `true`.

## Usage Notes

- The function correctly identifies that numbers less than or equal to 1 are not prime.
- The return type is `bool`. In C, this will evaluate to `true` (typically 1) or `false` (typically 0).
- This implementation is efficient for moderately sized integers.

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

int main() {
    int num1 = 29;
    int num2 = 10;

    // Example usage
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

The `main` function serves as the entry point for the program, demonstrating the usage of several utility functions: `findMax`, `stringLength`, and `isPrime`.

## parameters

This function does not accept any parameters upon execution.

## Description

The `main` function orchestrates a series of operations to showcase the functionality of other helper functions within the program.

1.  **Find Maximum in an Array**:
    - An integer array `nums` is initialized with the values `{5, 12, 3, 19, 7}`.
    - The `size` of the array is calculated by dividing the total memory occupied by the array (`sizeof(nums)`) by the memory size of a single element (`sizeof(nums[0])`).
    - The `findMax` function is called with the `nums` array and its `size`. The result, which is the largest number in the array, is then printed to the console.

2.  **Calculate String Length**:
    - A character array `name` is initialized with the string literal "Prateek".
    - The `stringLength` function is invoked with the `name` array. The function calculates the number of characters in the string (excluding the null terminator), and this length is printed.

3.  **Check for Prime Number**:
    - An integer variable `number` is declared and initialized with the value `17`.
    - The `isPrime` function is called with `number` as its argument.
    - An `if-else` statement evaluates the boolean result from `isPrime`. It prints a message indicating whether `number` is a prime number or not.

Finally, the function returns `0`, a standard convention indicating that the program terminated successfully.

## Usage Notes

- This function is the primary entry point for the C program and is automatically called when the program starts.
- It depends on three external functions: `findMax`, `stringLength`, and `isPrime`. These functions must be defined and linked for the program to compile and run correctly.
- The `printf` function is used for output, which requires including the standard I/O library header (`<stdio.h>`).

**Output Example**: The console output when the program is executed, assuming the helper functions are implemented correctly.

## Example

The `main` function is not called by other functions but is executed when the compiled program is run. The code below is the complete implementation for this entry point.

```c
#include <stdio.h>

// Assuming findMax, stringLength, and isPrime are defined elsewhere
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

```
Maximum number: 19
Length of 'Prateek': 7
17 is a prime number.
```

***
