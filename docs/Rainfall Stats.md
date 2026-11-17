# Rainfall Stats – C Program Documentation

| **Program Information** | **Details** |
|---|---|
| Program Name | Rainfall Stats |
| Programmer(s) | Brian Lorick & Tyler Goss |
| Programming Language | C |
| Development Environment | Microsoft Visual Studio |
| Course Topic | Chapter 5 – Arrays |
| Original Date | March 13, 2024 |
| Source File | `Rainfall Stats.c` |

---

## 1. Program Overview

**Rainfall Stats** is a C program designed to collect and analyze rainfall measurements for all twelve months of a calendar year. The program prompts the user to enter the amount of rainfall, measured in inches, for each month.

After collecting the twelve measurements, the program processes the data using arrays, loops, conditional statements, arithmetic operations, and comparison operators to calculate and identify several statistical values.

The program produces the following results:

- Total rainfall for the year.
- Average monthly rainfall.
- Lowest monthly rainfall and its corresponding month.
- Highest monthly rainfall and its corresponding month.
- A formatted display of the rainfall measurements organized by month.

The program demonstrates how arrays can store related data and how loops and conditional statements can process that data efficiently.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directive

```c
#define _CRT_SECURE_NO_WARNINGS
```

This preprocessor directive disables Microsoft Visual C runtime warnings associated with certain standard C library functions, including `scanf()`.

It allows the program to use standard input functions without displaying Microsoft's secure-function warning messages.

### 2.2 Standard Input/Output Library

```c
#include <stdio.h>
```

The `stdio.h` header file provides the standard input/output functions used by the program.

| Function | Purpose |
|---|---|
| `printf()` | Displays prompts, rainfall values, and calculated statistics. |
| `scanf()` | Accepts rainfall measurements entered by the user. |

## 3. Variables and Data Structures

The program uses variables to store rainfall measurements, perform calculations, and track the months associated with the highest and lowest rainfall values.

### 3.1 Array Declarations

**Rainfall Array**

```c
double rainfall[13];
```

The `rainfall` array stores the rainfall measurement entered for each month.

Although the program processes twelve months, the array contains thirteen elements. This allows the program to use indexes 1 through 12 instead of the conventional 0 through 11.

| Index | Month |
|---:|---|
| 1 | January |
| 2 | February |
| 3 | March |
| 4 | April |
| 5 | May |
| 6 | June |
| 7 | July |
| 8 | August |
| 9 | September |
| 10 | October |
| 11 | November |
| 12 | December |

Index 0 is intentionally left unused.

**Months Array**

```c
const char* months[13] = {
    "", "Jan", "Feb", "Mar", "Apr", "May",
    "Jun", "Jul", "Aug", "Sep", "Oct",
    "Nov", "Dec"
};
```

The `months` array stores abbreviated month names as strings.

The `const char*` declaration identifies an array of pointers to constant character strings. The program uses the same numerical indexes for both arrays, allowing it to associate each rainfall measurement with the correct month.

### 3.2 Variable Reference

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `rainfall[13]` | `double` array | Uninitialized | Stores twelve monthly rainfall measurements. |
| `months[13]` | `const char*` array | Month names | Stores abbreviated month names. |
| `total` | `double` | `0.0` | Accumulates annual rainfall. |
| `average` | `double` | Uninitialized | Stores average monthly rainfall. |
| `lowest` | `double` | `999.9` | Tracks the smallest rainfall measurement. |
| `highest` | `double` | `0.0` | Tracks the largest rainfall measurement. |
| `lowestIndex` | `int` | Uninitialized | Stores the index of the month with the lowest rainfall. |
| `highestIndex` | `int` | Uninitialized | Stores the index of the month with the highest rainfall. |
| `i` | `int` | Loop-dependent | Controls the iterations of the `for` loops. |

### 3.3 Data Types

The program uses two primary data types:

- **`double`** – Stores rainfall measurements and statistical calculations with decimal precision.
- **`int`** – Stores array indexes and controls loop iterations.

The `const char*` data type is used for the month-name strings.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
```

The `main()` function serves as the program's entry point. All variable declarations, input operations, calculations, and output statements are contained within this function.

The program executes sequentially, beginning with variable initialization and continuing through data collection, statistical processing, and output.

### 4.2 Input Processing Loop

```c
for (int i = 1; i <= 12; i++)
{
    printf("Enter the rainfall (in inches) for %s: ", months[i]);
    scanf(" %lf", &rainfall[i]);
    total += rainfall[i];

    if (rainfall[i] < lowest)
    {
        lowest = rainfall[i];
        lowestIndex = i;
    }

    if (rainfall[i] > highest)
    {
        highest = rainfall[i];
        highestIndex = i;
    }
}
```

This `for` loop collects the rainfall measurements for all twelve months.

**Loop components:**

1. Initialization: `int i = 1` establishes the starting array index.
2. Condition: `i <= 12` determines whether another month should be processed.
3. Increment: `i++` advances the index by one after each iteration.

During each iteration, the program:

- Displays the current month using `months[i]`.
- Accepts a rainfall measurement using `scanf()`.
- Stores the measurement in `rainfall[i]`.
- Adds the measurement to the annual total.
- Compares the measurement against the current lowest value.
- Compares the measurement against the current highest value.
- Updates the corresponding value and month index when a new minimum or maximum is found.

The loop executes twelve times, once for each month.

### 4.3 Accumulating Total Rainfall

```c
total += rainfall[i];
```

The `+=` compound assignment operator adds the current month's rainfall to the running total.

This is equivalent to:

```c
total = total + rainfall[i];
```

After all twelve iterations, `total` contains the accumulated rainfall for the year.

### 4.4 Identifying the Lowest Rainfall

```c
if (rainfall[i] < lowest)
{
    lowest = rainfall[i];
    lowestIndex = i;
}
```

The `if` statement evaluates whether the current rainfall measurement is less than the lowest value recorded so far.

If the condition evaluates to true:

- `lowest` is updated with the current rainfall measurement.
- `lowestIndex` stores the corresponding month index.

This process continues throughout the input loop until all twelve measurements have been evaluated.

### 4.5 Identifying the Highest Rainfall

```c
if (rainfall[i] > highest)
{
    highest = rainfall[i];
    highestIndex = i;
}
```

This conditional statement performs the opposite comparison.

It checks whether the current rainfall measurement exceeds the highest value recorded so far.

When a higher measurement is found:

- `highest` is updated.
- `highestIndex` stores the corresponding month index.

### 4.6 Displaying the Rainfall Measurements

The program displays the collected measurements in two groups to make the results easier to read.

**January through June:**

```c
for (int i = 1; i <= 6; i++)
{
    printf("%s\t", months[i]);
}

printf("\n");

for (int i = 1; i <= 6; i++)
{
    printf("%.1lf\t", rainfall[i]);
}
```

The first loop displays the month names for January through June. The second loop displays their corresponding rainfall measurements.

**July through December:**

```c
for (int i = 7; i <= 12; i++)
{
    printf("%s\t", months[i]);
}

printf("\n");

for (int i = 7; i <= 12; i++)
{
    printf("%.1lf\t", rainfall[i]);
}
```

These loops perform the same operation for July through December.

The `\t` escape sequence inserts tab spacing between values, while `\n` moves output to a new line.

### 4.7 Calculating Average Rainfall

```c
average = total / 12.0;
```

The program calculates the average monthly rainfall by dividing the accumulated annual rainfall by twelve.

**Formula:**

\[
\text{Average Rainfall}=\frac{\text{Total Rainfall}}{12}
\]

The divisor `12.0` ensures that the calculation uses floating-point arithmetic.

### 4.8 Displaying Statistical Results

```c
printf("The total rain that fell was %.1lf inches.\n", total);

printf("The average monthly rainfall was %.1lf inches.\n", average);

printf("The lowest monthly rainfall was %.1lf inches in %s.\n",
       lowest, months[lowestIndex]);

printf("The highest monthly rainfall was %.1lf inches in %s.\n",
       highest, months[highestIndex]);
```

These statements display the calculated statistics.

The program uses the stored indexes to retrieve the appropriate month names from the `months` array.

The conditional expressions in the original source are:

```c
(lowestIndex <= 6) ? months[lowestIndex] : months[lowestIndex]
```

```c
(highestIndex <= 6) ? months[highestIndex] : months[highestIndex]
```

Both branches of each conditional expression return the same array element. Therefore, the expressions are functionally equivalent to simply using:

```c
months[lowestIndex]
months[highestIndex]
```

The original expressions do not change the program's output.

## 5. Operators Used

The program uses arithmetic, relational, assignment, increment, and conditional operators.

| Operator | Category | Purpose |
|---|---|---|
| `=` | Assignment | Assigns values to variables. |
| `+=` | Compound assignment | Adds rainfall measurements to `total`. |
| `<` | Relational | Determines whether a measurement is lower than the current minimum. |
| `>` | Relational | Determines whether a measurement is higher than the current maximum. |
| `<=` | Relational | Controls loop termination and evaluates conditional expressions. |
| `/` | Arithmetic | Calculates average rainfall. |
| `++` | Increment | Advances loop indexes. |
| `?:` | Conditional | Selects a result based on a Boolean condition. |

### 5.1 Arithmetic Operations

The program performs addition and division.

- Addition accumulates the twelve rainfall measurements.
- Division calculates the average monthly rainfall.

### 5.2 Relational Operations

The `<` and `>` operators compare rainfall measurements to identify the lowest and highest values.

The `<=` operator controls the execution of the loops and appears in the conditional expressions used when displaying the results.

### 5.3 Conditional Operator

The `?:` operator is known as the ternary or conditional operator.

Its general syntax is:

```c
condition ? expression_if_true : expression_if_false;
```

In this program, both possible expressions return the same month-array element, making the conditional operator unnecessary for the intended output.

## 6. Program Execution Sequence

The program follows a structured sequence of operations:

1. The program enters `main()`.
2. Variables and arrays are declared.
3. The `total`, `lowest`, and `highest` variables are initialized.
4. A `for` loop begins collecting monthly rainfall measurements.
5. Each measurement is stored in the `rainfall` array.
6. Each measurement is added to the annual total.
7. Conditional statements compare the measurement against the current minimum and maximum.
8. The corresponding month indexes are updated when necessary.
9. The input loop completes after December.
10. The program displays January through June.
11. The program displays July through December.
12. The average monthly rainfall is calculated.
13. The total and average rainfall are displayed.
14. The lowest and highest rainfall measurements and their corresponding months are displayed.
15. The program returns `0` and terminates.

## 7. Text-Based Program Flowchart

### 7.1 Main Program Flow

```text
              +----------------------+
              |        START         |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | Declare Variables    |
              | and Initialize       |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | Initialize i = 1     |
              +----------+-----------+
                         |
                         v
              +----------------------+
              |      i <= 12?        |
              +----------+-----------+
                         |
                +--------+--------+
                |                 |
               YES                NO
                |                 |
                v                 v
      +-------------------+  +----------------------+
      | Prompt for Month  |  | Display Rainfall     |
      | and Read Rainfall |  | Measurements         |
      +---------+---------+  +----------+-----------+
                |                       |
                v                       v
      +-------------------+  +----------------------+
      | Add Rainfall to   |  | Calculate Average    |
      | Annual Total      |  | Rainfall             |
      +---------+---------+  +----------+-----------+
                |                       |
                v                       v
      +-------------------+  +----------------------+
      | Rainfall[i] <     |  | Display Total and    |
      | Lowest?           |  | Average Rainfall     |
      +---------+---------+  +----------+-----------+
                |                       |
          +-----+-----+                 v
          |           |       +----------------------+
         YES          NO      | Display Lowest and   |
          |           |       | Highest Rainfall     |
          v           |       +----------+-----------+
      +-------------------+               |
      | Update Lowest and |               v
      | Lowest Index      |       +------------------+
      +---------+---------+       |       END        |
                |                 +------------------+
                v
      +-------------------+
      | Rainfall[i] >     |
      | Highest?          |
      +---------+---------+
                |
          +-----+-----+
          |           |
         YES          NO
          |           |
          v           |
      +-------------------+
      | Update Highest and|
      | Highest Index     |
      +---------+---------+
                |
                v
      +-------------------+
      | Increment i       |
      +---------+---------+
                |
                +-----------> Return to i <= 12
```

### 7.2 Statistical Processing Flow

```text
        +----------------------+
        | Twelve Values Stored |
        +----------+-----------+
                   |
                   v
        +----------------------+
        | Calculate Total      |
        | Rainfall             |
        +----------+-----------+
                   |
                   v
        +----------------------+
        | Divide Total by 12   |
        +----------+-----------+
                   |
                   v
        +----------------------+
        | Obtain Average       |
        +----------+-----------+
                   |
                   v
        +----------------------+
        | Retrieve Lowest and  |
        | Highest Month Names  |
        +----------+-----------+
                   |
                   v
        +----------------------+
        | Display Statistics   |
        +----------+-----------+
                   |
                   v
        +----------------------+
        |         END          |
        +----------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Arrays

The program demonstrates how arrays store multiple related values under one variable name.

Instead of creating twelve separate rainfall variables, the program uses:

```c
double rainfall[13];
```

Each measurement is accessed using its corresponding index.

### 8.2 Parallel Arrays

The `rainfall` and `months` arrays operate together.

Both arrays use the same index to associate a rainfall measurement with a month name.

For example:

```c
rainfall[1]
months[1]
```

Both elements represent January.

This technique is commonly referred to as using parallel arrays.

### 8.3 For Loops

The program uses `for` loops to perform repetitive operations without writing separate statements for every month.

The loops handle:

- Collecting twelve rainfall measurements.
- Displaying the first six months.
- Displaying the last six months.
- Displaying corresponding rainfall values.

### 8.4 Conditional Statements

The `if` statements evaluate rainfall measurements and determine whether the current values should replace the recorded minimum or maximum.

These conditions allow the program to identify statistical extremes while processing the array.

### 8.5 Accumulator Variables

The `total` variable functions as an accumulator.

Each rainfall measurement is added to the existing value until the entire year has been processed.

### 8.6 Index Tracking

The `lowestIndex` and `highestIndex` variables preserve the array positions of the smallest and largest measurements.

This allows the program to retrieve the associated month names after the input loop finishes.

### 8.7 Formatted Output

The program uses formatting specifiers to control how information appears.

| Format Specifier | Purpose |
|---|---|
| `%d` | Integer values. |
| `%lf` | Floating-point input with `scanf()`. |
| `%.1lf` | Displays a floating-point value to one decimal place with `printf()`. |
| `%s` | Displays a string. |
| `\n` | Starts a new line. |
| `\t` | Inserts a tab. |

## 9. Program Characteristics and Limitations

The source code demonstrates the intended array-processing and statistical concepts. There are also several implementation details worth understanding.

### 9.1 Array Indexing

The program declares arrays with thirteen elements but uses indexes 1 through 12.

This makes the month-to-index relationship easier to follow, but leaves index 0 unused.

A conventional C implementation could instead use twelve elements and indexes 0 through 11.

### 9.2 Initial Minimum and Maximum Values

The program initializes:

```c
double lowest = 999.9;
double highest = 0.0;
```

These initial values establish starting comparison boundaries.

However, the program assumes the entered rainfall measurements fall within an appropriate nonnegative range. It does not validate whether the user enters negative values or unusually large values.

### 9.3 Input Validation

The program uses:

```c
scanf(" %lf", &rainfall[i]);
```

It does not check the return value of `scanf()`.

Consequently, invalid or nonnumeric input is not handled explicitly. The program assumes the user enters valid numerical rainfall measurements.

### 9.4 Equal Measurements

The program uses strict comparisons:

```c
rainfall[i] < lowest
rainfall[i] > highest
```

If two or more months have the same lowest or highest measurement, the program retains the first month encountered with that value. It does not report every month tied for the minimum or maximum.

### 9.5 Conditional Expressions

The ternary expressions used when displaying the lowest and highest months contain identical true and false branches.

They do not affect the output, but could be simplified to direct array references.

### 9.6 Decimal Precision

The program stores calculations using the `double` data type but displays rainfall statistics to one decimal place.

This means the displayed values are rounded for presentation; the underlying calculations retain greater floating-point precision.

## 10. Overall Summary

Rainfall Stats demonstrates the use of arrays, parallel arrays, iteration, conditional logic, arithmetic operations, and formatted input/output in the C programming language.

The program collects twelve monthly rainfall measurements, stores them in an indexed array, and processes the values to calculate annual and monthly statistics. It uses accumulator logic to calculate total rainfall, division to determine the average, and relational comparisons to identify the lowest and highest rainfall measurements.

The associated month indexes allow the program to retrieve and display the month names corresponding to the statistical results.

Overall, the program provides a practical example of how arrays and control structures can be combined to process a collection of related numerical data.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational, instructional, and programming-reference purposes. It is intended to demonstrate concepts associated with C programming, including arrays, parallel arrays, loops, conditional statements, arithmetic operations, variable declarations, and formatted input/output.

This source code is not intended to be submitted as another student's original work, used to circumvent coursework requirements, or used for plagiarism or academic dishonesty.

Students should maintain academic integrity by understanding the source code, independently completing assigned coursework, and following their institution's academic policies.

The author(s) are not responsible for unauthorized use, academic misconduct, plagiarism, cheating, or any other misuse of this program or its contents.