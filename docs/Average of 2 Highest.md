# Average of 2 Highest – C Programming Project Documentation

**Programmer:** Brian Lorick  
**Program Name:** Average of 2 Highest  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio 2019  
**Course Topic:** Chapter 3 – Decisions  
**Original Date:** February 15, 2024  
**Source File:** `Average of 2 Highest.cpp`

---

## 1. Program Overview

The **Average of 2 Highest** program is a C application that prompts the user to enter three non-zero positive integer values. It validates each input, determines which two values are the highest, calculates their arithmetic average, and displays the two highest numbers along with the resulting average.

The program demonstrates decision-making structures using `if`, `else if`, and `else` statements, as well as relational and logical operators to compare numerical values.

The program follows three primary stages:

1. **Input and Validation** – Collects three integer values and verifies that each is greater than zero.
2. **Processing** – Compares the three values to identify the highest and second-highest numbers, then calculates their average.
3. **Output** – Displays the two highest numbers and their calculated average.

Unlike programs that use arrays or loops, this program relies on nested conditional statements to evaluate the possible ordering of three input values.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive | Purpose |
|---|---|
| `#include <stdio.h>` | Includes the Standard Input/Output library, providing access to `printf()` and `scanf()`. |

### 2.2 Standard Library Functions

| Function | Purpose |
|---|---|
| `printf()` | Displays input prompts, validation messages, and the final calculation. |
| `scanf()` | Accepts integer values entered by the user and stores them in variables. |

The program uses the standard input/output library for all console interactions. No additional libraries are required.

## 3. Variables and Data Structures

### 3.1 Constant Variable

| Identifier | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `VALIDATION_LIMIT` | `const int` | `0` | Establishes the minimum acceptable input boundary. Values less than or equal to zero are rejected. |

The declaration:

```c
const int VALIDATION_LIMIT = 0;
```

Creates a constant integer that cannot be reassigned during program execution. Using a named constant makes the validation condition easier to understand and maintain.

### 3.2 Integer Variables

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `numOne` | `int` | `0` | Stores the first integer entered by the user. |
| `numTwo` | `int` | `0` | Stores the second integer entered by the user. |
| `numThree` | `int` | `0` | Stores the third integer entered by the user. |
| `highestOne` | `int` | `0` | Stores the highest of the three input values. |
| `highestTwo` | `int` | `0` | Stores the second-highest of the three input values. |

### 3.3 Floating-Point Variable

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `highAverage` | `double` | `0.0` | Stores the calculated average of the two highest numbers. |

The `double` data type allows the program to retain decimal precision when calculating the average of two integers.

### 3.4 Variable Relationships

The program uses the following relationship to determine its final result:

- `numOne`, `numTwo`, and `numThree` hold the original user inputs.
- `highestOne` holds the greatest input value.
- `highestTwo` holds the greater of the two remaining values.
- `highAverage` stores the arithmetic average of `highestOne` and `highestTwo`.

No arrays, pointers, or user-defined functions are used in this implementation. All variables and processing logic are contained within `main()`.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
{
    // Program statements

    return 0;
}
```

The `main()` function serves as the program's entry point. All input, validation, comparison, calculation, and output operations are executed within this function.

The `void` parameter indicates that `main()` does not receive command-line arguments.

The statement `return 0;` indicates normal program termination.

### 4.2 Input Collection

The program prompts the user for three integer values using separate `printf()` and `scanf()` statements.

```c
printf("Enter the 1st non-zero positive number: ");
scanf("%d", &numOne);

printf("Enter the 2nd non-zero positive number: ");
scanf("%d", &numTwo);

printf("Enter the 3rd non-zero positive number: ");
scanf("%d", &numThree);
```

The `%d` format specifier tells `scanf()` to read an integer.

The address-of operator (`&`) supplies the memory address of the destination variable so that the entered value can be stored.

Each input is collected individually rather than through a loop.

### 4.3 Input Validation

After each value is entered, the program checks whether it is a valid non-zero positive integer.

```c
if (numOne <= VALIDATION_LIMIT)
{
    printf("The 1st number, %d, was not a non-zero positive number.\n", numOne);
    return 0;
}
```

The same validation structure is repeated for `numTwo` and `numThree`.

The condition:

```c
numOne <= VALIDATION_LIMIT
```

Checks whether the entered value is less than or equal to zero.

If the condition evaluates to true:

1. An error message is displayed.
2. The program executes `return 0;`.
3. Program execution terminates immediately.
4. The remaining inputs and calculations are not performed.

If the condition evaluates to false, the program continues to the next statement.

**Important:** The validation rejects zero and negative integers. It does not explicitly validate whether the user entered numeric data; the program assumes valid integer input.

### 4.4 Determining the Two Highest Numbers

The program uses a series of nested conditional statements to identify the highest and second-highest values.

The first conditional evaluates whether `numOne` is greater than or equal to both other values.

```c
if (numOne >= numTwo && numOne >= numThree)
{
    highestOne = numOne;

    if (numTwo >= numThree)
    {
        highestTwo = numTwo;
    }
    else
    {
        highestTwo = numThree;
    }
}
```

If `numOne` is the highest, it is assigned to `highestOne`. The nested `if` statement then compares `numTwo` and `numThree` to determine which is second-highest.

The second conditional evaluates whether `numTwo` is the highest.

```c
else if (numTwo >= numOne && numTwo >= numThree)
{
    highestOne = numTwo;

    if (numOne >= numThree)
    {
        highestTwo = numOne;
    }
    else
    {
        highestTwo = numThree;
    }
}
```

If the first condition is false and this condition is true, `numTwo` becomes `highestOne`. The nested conditional compares the remaining two values to identify `highestTwo`.

The final `else` handles the remaining possibility, where `numThree` is the highest.

```c
else
{
    highestOne = numThree;

    if (numOne >= numTwo)
    {
        highestTwo = numOne;
    }
    else
    {
        highestTwo = numTwo;
    }
}
```

Because the program has already established that all three values are positive integers, one of these three branches will identify the highest value and the second-highest value.

### 4.5 Conditional Logic and Comparison Strategy

The program uses `>=` rather than `>` in its highest-value comparisons.

This allows the conditions to account for equal values.

For example, if the user enters:

```text
25
25
10
```

The first condition evaluates as true because `numOne` is greater than or equal to both other values.

The nested comparison also evaluates as true because `numTwo` is greater than or equal to `numThree`.

The program therefore assigns:

```c
highestOne = 25;
highestTwo = 25;
```

The average is calculated using both occurrences of the highest value.

### 4.6 Calculating the Average

After identifying the two highest values, the program calculates their arithmetic average.

```c
highAverage = (highestOne + (double)highestTwo) / 2;
```

The expression uses a type cast:

```c
(double)highestTwo
```

This converts `highestTwo` from an integer to a `double` before the addition takes place.

The calculation follows this formula:

\[
\text{Average} = \frac{\text{Highest One}+\text{Highest Two}}{2}
\]

For example, if the two highest values are 80 and 60:

\[
\text{Average} = \frac{80+60}{2}=70.00
\]

Using a `double` ensures that the calculation can produce a fractional result when the sum of the two integers is odd.

### 4.7 Displaying the Results

The program displays a heading followed by the two highest numbers and their average.

```c
printf("The average of the 2 highest numbers\n");
```

It then uses another conditional statement to determine the display order.

```c
if (highestOne > highestTwo)
{
    printf("(%d and %d) is: %.2lf.\n", highestOne, highestTwo, highAverage);
}
else
{
    printf("(%d and %d) is: %.2lf.\n", highestTwo, highestOne, highAverage);
}
```

The output conditional ensures that the larger value is displayed first when the two values are different.

The `%.2lf` format specifier displays the average with two digits after the decimal point.

If both values are equal, the `else` branch executes. Because the values are identical, their display order does not affect the result.

## 5. Operators Used

The program uses relational, logical, arithmetic, assignment, and type-conversion operations.

### 5.1 Relational Operators

| Operator | Name | Purpose |
|---|---|---|
| `<=` | Less than or equal to | Validates that an input is greater than zero. |
| `>=` | Greater than or equal to | Compares input values to identify the highest and second-highest numbers. |
| `>` | Greater than | Determines the order in which the two highest numbers are displayed. |

### 5.2 Logical Operators

| Operator | Name | Purpose |
|---|---|---|
| `&&` | Logical AND | Requires both comparison conditions to be true before selecting a conditional branch. |

Example:

```c
numOne >= numTwo && numOne >= numThree
```

Both comparisons must evaluate to true for the entire expression to be true.

### 5.3 Arithmetic Operators

| Operator | Name | Purpose |
|---|---|---|
| `+` | Addition | Adds the two highest values together. |
| `/` | Division | Divides their sum by two to calculate the average. |

### 5.4 Assignment and Type Conversion

| Operation | Name | Purpose |
|---|---|---|
| `=` | Assignment | Assigns values to variables such as `highestOne`, `highestTwo`, and `highAverage`. |
| `(double)` | Explicit type cast | Converts the second-highest integer to a `double` for floating-point arithmetic. |

## 6. Program Execution Sequence

The program follows a sequential decision-making process.

| Step | Operation | Description |
|---:|---|---|
| 1 | Program Start | Execution begins in `main()`. |
| 2 | Variable Initialization | Declares the constant and initializes all variables. |
| 3 | First Input | Prompts the user for the first positive integer. |
| 4 | First Validation | Checks whether `numOne` is greater than zero. |
| 5 | Second Input | Prompts the user for the second positive integer. |
| 6 | Second Validation | Checks whether `numTwo` is greater than zero. |
| 7 | Third Input | Prompts the user for the third positive integer. |
| 8 | Third Validation | Checks whether `numThree` is greater than zero. |
| 9 | First Comparison | Determines whether `numOne` is the highest value. |
| 10 | Second Comparison | If necessary, determines whether `numTwo` is the highest value. |
| 11 | Final Comparison | If neither previous condition is true, assigns `numThree` as the highest value. |
| 12 | Second-Highest Determination | Uses nested conditional statements to identify the second-highest value. |
| 13 | Average Calculation | Adds the two highest values and divides by two. |
| 14 | Output Ordering | Checks which of the two values should be displayed first. |
| 15 | Display Results | Prints the two highest values and their average. |
| 16 | Program Termination | Returns `0` and ends execution. |

**Early termination:** If any input is zero or negative, the program displays an error message and terminates immediately. The comparison and average calculation stages are skipped.

## 7. Text-Based Program Flowchart

```text
                +-------------------------+
                |      PROGRAM START      |
                +-------------------------+
                            |
                            v
                +-------------------------+
                |       main(void)        |
                | Initialize variables    |
                | VALIDATION_LIMIT = 0    |
                +-------------------------+
                            |
                            v
                +-------------------------+
                | Prompt for numOne       |
                | Read integer input      |
                +-------------------------+
                            |
                            v
                    +---------------+
                    | numOne <= 0?  |
                    +---------------+
                      |           |
                    YES           NO
                      |           |
                      v           v
             +----------------+  +-------------------------+
             | Display error  |  | Prompt for numTwo       |
             | return 0       |  | Read integer input      |
             +----------------+  +-------------------------+
                      |                       |
                      v                       v
               +-------------+        +---------------+
               | PROGRAM END |        | numTwo <= 0?  |
               +-------------+        +---------------+
                                        |           |
                                      YES           NO
                                        |           |
                                        v           v
                               +----------------+  +-------------------------+
                               | Display error  |  | Prompt for numThree     |
                               | return 0       |  | Read integer input      |
                               +----------------+  +-------------------------+
                                        |                       |
                                        v                       v
                                 +-------------+        +----------------+
                                 | PROGRAM END |        | numThree <= 0? |
                                 +-------------+        +----------------+
                                                          |           |
                                                        YES           NO
                                                          |           |
                                                          v           v
                                                 +----------------+  +-------------------------+
                                                 | Display error  |  | Is numOne >= numTwo AND |
                                                 | return 0       |  | numOne >= numThree?     |
                                                 +----------------+  +-------------------------+
                                                          |              |                 |
                                                          v             YES                NO
                                                   +-------------+       |                 |
                                                   | PROGRAM END |       v                 v
                                                   +-------------+ +----------------+ +-------------------------+
                                                                    | highestOne =  | | Is numTwo >= numOne AND |
                                                                    | numOne         | | numTwo >= numThree?     |
                                                                    +----------------+ +-------------------------+
                                                                           |             |                 |
                                                                           v            YES                NO
                                                                  +----------------+     |                 |
                                                                  | numTwo >=      |     v                 v
                                                                  | numThree?      | +----------------+ +----------------+
                                                                  +----------------+ | highestOne =  | | highestOne =  |
                                                                    |           |   | numTwo         | | numThree       |
                                                                   YES          NO  +----------------+ +----------------+
                                                                    |           |          |                  |
                                                                    v           v          v                  v
                                                             +----------+ +----------+ +----------------+ +----------------+
                                                             | highestTwo| | highestTwo| | numOne >=    | | numOne >=      |
                                                             | = numTwo  | | = numThree| | numThree?    | | numTwo?        |
                                                             +----------+ +----------+ +----------------+ +----------------+
                                                                    |           |        |          |       |          |
                                                                    |           |       YES         NO     YES         NO
                                                                    |           |        |          |       |          |
                                                                    |           |        v          v       v          v
                                                                    |           |   +----------+ +----------+ +----------+ +----------+
                                                                    |           |   | highestTwo| | highestTwo| | highestTwo| | highestTwo|
                                                                    |           |   | = numOne  | | = numThree| | = numOne  | | = numTwo  |
                                                                    |           |   +----------+ +----------+ +----------+ +----------+
                                                                    |           |        |          |       |          |
                                                                    +-----------+--------+----------+-------+----------+
                                                                                         |
                                                                                         v
                                                                        +-------------------------------+
                                                                        | Calculate average:            |
                                                                        | (highestOne + (double)        |
                                                                        |  highestTwo) / 2              |
                                                                        +-------------------------------+
                                                                                         |
                                                                                         v
                                                                        +-------------------------------+
                                                                        | Is highestOne > highestTwo?   |
                                                                        +-------------------------------+
                                                                            |                    |
                                                                           YES                  NO
                                                                            |                    |
                                                                            v                    v
                                                               +----------------------+ +----------------------+
                                                               | Display highestOne   | | Display highestTwo   |
                                                               | then highestTwo      | | then highestOne      |
                                                               | and average           | | and average           |
                                                               +----------------------+ +----------------------+
                                                                            |                    |
                                                                            +---------+----------+
                                                                                      |
                                                                                      v
                                                                        +----------------------+
                                                                        |      return 0;       |
                                                                        +----------------------+
                                                                                      |
                                                                                      v
                                                                        +----------------------+
                                                                        |     PROGRAM END      |
                                                                        +----------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Decision-Making Statements

The program primarily demonstrates conditional execution using `if`, `else if`, and `else` statements.

These statements allow the program to evaluate conditions and execute different blocks of code depending on whether those conditions are true or false.

### 8.2 Nested Conditional Statements

The program uses nested `if` statements to compare the remaining two numbers after identifying the highest number.

This allows the program to determine the second-highest value without sorting all three numbers.

### 8.3 Relational Comparisons

Relational operators compare numerical values and produce Boolean results that determine which conditional branch executes.

The program uses `<=`, `>=`, and `>` to validate inputs, compare values, and control output ordering.

### 8.4 Logical AND

The logical AND operator (`&&`) combines two relational expressions.

Both expressions must be true for the overall condition to evaluate as true.

### 8.5 Constants

The `VALIDATION_LIMIT` constant establishes a reusable validation boundary.

Using a named constant instead of repeatedly writing `0` makes the validation logic more descriptive.

### 8.6 Type Casting

The program uses explicit type conversion to convert an integer into a `double`.

```c
(double)highestTwo
```

This ensures floating-point arithmetic is performed when calculating the average.

### 8.7 Input Validation and Early Termination

The program checks each input before continuing.

When an invalid value is detected, `return 0;` terminates execution rather than allowing invalid data to enter the comparison and calculation stages.

### 8.8 Arithmetic Calculations

The program applies addition and division to calculate the arithmetic mean of the two highest values.

### 8.9 Formatted Output

The program uses `printf()` format specifiers to display integer values and a floating-point result.

The `%.2lf` format controls the displayed precision of the average.

## 9. Program Characteristics and Limitations

| Characteristic | Description |
|---|---|
| Input Quantity | Accepts exactly three integer values. |
| Input Requirement | All values must be greater than zero. |
| Data Types | Uses `int`, `const int`, and `double`. |
| Decision Structure | Uses `if`, `else if`, `else`, and nested `if` statements. |
| Comparison Method | Uses relational and logical operators. |
| Highest-Value Selection | Identifies the highest and second-highest values through conditional comparisons. |
| Calculation | Computes the average of the two highest values. |
| Type Conversion | Explicitly casts an integer to `double`. |
| Output Precision | Displays the average to two decimal places. |
| Program Structure | All logic is contained in `main()`. |
| Termination | Uses `return 0;` for normal and validation-triggered termination. |

### 9.1 Input Validation Limitations

The program validates whether entered integer values are positive and non-zero.

However, it does not check the return value of `scanf()`. If a user enters nonnumeric data, the program does not have a dedicated recovery mechanism.

### 9.2 Fixed Input Quantity

The program always requests three values. The number of inputs is not configurable by the user.

### 9.3 Integer Input Restrictions

The input variables use the `int` data type. Therefore, the program accepts integer values rather than decimal input values.

### 9.4 No Sorting Algorithm

The program does not use a sorting algorithm or array. Instead, it evaluates the possible highest-value combinations through conditional statements.

This approach is appropriate for the fixed requirement of comparing exactly three numbers.

### 9.5 Equal Values

The use of `>=` allows the program to handle duplicate values when determining the two highest numbers.

For example, if the inputs are `90`, `90`, and `50`, the two highest values are both `90`, and the resulting average is `90.00`.

## 10. Overall Summary

The **Average of 2 Highest** program demonstrates fundamental C programming decision-making concepts by collecting three positive integer values, validating each input, identifying the two highest numbers, and calculating their arithmetic average.

The program uses a constant to establish its validation boundary and conditional statements to control execution. A combination of relational operators and the logical AND operator determines which input value is highest. Nested conditional statements then identify the second-highest value from the remaining two inputs.

Once both values have been identified, the program uses addition, explicit type casting, and division to calculate their average. Finally, formatted output statements display the two selected values and the result to two decimal places.

The primary programming concepts demonstrated include input validation, constants, variable initialization, decision-making statements, nested conditionals, relational operators, logical operators, arithmetic calculations, type casting, and formatted console output.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, particularly decision-making structures, conditional statements, relational operators, logical operators, input validation, and arithmetic calculations.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.