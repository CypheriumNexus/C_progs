# Average an Array – C Programming Project Documentation

**Programmer:** Brian Lorick  
**Program Name:** Average an Array  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio 2019  
**Course Topic:** Chapter 6 – Functions  
**Source File:** `Average an Array.c`

---

## 1. Program Overview

The **Average an Array** program is a C application that accepts ten numerical values from the user, stores them in an array, calculates their arithmetic average, and displays the result.

The program demonstrates the use of arrays, user-defined functions, function prototypes, loops, arithmetic operations, and parameter passing.

The program separates its operations into three functions:

1. `inputValues()` – Collects and stores the user's input.
2. `calculateAverage()` – Adds the array elements and calculates their average.
3. `displayAverage()` – Displays the calculated average.

This structure demonstrates modular programming by separating input, processing, and output into individual functions.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive | Purpose |
|---|---|
| `#define _CRT_SECURE_NO_WARNINGS` | Disables Microsoft Visual Studio warnings associated with certain standard C functions, including `scanf()`. |
| `#include <stdio.h>` | Includes the Standard Input/Output library, which provides `printf()` and `scanf()`. |

### 2.2 Standard Library Functions

| Function | Purpose |
|---|---|
| `printf()` | Displays prompts and program output in the console. |
| `scanf()` | Accepts numerical input from the user and stores it in the array. |

The program uses `<stdio.h>` for console input and output. No additional libraries are required.

## 3. Variables and Data Structures

### 3.1 Variables

| Variable | Data Type | Purpose |
|---|---|---|
| `values` | `double[10]` | Stores the ten numerical values entered by the user. |
| `average` | `double` | Stores the calculated average returned by `calculateAverage()`. |
| `sum` | `double` | Accumulates the total of all array elements. |
| `i` | `int` | Loop counter used to access individual array elements. |
| `size` | `int` | Represents the number of elements to process in the array. |
| `array[]` | `double[]` | Function parameter that provides access to the array elements. |

### 3.2 Array Structure

The program declares a fixed-size array:

```c
double values[10];
```

This creates an array capable of storing ten values using the `double` data type.

Each element is accessed through an index beginning at `0` and ending at `9`.

| Array Index | Element |
|---:|---|
| 0 | First value |
| 1 | Second value |
| 2 | Third value |
| 3 | Fourth value |
| 4 | Fifth value |
| 5 | Sixth value |
| 6 | Seventh value |
| 7 | Eighth value |
| 8 | Ninth value |
| 9 | Tenth value |

The program passes the array and its size to the functions responsible for input and processing.

## 4. Processing Logic and Statements

### 4.1 Function Prototypes

The program declares three function prototypes before `main()`:

```c
void inputValues(double array[], int size);
double calculateAverage(double array[], int size);
void displayAverage(double average);
```

Function prototypes inform the compiler about each function's name, return type, and parameters before the functions are called.

| Function | Return Type | Parameters | Responsibility |
|---|---|---|---|
| `inputValues()` | `void` | Array and size | Collects user input. |
| `calculateAverage()` | `double` | Array and size | Calculates and returns the average. |
| `displayAverage()` | `void` | Average | Displays the result. |

The `void` return type indicates that a function does not return a value.

### 4.2 Main Function

The `main()` function controls the overall execution of the program.

```c
int main()
{
    double values[10];

    inputValues(values, 10);

    double average = calculateAverage(values, 10);

    displayAverage(average);

    return 0;
}
```

Execution begins by declaring the array. The program then calls each function in sequence:

1. Declares an array containing ten elements.
2. Calls `inputValues()` to populate the array.
3. Calls `calculateAverage()` to process the stored values.
4. Stores the returned result in `average`.
5. Calls `displayAverage()` to display the result.
6. Returns `0` to indicate successful program termination.

### 4.3 Input Function – `inputValues()`

```c
void inputValues(double array[], int size)
{
    for (int i = 0; i < size; i++)
    {
        printf("Enter a value for #%d: ", i + 1);
        scanf("%lf", &array[i]);
    }
}
```

This function collects ten numerical values from the user.

The `for` loop iterates through the array using the loop counter `i`.

The loop condition:

```c
i < size
```

Ensures that the loop continues while the index is less than the array size.

The `printf()` statement displays the input prompt. The expression `i + 1` displays the position as a number from 1 through 10, even though array indexing begins at 0.

The `scanf()` statement:

```c
scanf("%lf", &array[i]);
```

Uses the `%lf` format specifier to read a `double` value. The address-of operator (`&`) provides the memory address where the entered value should be stored.

### 4.4 Processing Function – `calculateAverage()`

```c
double calculateAverage(double array[], int size)
{
    double sum = 0.0;

    for (int i = 0; i < size; i++)
    {
        sum += array[i];
    }

    return sum / size;
}
```

This function calculates the arithmetic average of the values stored in the array.

The variable `sum` is initialized to `0.0` before processing begins.

A `for` loop iterates through each array element. During each iteration, the current element is added to the running total:

```c
sum += array[i];
```

After the loop finishes, the function divides the accumulated sum by the number of elements:

```c
return sum / size;
```

The calculated average is returned to `main()` as a `double` value.

**Mathematical operation:**

\[
\text{Average} = \frac{\text{Sum of all values}}{\text{Number of values}}
\]

For this program:

\[
\text{Average} = \frac{x_1+x_2+\cdots+x_{10}}{10}
\]

### 4.5 Output Function – `displayAverage()`

```c
void displayAverage(double average)
{
    printf("\nThe average of the values is %.2lf.\n", average);
    printf("\n");
}
```

This function receives the calculated average as a parameter and displays it in the console.

The format specifier `%.2lf` displays the numerical result with two digits after the decimal point.

The function uses `void` because it performs an output operation without returning a value.

## 5. Operators Used

| Operator | Name | Purpose in Program |
|---|---|---|
| `=` | Assignment | Assigns values to variables, such as initializing `sum`. |
| `<` | Less than | Controls the continuation of the `for` loops. |
| `++` | Increment | Increases the loop counter by one. |
| `+=` | Addition assignment | Adds each array element to the running total. |
| `/` | Division | Divides the sum by the number of elements. |
| `&` | Address-of | Supplies the memory address of an array element to `scanf()`. |

### Additional Expressions

| Expression | Explanation |
|---|---|
| `i < size` | Checks whether the loop counter is within the array's valid range. |
| `i + 1` | Displays the user's input position starting at 1. |
| `sum += array[i]` | Adds the current array element to the accumulated sum. |
| `sum / size` | Calculates the arithmetic average. |

## 6. Program Execution Sequence

The program follows a sequential input-processing-output structure.

| Step | Operation | Description |
|---:|---|---|
| 1 | Program Start | Execution begins in `main()`. |
| 2 | Array Declaration | Creates an array capable of storing ten `double` values. |
| 3 | Input Function Call | Calls `inputValues()` and passes the array and its size. |
| 4 | Input Loop | Prompts the user to enter ten numerical values. |
| 5 | Array Population | Stores each entered value in its corresponding array element. |
| 6 | Processing Function Call | Calls `calculateAverage()` with the populated array. |
| 7 | Summation Loop | Adds all ten array elements together. |
| 8 | Average Calculation | Divides the accumulated sum by the array size. |
| 9 | Return Result | Returns the calculated average to `main()`. |
| 10 | Output Function Call | Calls `displayAverage()` and passes the calculated average. |
| 11 | Display Result | Prints the average with two decimal places. |
| 12 | Program Termination | Returns `0` and ends execution. |

## 7. Text-Based Program Flowchart

```text
             +----------------------+
             |      PROGRAM START   |
             +----------------------+
                        |
                        v
             +----------------------+
             |       main()         |
             | Declare values[10]   |
             +----------------------+
                        |
                        v
             +----------------------+
             | Call inputValues()   |
             +----------------------+
                        |
                        v
             +----------------------+
             | Initialize i = 0     |
             +----------------------+
                        |
                        v
                +---------------+
                |   i < size?   |
                +---------------+
                  |           |
                YES           NO
                  |           |
                  v           |
        +------------------+  |
        | Prompt for value |  |
        +------------------+  |
                  |           |
                  v           |
        +------------------+  |
        | Read input using |  |
        | scanf("%lf", ...)|
        +------------------+  |
                  |           |
                  v           |
        +------------------+  |
        | Store value in   |  |
        | array[i]         |  |
        +------------------+  |
                  |           |
                  v           |
        +------------------+  |
        | Increment i      |--+
        +------------------+
                              |
                              v
                  +----------------------+
                  | Call calculateAverage|
                  +----------------------+
                              |
                              v
                  +----------------------+
                  | Initialize sum = 0.0 |
                  | Initialize i = 0     |
                  +----------------------+
                              |
                              v
                       +-------------+
                       | i < size?   |
                       +-------------+
                         |         |
                       YES         NO
                         |         |
                         v         |
               +----------------+  |
               | sum += array[i]|  |
               +----------------+  |
                         |         |
                         v         |
               +----------------+  |
               | Increment i    |--+
               +----------------+
                                   |
                                   v
                       +----------------------+
                       | Calculate average:    |
                       | sum / size            |
                       +----------------------+
                                   |
                                   v
                       +----------------------+
                       | Return average to     |
                       | main()                |
                       +----------------------+
                                   |
                                   v
                       +----------------------+
                       | Call displayAverage()|
                       +----------------------+
                                   |
                                   v
                       +----------------------+
                       | Display average      |
                       | with two decimals    |
                       +----------------------+
                                   |
                                   v
                       +----------------------+
                       | return 0;             |
                       +----------------------+
                                   |
                                   v
                       +----------------------+
                       |     PROGRAM END      |
                       +----------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Arrays

The program uses a fixed-size array to store multiple numerical values under one variable name. Individual elements are accessed through their numerical indexes.

### 8.2 User-Defined Functions

The program separates input, processing, and output into three independently defined functions. This improves organization, readability, and maintainability.

### 8.3 Function Parameters and Arguments

The program passes the array and its size to `inputValues()` and `calculateAverage()`. The calculated average is passed to `displayAverage()`.

This demonstrates how functions receive information from the calling function.

### 8.4 Function Return Values

The `calculateAverage()` function returns a `double` value to `main()`. The returned value is assigned to the `average` variable.

### 8.5 Iteration

The program uses `for` loops to repeat operations across the array. One loop collects the values, while another processes them.

### 8.6 Accumulator Variable

The `sum` variable functions as an accumulator. It maintains a running total as each array element is processed.

### 8.7 Data Types

The `double` data type is used to support numerical values containing decimal portions. The `int` data type is used for the loop counter and array size.

### 8.8 Modular Programming

By dividing the program into separate functions, each operation has a defined responsibility. This makes the program easier to understand, test, troubleshoot, and modify.

## 9. Program Characteristics and Limitations

| Characteristic | Description |
|---|---|
| Input Method | Console input using `scanf()`. |
| Input Quantity | Accepts exactly ten values. |
| Data Structure | Fixed-size array of type `double`. |
| Processing Method | Iterative summation using a `for` loop. |
| Calculation | Arithmetic mean of the ten values. |
| Output Method | Console output using `printf()`. |
| Output Precision | Displays two decimal places. |
| Function Structure | Three user-defined functions. |
| Termination | Returns `0` from `main()`. |

### 9.1 Input Validation

The current implementation assumes that the user enters valid numerical values.

It does not check the return value of `scanf()`. Consequently, nonnumeric input is not handled, and the program does not provide an error-recovery mechanism.

### 9.2 Fixed Array Size

The array is defined with ten elements, and the functions are called with a size argument of `10`.

The program does not dynamically resize the array or ask the user how many values they want to enter.

### 9.3 Division by Zero

The current program passes a size of `10` to `calculateAverage()`, so division by zero does not occur during normal execution.

However, the function itself does not validate that its `size` parameter is greater than zero. A more general implementation would include a size check before performing the division.

### 9.4 Numerical Precision

The program stores and calculates values using the `double` data type. Although the calculation retains floating-point precision internally, the output is formatted to display only two decimal places.

## 10. Overall Summary

The **Average an Array** program demonstrates how arrays and user-defined functions can work together to collect, process, and display numerical data in C.

The program begins by declaring an array capable of storing ten `double` values. It then calls `inputValues()` to collect the values from the user. Once the array has been populated, `calculateAverage()` uses a `for` loop and an accumulator variable to calculate the total and determine the arithmetic average. Finally, `displayAverage()` receives the returned result and prints it to the console with two decimal places.

The primary programming concepts demonstrated include array declaration and indexing, function prototypes, function calls, parameter passing, return values, iteration, arithmetic operations, and modular program design.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, including arrays, functions, loops, data types, and arithmetic calculations.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.