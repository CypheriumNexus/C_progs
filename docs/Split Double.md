# Split Double – C Program Documentation

| **Program Information** | **Details** |
|---|---|
| Program Name | Split Double |
| Programmer(s) | Brian Lorick & Roger Harper |
| Programming Language | C |
| Development Environment | Microsoft Visual Studio |
| Course Topic | Chapter 2 – Fundamentals |
| Original Date | January 29, 2024 |
| Source File | `Split Double.c` |

---

## 1. Program Overview

**Split Double** is a C program that accepts a decimal number from the user and separates it into two components:

- **Integer portion:** The whole-number portion to the left of the decimal point.
- **Decimal portion:** The remaining fractional portion to the right of the decimal point.

The program uses typecasting to convert the user's floating-point input into an integer. It then subtracts that integer from the original number to isolate the fractional portion.

For example, if the user enters `45.75`, the program produces:

- Integer portion: `45`
- Decimal portion: `0.75`

The program demonstrates fundamental C programming concepts, including variable declarations, floating-point data types, user input, typecasting, arithmetic operations, formatted output, and sequential execution.

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

The `stdio.h` header file provides the standard input/output functionality required by the program.

| Function | Purpose |
|---|---|
| `printf()` | Displays prompts and the calculated integer and decimal portions. |
| `scanf()` | Accepts the decimal number entered by the user. |

No additional libraries are required because the program performs only basic input, arithmetic processing, and output operations.

## 3. Variables and Data Structures

The program declares three variables inside the `main()` function.

### 3.1 Variable Declarations

```c
double userNumber = 0.0;
int userInteger = 0;
double userDecimal = 0.0;
```

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `userNumber` | `double` | `0.0` | Stores the original decimal number entered by the user. |
| `userInteger` | `int` | `0` | Stores the integer portion obtained by typecasting the original number. |
| `userDecimal` | `double` | `0.0` | Stores the remaining fractional portion after subtracting the integer portion. |

### 3.2 Data Types

The program uses two numerical data types:

- **`double`** – Stores floating-point numbers with decimal precision.
- **`int`** – Stores whole-number values without a fractional component.

The `double` data type is necessary for preserving the original decimal input and calculating the remaining fractional portion.

The `int` data type is used to store the result of converting the original number into an integer.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
```

The `main()` function is the entry point of the program.

It contains the variable declarations, input operation, mathematical processing, output statements, and final return statement.

The source code is organized into three processing sections:

1. Input
2. Processing
3. Output

### 4.2 Input – Accepting a Decimal Number

```c
printf("Enter a number that includes a decimal point: ");
scanf("%lf", &userNumber);
```

The program begins by prompting the user to enter a number containing a decimal point.

The `printf()` function displays the prompt, while `scanf()` accepts the numerical input and stores it in `userNumber`.

**Input format specifier: `%lf`**

The `%lf` conversion specifier instructs `scanf()` to read a `double` value.

The address-of operator (`&`) provides the memory address of `userNumber`, allowing `scanf()` to store the entered value directly in that variable.

### 4.3 Processing – Typecasting the Original Number

```c
userInteger = (int)userNumber;
```

This statement converts the floating-point value stored in `userNumber` into an integer.

The expression:

```c
(int)userNumber
```

uses an explicit typecast to convert the original `double` value into an `int`.

When a floating-point value is converted to an integer in C, the fractional portion is discarded. The value is truncated toward zero rather than rounded to the nearest integer.

**Example:**

If the user enters:

```text
45.75
```

The conversion produces:

```text
45
```

The result is then assigned to `userInteger`.

### 4.4 Processing – Isolating the Decimal Portion

```c
userDecimal = userNumber - userInteger;
```

This statement subtracts the integer portion from the original floating-point number.

The remaining result represents the fractional portion of the original value.

**Formula:**

\[
\text{Decimal Portion}
=
\text{Original Number}
-
\text{Integer Portion}
\]

**Example:**

Given:

\[
\text{userNumber}=45.75
\]

\[
\text{userInteger}=45
\]

The calculation becomes:

\[
45.75-45=0.75
\]

The resulting value is stored in `userDecimal`.

### 4.5 Output – Displaying the Integer Portion

```c
printf("The integer part of %lf is %d." "\n",
       userNumber, userInteger);
```

This statement displays the original number and its integer portion.

The format specifiers identify how each variable should be displayed.

| Format Specifier | Purpose |
|---|---|
| `%lf` | Displays the original floating-point number. |
| `%d` | Displays the integer portion. |
| `\n` | Moves the output cursor to the next line. |

The first argument corresponds to `userNumber`, while the second corresponds to `userInteger`.

### 4.6 Output – Displaying the Decimal Portion

```c
printf("The decimal part of %lf is %lf.\n",
       userNumber, userDecimal);
```

This statement displays the original number and the calculated fractional portion.

Both values use the `%lf` format specifier in the source code.

The output displays the original floating-point value followed by the remaining decimal value.

### 4.7 Formatting the Output

```c
printf("\n");
```

This statement inserts an additional blank line after the results.

The newline escape sequence improves console readability by separating the program output from the command prompt.

### 4.8 Program Termination

```c
return 0;
```

The `return 0` statement terminates the `main()` function and indicates successful program execution.

## 5. Operators Used

The program uses assignment, arithmetic, typecasting, and address-of syntax.

| Operator / Syntax | Category | Example | Purpose |
|---|---|---|---|
| `=` | Assignment | `userInteger = (int)userNumber;` | Assigns a calculated value to a variable. |
| `-` | Arithmetic | `userNumber - userInteger` | Subtracts the integer portion from the original number. |
| `(int)` | Typecast | `(int)userNumber` | Explicitly converts a `double` value into an integer. |
| `&` | Address-of | `&userNumber` | Provides the memory address required by `scanf()`. |

### 5.1 Assignment Operator

The assignment operator (`=`) stores a value in a variable.

For example:

```c
userDecimal = userNumber - userInteger;
```

The subtraction is evaluated first, and the resulting value is assigned to `userDecimal`.

### 5.2 Subtraction Operator

The subtraction operator (`-`) performs arithmetic subtraction.

It is used to remove the integer portion from the original floating-point value.

### 5.3 Explicit Typecasting

The typecast:

```c
(int)userNumber
```

instructs the compiler to convert the value into an integer before assigning it to `userInteger`.

This conversion discards the fractional portion rather than rounding the value.

### 5.4 Address-of Operator

The address-of operator (`&`) retrieves the memory address of a variable.

```c
scanf("%lf", &userNumber);
```

This allows `scanf()` to write the user's input directly into the memory location associated with `userNumber`.

## 6. Program Execution Sequence

The program follows this execution sequence:

1. The program enters the `main()` function.
2. Three variables are declared and initialized.
3. The program prompts the user to enter a decimal number.
4. The entered value is stored in `userNumber`.
5. The program converts `userNumber` into an integer using `(int)userNumber`.
6. The converted value is stored in `userInteger`.
7. The program subtracts `userInteger` from `userNumber`.
8. The resulting fractional portion is stored in `userDecimal`.
9. The program displays the original number and integer portion.
10. The program displays the original number and decimal portion.
11. A blank line is printed.
12. The program returns zero and terminates.

## 7. Text-Based Program Flowchart

### 7.1 Main Program Flow

```text
              +-------------------------+
              |          START          |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Declare Variables       |
              | userNumber              |
              | userInteger             |
              | userDecimal             |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Prompt User for Decimal |
              | Number                  |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Read Input into         |
              | userNumber              |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Typecast userNumber     |
              | to int                  |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Store Result in         |
              | userInteger             |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Subtract Integer Part   |
              | from Original Number    |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Store Result in         |
              | userDecimal             |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Display Integer Portion |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Display Decimal Portion |
              +------------+------------+
                           |
                           v
              +-------------------------+
              |       return 0          |
              +------------+------------+
                           |
                           v
              +-------------------------+
              |           END           |
              +-------------------------+
```

### 7.2 Number-Splitting Logic

```text
       +----------------------------+
       | Receive Decimal Number     |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Convert to Integer         |
       | userInteger = (int)value   |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Subtract Integer Portion   |
       | userDecimal = value - int  |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Display Integer Portion    |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Display Decimal Portion    |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       |          END               |
       +----------------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Variable Declaration and Initialization

The program demonstrates how variables are declared using specific data types and initialized with starting values.

```c
double userNumber = 0.0;
```

This statement declares a floating-point variable and assigns it an initial value of zero.

### 8.2 Floating-Point Data Types

The `double` data type allows the program to store numerical values containing fractional components.

This is important because the original input must retain its decimal portion for the subtraction operation.

### 8.3 Integer Data Types

The `int` data type stores the whole-number result obtained through typecasting.

### 8.4 Explicit Typecasting

The program demonstrates explicit type conversion using:

```c
(int)userNumber
```

This instructs the compiler to convert a floating-point value into an integer.

The conversion truncates the fractional portion toward zero.

### 8.5 Arithmetic Processing

The program uses subtraction to isolate the fractional portion of the original number.

This demonstrates how a value can be decomposed into separate components using basic arithmetic operations.

### 8.6 Standard Input and Output

The program uses `scanf()` and `printf()` to interact with the user.

The input function accepts a floating-point value, while the output functions display the calculated results.

### 8.7 Sequential Execution

The program executes statements in the order they appear in the source code.

There are no loops, conditional statements, or decision structures.

### 8.8 Formatted Input and Output

The program demonstrates the following format specifiers and escape sequences:

| Format / Escape Sequence | Purpose |
|---|---|
| `%lf` | Reads a `double` with `scanf()` and displays a floating-point value with `printf()`. |
| `%d` | Displays an integer value. |
| `\n` | Moves output to a new line. |
| `&` | Supplies the memory address required by `scanf()`. |

## 9. Program Characteristics and Limitations

### 9.1 Truncation Rather Than Rounding

The program uses explicit typecasting to convert the original number into an integer.

This conversion truncates the fractional portion toward zero.

For example:

| Original Number | Integer Portion | Decimal Portion |
|---:|---:|---:|
| 45.75 | 45 | 0.75 |
| 18.25 | 18 | 0.25 |
| 9.99 | 9 | 0.99 |
| 7.50 | 7 | 0.50 |
| -12.75 | -12 | -0.75 |
| -8.25 | -8 | -0.25 |

Negative values are also truncated toward zero rather than rounded downward.

### 9.2 Floating-Point Precision

The program uses the `double` data type to represent decimal values.

However, floating-point numbers are stored using binary representations. Some decimal fractions cannot be represented exactly, so calculations may produce small precision differences.

For example, a decimal portion that mathematically equals `0.75` may be represented internally with a small approximation difference in certain calculations.

### 9.3 Output Precision

The source code uses `%lf` without specifying a decimal precision.

For `printf()`, this normally displays six digits after the decimal point.

Consequently, a value such as `45.75` may appear as:

```text
The integer part of 45.750000 is 45.
The decimal part of 45.750000 is 0.750000.
```

The program displays the original floating-point value and the calculated fractional portion using the default floating-point formatting precision.

### 9.4 Negative Number Handling

The program does not reject negative values.

Because C typecasting truncates toward zero, a negative input produces a negative integer portion and a negative fractional remainder.

For example:

\[
-12.75-(-12)=-0.75
\]

The program therefore separates negative values according to truncation toward zero, not mathematical floor.

### 9.5 Input Validation

The program uses:

```c
scanf("%lf", &userNumber);
```

It does not check the return value of `scanf()`.

Consequently, it assumes the user enters a valid numerical value. Nonnumeric input and input errors are not handled explicitly.

### 9.6 Large Number Limitations

The program converts the `double` value to an `int`.

If the original floating-point value is outside the representable range of the `int` data type, the conversion does not have a defined result under the C language rules.

The program does not include a range check before performing the conversion.

### 9.7 No Repetition or Conditional Processing

The program accepts only one numerical value per execution.

It does not include loops for processing multiple numbers or conditional statements for handling different input categories.

## 10. Overall Summary

Split Double demonstrates fundamental C programming concepts through a simple numerical processing application.

The program accepts a decimal number, converts it into an integer using explicit typecasting, and subtracts the integer portion from the original floating-point value to isolate the fractional portion.

The source code demonstrates variable declarations, integer and floating-point data types, standard input/output functions, typecasting, arithmetic subtraction, address-of operations, formatted output, and sequential program execution.

An important concept demonstrated by this program is that converting a floating-point value into an integer truncates the fractional portion toward zero rather than rounding the value.

Overall, the program provides a practical introduction to data types, type conversion, and basic arithmetic operations in the C programming language.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational, instructional, and programming-reference purposes. It is intended to demonstrate C programming concepts, including variable declarations, integer and floating-point data types, formatted input/output, explicit typecasting, arithmetic operations, and sequential program execution.

This source code is not intended to be submitted as another student's original work, used to circumvent coursework requirements, or used for plagiarism or academic dishonesty.

Students should maintain academic integrity by understanding the source code, independently completing assigned coursework, and following their institution's academic policies.

The author(s) are not responsible for unauthorized use, academic misconduct, plagiarism, cheating, or any other misuse of this program or its contents.