# Minutes, Hours, Days – C Programming Project Documentation

**Programmer:** Brian Lorick  
**Program Name:** Minutes, Hours, Days  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio  
**Course Topic:** Chapter 3 – Decisions  
**Original Date:** February 9, 2024  
**Source File:** `Minutes, Hours, Days.c`

---

## 1. Program Overview

The **Minutes, Hours, Days** program is a C application that prompts the user to enter a numerical value representing an amount of time in seconds. The program then determines whether the entered value can be converted into minutes, hours, and days and displays the applicable conversions.

The program uses conditional statements to validate the input and determine which time conversions should be displayed.

The program follows three primary stages:

1. **Input** – Prompts the user to enter a number of seconds and stores the value in a `long int` variable.
2. **Processing** – Validates that the entered value is greater than zero and evaluates whether it meets the minimum number of seconds required for each conversion.
3. **Output** – Displays the applicable conversions using floating-point calculations formatted to two decimal places.

The program demonstrates fundamental C programming concepts, including constants, variable declarations, input/output operations, conditional statements, relational operators, arithmetic operations, and formatted output.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive | Purpose |
|---|---|
| `#define _CRT_SECURE_NO_WARNINGS` | Disables Microsoft Visual Studio warnings associated with certain standard C functions, including `scanf()`. |
| `#include <stdio.h>` | Includes the Standard Input/Output library, providing access to `printf()` and `scanf()`. |

### 2.2 Standard Library Functions

| Function | Purpose |
|---|---|
| `printf()` | Displays the input prompt, conversion results, and validation error message. |
| `scanf()` | Accepts the user's numerical input and stores it in the `numSec` variable. |

The program uses `<stdio.h>` for console input and output. No additional libraries or user-defined functions are required.

## 3. Variables and Data Structures

### 3.1 Integer Variable

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `numSec` | `long int` | `0` | Stores the number of seconds entered by the user. |

The program uses `long int` to store the user's numerical input.

The variable is initialized to zero before the input operation.

The `long int` data type provides a larger integer range than a standard `int` on many implementations, allowing the program to represent larger quantities of seconds.

### 3.2 Constant Variables

The program declares three constant integer variables representing the number of seconds in each unit of time.

| Constant | Data Type | Value | Purpose |
|---|---|---:|---|
| `SEC_PER_MIN` | `const int` | `60` | Represents the number of seconds in one minute. |
| `SEC_PER_HOUR` | `const int` | `3600` | Represents the number of seconds in one hour. |
| `SEC_PER_DAY` | `const int` | `86400` | Represents the number of seconds in one day. |

The `const` keyword prevents these values from being modified during program execution.

Using named constants makes the conversion calculations easier to read and maintain.

### 3.3 Data Structures

The program does not use arrays, structures, pointers, or other aggregate data structures.

It relies on one integer variable to store the user's input and three constants to define the conversion values.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
{
    // Constant and Variable Declarations

    // Input

    // Processing and Output

    // Error Handling

    return 0;
}
```

The `main()` function is the program's entry point.

All variable declarations, input operations, conditional statements, conversion calculations, output operations, and error handling are contained within this function.

The parameter `void` indicates that `main()` does not receive command-line arguments.

### 4.2 Variable and Constant Declarations

```c
long int numSec = 0;

const int SEC_PER_MIN = 60;
const int SEC_PER_HOUR = 3600;
const int SEC_PER_DAY = 86400;
```

The program begins by declaring the variable and initializing it to zero.

It then declares three constants:

- `SEC_PER_MIN` stores 60.
- `SEC_PER_HOUR` stores 3,600.
- `SEC_PER_DAY` stores 86,400.

These constants establish the conversion values used by the conditional statements and arithmetic expressions.

### 4.3 Collecting User Input

```c
printf("Enter the number of seconds: ");
scanf("%ld", &numSec);
```

The program prompts the user to enter a numerical amount of seconds.

The `scanf()` function reads the entered value and stores it in `numSec`.

The format specifier `%ld` indicates that the program expects a `long int` value.

The address-of operator (`&`) provides the memory address of `numSec`, allowing `scanf()` to store the input in that variable.

### 4.4 Validating the Input

```c
if (numSec > 0)
{
    // Processing and conversion statements
}
else
{
    printf("The number of seconds entered must be greater than 0.\n");
}
```

The program uses an `if/else` decision structure to determine whether the entered number of seconds is valid.

The condition:

```c
numSec > 0
```

Checks whether the entered value is greater than zero.

**If the condition is true:**

- The program proceeds to the conversion logic.
- The applicable time-unit conditions are evaluated.
- Conversion results are displayed when their conditions are satisfied.

**If the condition is false:**

- The program displays an error message.
- The conversion calculations are skipped.
- Execution continues to the program's termination statement.

This validation prevents zero and negative values from being processed.

### 4.5 Converting Seconds to Minutes

```c
if (numSec >= SEC_PER_MIN)
{
    printf("The number of seconds you entered, %ld, is %.2lf minutes.\n",
           numSec, (numSec * 1.0) / SEC_PER_MIN);
}
```

The first conversion condition checks whether the entered number of seconds is greater than or equal to 60.

The condition:

```c
numSec >= SEC_PER_MIN
```

Determines whether the input contains enough seconds to represent at least one full minute.

If the condition evaluates to true, the program divides the entered seconds by 60.

The calculation is:

\[
\text{Minutes} = \frac{\text{Seconds}}{60}
\]

The expression:

```c
(numSec * 1.0) / SEC_PER_MIN
```

Multiplies the integer input by `1.0` before performing the division.

Because `1.0` is a floating-point value, the expression uses floating-point arithmetic rather than integer division.

The result is displayed using `%.2lf`, which formats the conversion to two decimal places.

### 4.6 Converting Seconds to Hours

```c
if (numSec >= SEC_PER_HOUR)
{
    printf("The number of seconds you entered, %ld, is %.2lf hours.\n",
           numSec, (numSec * 1.0) / SEC_PER_HOUR);
}
```

The second conversion condition checks whether the input contains at least 3,600 seconds.

The condition:

```c
numSec >= SEC_PER_HOUR
```

Determines whether the program should display the hours conversion.

If true, the program divides the entered number of seconds by 3,600.

The calculation is:

\[
\text{Hours} = \frac{\text{Seconds}}{3600}
\]

The result is displayed with two decimal places.

This is an independent `if` statement, not an `else if` statement. Therefore, the program can display both minutes and hours when the entered value meets both conditions.

### 4.7 Converting Seconds to Days

```c
if (numSec >= SEC_PER_DAY)
{
    printf("The number of seconds you entered, %ld, is %.2lf days.\n",
           numSec, (numSec * 1.0) / SEC_PER_DAY);
}
```

The third conversion condition checks whether the entered number of seconds is greater than or equal to 86,400.

The condition:

```c
numSec >= SEC_PER_DAY
```

Determines whether the program should display the days conversion.

If true, the program divides the entered number of seconds by 86,400.

The calculation is:

\[
\text{Days} = \frac{\text{Seconds}}{86400}
\]

The result is displayed with two decimal places.

Like the previous conversion statements, this is an independent `if` statement. The program can therefore display minutes, hours, and days together when the input meets all three thresholds.

### 4.8 Understanding Independent Conditional Statements

One of the important characteristics of this program is that the three conversion conditions are evaluated independently.

```c
if (numSec >= SEC_PER_MIN)
{
    // Display minutes
}

if (numSec >= SEC_PER_HOUR)
{
    // Display hours
}

if (numSec >= SEC_PER_DAY)
{
    // Display days
}
```

The program does not use `else if` between these conditions.

This allows multiple conversion statements to execute during the same program run.

For example, if the user enters `172800` seconds:

- The minutes condition is true.
- The hours condition is true.
- The days condition is true.

All three conversions are displayed.

### 4.9 Error Handling

```c
else
{
    printf("The number of seconds entered must be greater than 0.\n");
    printf("\n");
}
```

The `else` statement is associated with the primary validation condition:

```c
if (numSec > 0)
```

If the user enters zero or a negative number, the program displays an error message explaining that the input must be greater than zero.

The program does not perform any conversion calculations when this condition is false.

### 4.10 Program Termination

```c
return 0;
```

After the processing or error-handling section completes, the program returns `0` from `main()`.

This indicates normal program termination.

## 5. Operators Used

The program uses relational, arithmetic, assignment, and address-of operators.

### 5.1 Relational Operators

| Operator | Name | Purpose |
|---|---|---|
| `>` | Greater than | Determines whether the entered number of seconds is greater than zero. |
| `>=` | Greater than or equal to | Determines whether the input meets the minimum conversion threshold for minutes, hours, or days. |

### 5.2 Arithmetic Operators

| Operator | Name | Purpose |
|---|---|---|
| `*` | Multiplication | Multiplies the input by `1.0` to ensure floating-point arithmetic. |
| `/` | Division | Divides the number of seconds by the appropriate conversion constant. |

### 5.3 Assignment Operator

| Operator | Name | Purpose |
|---|---|---|
| `=` | Assignment | Initializes the `numSec` variable and assigns values to the constant declarations. |

### 5.4 Address-of Operator

| Operator | Name | Purpose |
|---|---|---|
| `&` | Address-of | Supplies the memory address of `numSec` to `scanf()`. |

## 6. Program Execution Sequence

The program follows a sequential input-validation-processing-output structure.

| Step | Operation | Description |
|---:|---|---|
| 1 | Program Start | Execution begins in `main()`. |
| 2 | Variable Declaration | Declares `numSec` as a `long int` and initializes it to zero. |
| 3 | Constant Declaration | Defines the seconds-per-minute, seconds-per-hour, and seconds-per-day values. |
| 4 | Input Prompt | Requests that the user enter a number of seconds. |
| 5 | Input Collection | Reads the input using `scanf()` and stores it in `numSec`. |
| 6 | Input Validation | Checks whether `numSec` is greater than zero. |
| 7 | Error Handling | If the input is zero or negative, displays an error message and skips conversion processing. |
| 8 | Minute Threshold Check | Determines whether the input is at least 60 seconds. |
| 9 | Minute Conversion | Divides the input by 60 and displays the result if the condition is true. |
| 10 | Hour Threshold Check | Determines whether the input is at least 3,600 seconds. |
| 11 | Hour Conversion | Divides the input by 3,600 and displays the result if the condition is true. |
| 12 | Day Threshold Check | Determines whether the input is at least 86,400 seconds. |
| 13 | Day Conversion | Divides the input by 86,400 and displays the result if the condition is true. |
| 14 | Program Termination | Returns `0` and ends execution. |

## 7. Text-Based Program Flowchart

```text
              +--------------------------+
              |       PROGRAM START      |
              +--------------------------+
                           |
                           v
              +--------------------------+
              |         main(void)       |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Declare numSec = 0       |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Declare constants:       |
              | SEC_PER_MIN = 60         |
              | SEC_PER_HOUR = 3600      |
              | SEC_PER_DAY = 86400      |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Prompt for seconds       |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Read numSec using scanf  |
              +--------------------------+
                           |
                           v
                    +---------------+
                    |  numSec > 0?  |
                    +---------------+
                       |         |
                      YES        NO
                       |         |
                       v         v
             +----------------+  +--------------------------+
             | Check minute   |  | Display error message    |
             | threshold      |  | Must be greater than 0   |
             +----------------+  +--------------------------+
                       |                    |
                       v                    |
              +-------------------+         |
              | numSec >= 60?     |         |
              +-------------------+         |
                 |           |              |
                YES          NO             |
                 |           |              |
                 v           |              |
        +------------------+ |              |
        | Calculate        | |              |
        | numSec / 60      | |              |
        +------------------+ |              |
                 |           |              |
                 v           |              |
        +------------------+ |              |
        | Display minutes  | |              |
        +------------------+ |              |
                 |           |              |
                 +-----+-----+              |
                       |                    |
                       v                    |
              +-------------------+         |
              | numSec >= 3600?   |         |
              +-------------------+         |
                 |           |              |
                YES          NO             |
                 |           |              |
                 v           |              |
        +------------------+ |              |
        | Calculate        | |              |
        | numSec / 3600    | |              |
        +------------------+ |              |
                 |           |              |
                 v           |              |
        +------------------+ |              |
        | Display hours    | |              |
        +------------------+ |              |
                 |           |              |
                 +-----+-----+              |
                       |                    |
                       v                    |
              +-------------------+         |
              | numSec >= 86400?  |         |
              +-------------------+         |
                 |           |              |
                YES          NO             |
                 |           |              |
                 v           |              |
        +------------------+ |              |
        | Calculate        | |              |
        | numSec / 86400   | |              |
        +------------------+ |              |
                 |           |              |
                 v           |              |
        +------------------+ |              |
        | Display days     | |              |
        +------------------+ |              |
                 |           |              |
                 +-----+-----+              |
                       |                    |
                       +---------+----------+
                                 |
                                 v
                       +------------------+
                       |     return 0;    |
                       +------------------+
                                 |
                                 v
                       +------------------+
                       |    PROGRAM END   |
                       +------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Variable Declaration and Initialization

The program declares a `long int` variable to store the user's input and initializes it to zero.

This establishes the storage location and initial value before the program reads the user's input.

### 8.2 Constants

The program uses three named constants to represent the number of seconds in a minute, hour, and day.

The `const` keyword prevents these values from being modified during execution.

### 8.3 Input and Output Operations

The program uses `printf()` to display prompts and conversion results.

It uses `scanf()` to accept the user's input and store it in the `numSec` variable.

### 8.4 Conditional Statements

The program uses `if/else` to validate the user's input and determine whether conversion processing should occur.

It also uses three independent `if` statements to evaluate the individual conversion thresholds.

### 8.5 Relational Operators

The program uses `>` and `>=` to compare the entered number of seconds against zero and the conversion thresholds.

These comparisons produce true or false results that control which statements execute.

### 8.6 Arithmetic Operations

The program uses multiplication and division to perform floating-point calculations.

Each conversion divides the original number of seconds by the appropriate constant.

### 8.7 Floating-Point Arithmetic

The expression:

```c
(numSec * 1.0) / SEC_PER_MIN
```

Converts the arithmetic operation into floating-point calculations by multiplying the integer value by `1.0`.

This prevents integer division from discarding fractional portions of the conversion result.

### 8.8 Multiple Independent Conditions

The three conversion statements are independent rather than connected through an `else if` structure.

This allows the program to display multiple applicable conversions during one execution.

### 8.9 Formatted Output

The program uses format specifiers to display the original seconds as a `long int` and the converted values as floating-point numbers.

The `%.2lf` format displays two digits after the decimal point.

### 8.10 Error Handling

The program uses an `else` statement to handle zero and negative input values.

Instead of performing invalid conversions, it displays an error message and proceeds toward normal program termination.

## 9. Program Characteristics and Limitations

| Characteristic | Description |
|---|---|
| Input Method | Console input using `scanf()`. |
| Input Data Type | `long int`. |
| Minimum Valid Input | Greater than zero. |
| Seconds per Minute | 60. |
| Seconds per Hour | 3,600. |
| Seconds per Day | 86,400. |
| Conversion Types | Minutes, hours, and days. |
| Validation Method | `if/else` decision structure. |
| Conversion Selection | Three independent `if` statements. |
| Arithmetic Method | Floating-point division. |
| Output Precision | Two decimal places. |
| Program Structure | All operations are contained in `main()`. |
| Program Termination | Returns `0` from `main()`. |

### 9.1 Conversion Thresholds

The program only displays a conversion when the entered number of seconds meets or exceeds the corresponding threshold.

| Input Range | Minutes Displayed | Hours Displayed | Days Displayed |
|---|---|---|---|
| 1–59 | No | No | No |
| 60–3,599 | Yes | No | No |
| 3,600–86,399 | Yes | Yes | No |
| 86,400 and greater | Yes | Yes | Yes |

The program does not display a conversion for a unit when the input is below that unit's threshold.

### 9.2 Original Input Used for Each Conversion

Each conversion is calculated independently from the original `numSec` value.

The program does not first convert seconds into minutes and then convert minutes into hours or days.

Instead, each calculation uses the appropriate seconds-per-unit constant.

### 9.3 No Input Validation for Nonnumeric Data

The program checks whether the numerical value is greater than zero.

However, it does not check the return value of `scanf()` to determine whether the user successfully entered a valid `long int`.

Nonnumeric input is not handled through a dedicated error-recovery mechanism.

### 9.4 No Conversion Output Below Thresholds

If the user enters a positive value below 60 seconds, the program does not display a minutes, hours, or days conversion.

It simply completes execution without displaying a conversion result.

### 9.5 Fixed Conversion Units

The program only supports conversions from seconds to minutes, hours, and days.

It does not calculate weeks, months, or years.

### 9.6 No Loops or User-Defined Functions

The program performs all operations within `main()`.

It does not use loops, arrays, or separate user-defined functions. The conversion logic is implemented through conditional statements and arithmetic expressions.

## 10. Overall Summary

The **Minutes, Hours, Days** program demonstrates fundamental C programming decision-making concepts by accepting a numerical amount of seconds and determining which time-unit conversions are applicable.

The program begins by declaring a `long int` variable for the user's input and three constant integer values representing the number of seconds in a minute, hour, and day.

After collecting the input, the program uses an `if/else` statement to verify that the entered number of seconds is greater than zero. Valid input proceeds through three independent conditional statements that check whether the value meets the required thresholds for minutes, hours, and days.

Each applicable conversion uses floating-point division to calculate the result and displays the converted value to two decimal places.

The primary programming concepts demonstrated include variable declarations, constants, data types, console input and output, conditional statements, relational operators, arithmetic operations, floating-point calculations, and formatted output.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, including variable declarations, constants, input/output operations, decision-making structures, relational operators, arithmetic calculations, and formatted output.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.