# Reverse and Average – C Program Documentation

| **Program Information** | **Details** |
|---|---|
| Program Name | Reverse and Average |
| Programmer | Brian Lorick |
| Programming Language | C |
| Development Environment | Microsoft Visual Studio 2019 |
| Course Topic | Chapter 5 – Arrays |
| Original Date | March 8, 2024 |
| Source File | `Reverse and Average.c` |

---

## 1. Program Overview

**Reverse and Average** is a C program that demonstrates array manipulation, indexed data processing, iteration, arithmetic operations, and formatted output.

The program prompts the user to enter ten integer values and stores them in an array named `originalArray`.

After collecting the input, the program performs two processing operations:

1. Reverses the order of the original array by copying its elements into a second array in reverse index order.
2. Calculates the average of each pair of corresponding elements from the original and reversed arrays.

The program stores the resulting values in a third array named `averageArray`.

Finally, it displays all three arrays:

- Original array – The ten values entered by the user.
- Reverse array – The original values arranged in reverse order.
- Average array – The calculated averages of corresponding elements.

The program demonstrates how multiple arrays can work together to store, manipulate, and process related data.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directive

```c
#define _CRT_SECURE_NO_WARNINGS
```

This Microsoft Visual C-specific preprocessor directive suppresses warnings associated with certain standard C library functions, including `scanf()`.

It allows the program to use standard input functions without Microsoft's secure-function warning messages.

### 2.2 Standard Input/Output Library

```c
#include <stdio.h>
```

The `stdio.h` header file provides the standard input/output functions used throughout the program.

| Function | Purpose |
|---|---|
| `printf()` | Displays prompts, headings, and array values. |
| `scanf()` | Accepts integer values entered by the user. |

## 3. Variables and Data Structures

The program uses three integer arrays and one integer loop-control variable.

### 3.1 Array Declarations

```c
int originalArray[10];
int reverseArray[10];
int averageArray[10];
```

Each array contains ten integer elements.

| Array | Data Type | Size | Purpose |
|---|---|---:|---|
| `originalArray` | `int` | 10 | Stores the ten values entered by the user. |
| `reverseArray` | `int` | 10 | Stores the original values in reverse order. |
| `averageArray` | `int` | 10 | Stores the intermediate calculations used to produce the displayed averages. |

### 3.2 Loop Variable

```c
int i;
```

The variable `i` is an integer used as the loop-control variable.

It determines which array element is accessed during input, processing, and output operations.

The program uses indexes from 0 through 9 because C arrays use zero-based indexing.

### 3.3 Array Index Reference

| Array Index | Element Position |
|---:|---:|
| 0 | First |
| 1 | Second |
| 2 | Third |
| 3 | Fourth |
| 4 | Fifth |
| 5 | Sixth |
| 6 | Seventh |
| 7 | Eighth |
| 8 | Ninth |
| 9 | Tenth |

For example:

```c
originalArray[0]
```

accesses the first element, while:

```c
originalArray[9]
```

accesses the tenth element.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
```

The `main()` function is the entry point of the program.

It contains all variable declarations, input operations, array-processing statements, output operations, and the final return statement.

The program executes sequentially through three primary stages:

1. Input
2. Processing
3. Output

### 4.2 Input Processing – Collecting Ten Values

```c
for (i = 0; i < 10; i++)
{
    printf("Enter value #%d: ", i + 1);
    scanf("%d", &originalArray[i]);
}
```

This `for` loop prompts the user to enter ten integer values.

Each entered value is stored in the corresponding position of `originalArray`.

**Loop components:**

| Component | Code | Purpose |
|---|---|---|
| Initialization | `i = 0` | Starts the loop at array index zero. |
| Condition | `i < 10` | Continues while the index is less than ten. |
| Increment | `i++` | Advances the index by one after each iteration. |

The prompt uses:

```c
i + 1
```

This displays input positions from 1 through 10, even though the array indexes begin at zero.

The input statement:

```c
scanf("%d", &originalArray[i]);
```

uses `%d` to read an integer and `&` to pass the memory address of the corresponding array element.

### 4.3 Processing – Reversing the Array

```c
for (i = 0; i < 10; i++)
{
    reverseArray[i] = originalArray[9 - i];
}
```

This loop reverses the order of the values stored in `originalArray`.

Instead of copying elements using the same index, the program calculates the source index using:

```c
9 - i
```

This causes the program to access the original array from the last element toward the first.

**Index relationship:**

\[
\text{reverseArray}[i]=\text{originalArray}[9-i]
\]

For example:

| Loop Index `i` | Source Index `9 - i` | Assignment |
|---:|---:|---|
| 0 | 9 | `reverseArray[0] = originalArray[9]` |
| 1 | 8 | `reverseArray[1] = originalArray[8]` |
| 2 | 7 | `reverseArray[2] = originalArray[7]` |
| 3 | 6 | `reverseArray[3] = originalArray[6]` |
| 4 | 5 | `reverseArray[4] = originalArray[5]` |
| 5 | 4 | `reverseArray[5] = originalArray[4]` |
| 6 | 3 | `reverseArray[6] = originalArray[3]` |
| 7 | 2 | `reverseArray[7] = originalArray[2]` |
| 8 | 1 | `reverseArray[8] = originalArray[1]` |
| 9 | 0 | `reverseArray[9] = originalArray[0]` |

This technique allows the program to reverse the array without modifying the original data.

### 4.4 Processing – Calculating Corresponding Averages

```c
averageArray[i] = (originalArray[i] + reverseArray[i]) * 5;
```

This statement adds the corresponding elements from the original and reversed arrays and multiplies the result by five.

The multiplication by five is mathematically equivalent to dividing the sum by two and multiplying by ten.

The program uses this calculation because `averageArray` is declared as an integer array, while the actual average may contain a fractional value.

**Intended average formula:**

\[
\text{Average}[i]=
\frac{\text{originalArray}[i]+\text{reverseArray}[i]}{2}
\]

**Actual intermediate calculation:**

\[
\text{averageArray}[i]=
(\text{originalArray}[i]+\text{reverseArray}[i])\times 5
\]

The multiplication by five creates an integer value that represents the average multiplied by ten.

The actual average is recovered later during output by dividing the stored value by `10.0`.

### 4.5 Output Processing – Displaying the Original Array

```c
printf("\nThe original array...\n");

for (i = 0; i < 10; i++)
{
    printf("%d\t", originalArray[i]);
}
```

The program displays a heading and iterates through `originalArray`.

The `%d` format specifier displays each integer, while `\t` inserts tab spacing between values.

### 4.6 Output Processing – Displaying the Reversed Array

```c
printf("\nThe reverse array...\n");

for (i = 0; i < 10; i++)
{
    printf("%d\t", reverseArray[i]);
}
```

This loop displays the values stored in `reverseArray`.

Because the array was populated using the reverse-index calculation, its elements appear in the opposite order from the original input.

### 4.7 Output Processing – Displaying the Average Array

```c
printf("\nThe average array...\n");

for (i = 0; i < 10; i++)
{
    printf("%.1f\t", averageArray[i] / 10.0);
}
```

This loop displays the calculated averages.

The expression:

```c
averageArray[i] / 10.0
```

converts the stored intermediate integer into its actual average value.

Using `10.0` instead of `10` ensures floating-point division rather than integer division.

The format specifier:

```c
%.1f
```

displays each result to one decimal place.

### 4.8 Program Termination

```c
return 0;
```

The `return 0` statement terminates the `main()` function and indicates that the program completed successfully.

## 5. Operators Used

The program uses assignment, arithmetic, relational, and increment operators.

| Operator | Category | Example | Purpose |
|---|---|---|---|
| `=` | Assignment | `reverseArray[i] = originalArray[9 - i];` | Assigns values to array elements. |
| `+` | Arithmetic | `originalArray[i] + reverseArray[i]` | Adds corresponding array values. |
| `-` | Arithmetic | `9 - i` | Calculates the reverse array index. |
| `*` | Arithmetic | `(...) * 5` | Scales the sum to represent the average multiplied by ten. |
| `/` | Arithmetic | `averageArray[i] / 10.0` | Converts the intermediate value into the actual average. |
| `<` | Relational | `i < 10` | Determines whether a loop should continue. |
| `++` | Increment | `i++` | Increases the loop index by one. |
| `&` | Address-of | `&originalArray[i]` | Supplies the memory address of an array element to `scanf()`. |

### 5.1 Assignment Operator

The assignment operator (`=`) stores the result of an expression in a variable or array element.

Example:

```c
reverseArray[i] = originalArray[9 - i];
```

The value retrieved from the original array is assigned to the corresponding position in the reversed array.

### 5.2 Arithmetic Operators

The program uses several arithmetic operations:

- Addition combines corresponding array values.
- Subtraction calculates the reverse index.
- Multiplication scales the sum by five.
- Division converts the intermediate value into the actual average.

### 5.3 Relational Operator

The less-than operator (`<`) controls loop execution.

For example:

```c
i < 10
```

evaluates whether the current index is less than ten.

### 5.4 Increment Operator

The increment operator (`++`) increases the loop variable by one.

```c
i++;
```

This advances the program to the next array element.

### 5.5 Address-of Operator

The address-of operator (`&`) retrieves the memory address of a variable or array element.

```c
scanf("%d", &originalArray[i]);
```

The `scanf()` function requires an address so it can store the user's input directly in the selected array element.

## 6. Program Execution Sequence

The program follows this sequence:

1. The program enters `main()`.
2. Three integer arrays are declared, each containing ten elements.
3. The integer loop variable `i` is declared.
4. The first `for` loop begins with `i = 0`.
5. The program prompts the user to enter the first integer.
6. The input is stored in `originalArray[0]`.
7. The loop increments `i` and repeats until all ten values have been entered.
8. The second `for` loop begins processing the arrays.
9. The program retrieves values from `originalArray` using the reverse index `9 - i`.
10. Each retrieved value is stored in `reverseArray[i]`.
11. The program adds the corresponding original and reversed values.
12. The sum is multiplied by five and stored in `averageArray[i]`.
13. The processing loop repeats until all ten elements have been processed.
14. The program displays the original array.
15. The program displays the reversed array.
16. The program displays the average array after dividing each intermediate value by `10.0`.
17. The program returns zero and terminates.

## 7. Text-Based Program Flowchart

### 7.1 Main Program Flow

```text
              +----------------------+
              |        START         |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | Declare Three Arrays |
              | and Loop Variable    |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | Initialize i = 0     |
              +----------+-----------+
                         |
                         v
              +----------------------+
              |       i < 10?        |
              +----------+-----------+
                         |
                 +-------+-------+
                 |               |
                YES              NO
                 |               |
                 v               v
       +------------------+  +----------------------+
       | Prompt User for  |  | Initialize Processing|
       | Integer Value    |  | Loop: i = 0          |
       +--------+---------+  +----------+-----------+
                |                       |
                v                       v
       +------------------+  +----------------------+
       | Store Value in   |  |       i < 10?        |
       | originalArray[i] |  +----------+-----------+
       +--------+---------+             |
                |                +------+------+
                v                |             |
       +------------------+     YES            NO
       | Increment i      |      |             |
       +--------+---------+      v             v
                |       +----------------+  +------------------+
                +------>| Retrieve Value |  | Display Original |
                        | Using 9 - i    |  | Array            |
                        +--------+-------+  +--------+---------+
                                 |                    |
                                 v                    v
                        +----------------+  +------------------+
                        | Store Reversed |  | Display Reversed |
                        | Array Element  |  | Array            |
                        +--------+-------+  +--------+---------+
                                 |                    |
                                 v                    v
                        +----------------+  +------------------+
                        | Calculate      |  | Display Average  |
                        | Intermediate   |  | Array            |
                        | Average        |  +--------+---------+
                        +--------+-------+           |
                                 |                    v
                                 v            +------------------+
                        +----------------+   |     return 0     |
                        | Increment i    |   +--------+---------+
                        +--------+-------+            |
                                 |                    v
                                 +-----> i < 10?  +------------------+
                                                  |       END        |
                                                  +------------------+
```

### 7.2 Array Reversal Logic

```text
       +--------------------------+
       | Begin Reversal Loop      |
       | i = 0                    |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Is i less than 10?       |
       +------------+-------------+
                    |
              +-----+-----+
              |           |
             YES          NO
              |           |
              v           v
       +----------------+  +----------------------+
       | Calculate      |  | Reversal Complete    |
       | Source Index   |  +----------------------+
       | 9 - i          |
       +--------+-------+
                |
                v
       +--------------------------+
       | Assign Original Value    |
       | to reverseArray[i]       |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Increment i              |
       +------------+-------------+
                    |
                    +------> Return to Condition
```

### 7.3 Average Calculation Logic

```text
       +--------------------------+
       | Begin Average Loop       |
       | i = 0                    |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Is i less than 10?       |
       +------------+-------------+
                    |
              +-----+-----+
              |           |
             YES          NO
              |           |
              v           v
       +----------------+  +----------------------+
       | Add Corresponding| | Average Processing |
       | Array Elements |  | Complete             |
       +--------+-------+  +----------------------+
                |
                v
       +--------------------------+
       | Multiply Sum by 5        |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Store in averageArray[i] |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Increment i              |
       +------------+-------------+
                    |
                    +------> Return to Condition
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Array Declaration and Initialization

The program demonstrates how arrays are declared using a data type, identifier, and fixed element count.

```c
int originalArray[10];
```

This creates an array capable of storing ten integer values.

The program does not initialize the array when it is declared. Instead, the input loop populates every element before the array is processed.

### 8.2 Zero-Based Array Indexing

C uses zero-based indexing, meaning the first element of an array is located at index zero.

For a ten-element array, the valid indexes are 0 through 9.

Understanding this indexing system is essential when accessing, modifying, or reversing array elements.

### 8.3 Parallel Array Processing

The program uses three arrays with corresponding indexes.

- `originalArray[i]` stores the original value.
- `reverseArray[i]` stores the corresponding value from the opposite end of the original array.
- `averageArray[i]` stores the intermediate calculation for those two values.

This demonstrates how multiple arrays can be processed together using a shared loop-control variable.

### 8.4 Array Reversal

The program demonstrates reverse indexing through:

```c
originalArray[9 - i]
```

This technique accesses the original array in descending index order without changing the original array.

### 8.5 Iteration Using For Loops

The program uses `for` loops to automate repetitive tasks.

The loops handle:

- Collecting ten user-provided values.
- Reversing the array.
- Calculating corresponding averages.
- Displaying the original array.
- Displaying the reversed array.
- Displaying the average array.

### 8.6 Integer and Floating-Point Arithmetic

The program stores its arrays as integers but performs floating-point division when displaying the average results.

The expression:

```c
averageArray[i] / 10.0
```

uses a floating-point divisor to produce decimal output.

### 8.7 Formatted Input and Output

The program uses standard input/output functions to collect and display data.

| Format / Escape Sequence | Purpose |
|---|---|
| `%d` | Reads or displays an integer. |
| `%.1f` | Displays a floating-point value to one decimal place. |
| `\n` | Moves output to a new line. |
| `\t` | Inserts horizontal tab spacing. |
| `&` | Supplies the memory address required by `scanf()`. |

## 9. Program Characteristics and Limitations

### 9.1 Fixed Array Size

The program is designed to process exactly ten integer values.

The array sizes and loop conditions are hardcoded to ten elements. Processing a different number of values would require changes to the declarations and loop conditions.

### 9.2 Original Array Preservation

The program does not modify `originalArray` during reversal.

Instead, it copies the values into `reverseArray` using reverse indexing.

This preserves the original input for comparison and display.

### 9.3 Average Calculation Implementation

The source code declares `averageArray` as an integer array.

It calculates:

```c
averageArray[i] = (originalArray[i] + reverseArray[i]) * 5;
```

The program later divides the stored value by `10.0` when displaying the result.

This produces the mathematical average while preserving the intermediate calculation as an integer, provided the arithmetic does not overflow.

A more direct implementation could declare `averageArray` as a `double` array and calculate:

```c
double averageArray[10];

averageArray[i] =
    (originalArray[i] + reverseArray[i]) / 2.0;
```

This is an alternative implementation, not the code used in the original source.

### 9.4 Integer Overflow

The original and reversed values are stored as integers.

Their addition and multiplication by five are also performed using integer arithmetic before assignment to `averageArray`.

If the user enters sufficiently large positive or negative values, these operations can exceed the range of the `int` data type, resulting in signed integer overflow.

### 9.5 Input Validation

The program uses:

```c
scanf("%d", &originalArray[i]);
```

It does not check the return value of `scanf()`.

Consequently, it assumes that the user enters valid integer values. Nonnumeric input is not handled explicitly.

### 9.6 Duplicate Values

The program does not require the ten input values to be unique.

Repeated values are accepted and processed normally.

### 9.7 Array Reversal and Average Relationship

The program calculates averages between matching positions in the original and reversed arrays.

For example, the first average combines the first original value with the last original value. The second average combines the second original value with the second-to-last original value.

This means each original value is paired with its counterpart from the opposite end of the array.

## 10. Overall Summary

Reverse and Average demonstrates how arrays can be used to store, manipulate, and process multiple related values in the C programming language.

The program collects ten integer values from the user, stores them in an original array, and creates a reversed copy using reverse indexing. It then calculates the average of corresponding elements from the original and reversed arrays and displays the results.

The source code demonstrates array declarations, zero-based indexing, parallel array processing, `for` loops, assignment statements, arithmetic operators, address-of operations, formatted input/output, and integer-to-floating-point conversion during output.

Overall, the program provides a practical example of array manipulation and demonstrates how multiple arrays can work together to perform structured data-processing operations.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational, instructional, and programming-reference purposes. It is intended to demonstrate C programming concepts, including array declarations, zero-based indexing, array reversal, parallel array processing, loops, arithmetic operations, variable declarations, and formatted input/output.

This source code is not intended to be submitted as another student's original work, used to circumvent coursework requirements, or used for plagiarism or academic dishonesty.

Students should maintain academic integrity by understanding the source code, independently completing assigned coursework, and following their institution's academic policies.

The author is not responsible for unauthorized use, academic misconduct, plagiarism, cheating, or any other misuse of this program or its contents.