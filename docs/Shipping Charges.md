# Shipping Charges – C Program Documentation

| **Program Information** | **Details** |
|---|---|
| Program Name | Shipping Charges |
| Programmer | Brian Lorick |
| Programming Language | C |
| Development Environment | Microsoft Visual Studio |
| Course Topic | Chapter 3 – Decisions |
| Original Date | February 13, 2024 |
| Source File | `Shipping Charges.c` |

---

## 1. Program Overview

**Shipping Charges** is a C program that calculates the shipping cost of a package based on its weight in pounds.

The program prompts the user to enter a package weight, validates that the entered weight is greater than zero, and uses a series of conditional statements to determine the appropriate shipping charge.

Four shipping rates are supported:

| Package Weight | Shipping Charge |
|---|---:|
| Up to and including 2 pounds | $1.25 |
| Over 2 pounds through 6 pounds | $2.50 |
| Over 6 pounds through 10 pounds | $3.90 |
| Over 10 pounds | $4.40 |

After determining the appropriate rate, the program displays the shipping charge formatted to two decimal places.

If the package weight is zero or negative, the program displays an error message and terminates without calculating a shipping charge.

The program demonstrates fundamental C programming concepts, including variable declarations, constants, user input, input validation, relational operators, conditional statements, arithmetic comparisons, and formatted output.

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

The `stdio.h` header file provides the standard input/output functionality used by the program.

| Function | Purpose |
|---|---|
| `printf()` | Displays input prompts, error messages, and the calculated shipping charge. |
| `scanf()` | Accepts the package weight entered by the user. |

No additional libraries are required because the program does not perform advanced mathematical operations, manipulate files, or use external data structures.

## 3. Variables and Data Structures

The program uses constant values to establish shipping weight thresholds and their corresponding charges. It also uses two floating-point variables to store the user's input and calculated result.

### 3.1 Constant Declarations

```c
const double WEIGHT_2LB = 2.0;
const double WEIGHT_6LB = 6.0;
const double WEIGHT_10LB = 10.0;

const double WEIGHT_MIN = 0.0;

const double CHARGE_2LB = 1.25;
const double CHARGE_6LB = 2.50;
const double CHARGE_10LB = 3.90;

const double CHARGE_OVER_10LB = 4.40;
```

The `const` keyword identifies values that cannot be modified after initialization.

| Constant | Data Type | Value | Purpose |
|---|---|---:|---|
| `WEIGHT_2LB` | `double` | 2.0 | Establishes the first weight threshold. |
| `WEIGHT_6LB` | `double` | 6.0 | Establishes the second weight threshold. |
| `WEIGHT_10LB` | `double` | 10.0 | Establishes the third weight threshold. |
| `WEIGHT_MIN` | `double` | 0.0 | Establishes the minimum permitted package weight. |
| `CHARGE_2LB` | `double` | 1.25 | Shipping charge for packages weighing up to 2 pounds. |
| `CHARGE_6LB` | `double` | 2.50 | Shipping charge for packages over 2 and up to 6 pounds. |
| `CHARGE_10LB` | `double` | 3.90 | Shipping charge for packages over 6 and up to 10 pounds. |
| `CHARGE_OVER_10LB` | `double` | 4.40 | Shipping charge for packages exceeding 10 pounds. |

Using named constants makes the program easier to read, maintain, and modify. Shipping rates and weight thresholds can be changed without rewriting the conditional logic.

### 3.2 Variable Declarations

```c
double shippingCharge = 0.0;
double packageWeight = 0.0;
```

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `shippingCharge` | `double` | `0.0` | Stores the shipping charge selected by the conditional statements. |
| `packageWeight` | `double` | `0.0` | Stores the package weight entered by the user. |

### 3.3 Data Types

The program uses the `double` data type for all numerical values.

This allows the program to accept fractional package weights and represent shipping charges with decimal precision.

For example, a package weighing `4.75` pounds can be evaluated against the shipping thresholds without converting the weight to an integer.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
```

The `main()` function is the entry point of the program.

It contains the constant declarations, variable declarations, input operations, validation logic, shipping-rate selection, output statements, and return statements.

The program follows three primary processing stages:

1. Input
2. Processing
3. Output

### 4.2 Input – Accepting Package Weight

```c
printf("Enter the weight of the package: ");
scanf("%lf", &packageWeight);
```

The program begins by prompting the user to enter the package weight.

The `printf()` function displays the prompt, while `scanf()` accepts the numerical input and stores it in `packageWeight`.

**Input format specifier: `%lf`**

The `%lf` conversion specifier instructs `scanf()` to read a `double` value.

The address-of operator (`&`) is used to provide the memory address of `packageWeight` so that `scanf()` can store the entered value directly in that variable.

### 4.3 Input Validation – If Statement

```c
if (packageWeight <= WEIGHT_MIN)
{
    printf("The weight of the package must be greater than 0.00.\n");
    printf("\n");
    return 1;
}
```

Before calculating the shipping charge, the program validates the package weight.

The condition:

```c
packageWeight <= WEIGHT_MIN
```

compares the entered weight against the minimum permitted value of zero.

If the condition evaluates to true, the program:

1. Displays an error message.
2. Prints a blank line.
3. Executes `return 1`.
4. Terminates the program.

The program therefore rejects both zero and negative package weights.

If the entered weight is greater than zero, the condition evaluates to false and execution continues to the shipping-rate calculations.

### 4.4 Processing – Selecting the Shipping Charge

The program uses an `if`, `else if`, and `else` decision structure to select the correct shipping charge.

```c
if (packageWeight <= WEIGHT_2LB)
{
    shippingCharge = CHARGE_2LB;
}

else if (packageWeight <= WEIGHT_6LB)
{
    shippingCharge = CHARGE_6LB;
}

else if (packageWeight <= WEIGHT_10LB)
{
    shippingCharge = CHARGE_10LB;
}

else
{
    shippingCharge = CHARGE_OVER_10LB;
}
```

Each condition evaluates the package weight against a predefined threshold.

Because the conditions are evaluated sequentially, the program does not need to explicitly check the lower boundary of each subsequent range.

#### First Condition – Packages Up to 2 Pounds

```c
if (packageWeight <= WEIGHT_2LB)
{
    shippingCharge = CHARGE_2LB;
}
```

The first condition checks whether the package weighs 2 pounds or less.

If true, the shipping charge is assigned a value of `$1.25`.

Examples:

- 0.5 pounds
- 1.0 pound
- 1.75 pounds
- 2.0 pounds

#### Second Condition – Packages Over 2 Through 6 Pounds

```c
else if (packageWeight <= WEIGHT_6LB)
{
    shippingCharge = CHARGE_6LB;
}
```

This condition is evaluated only when the first condition is false.

Therefore, the package must weigh more than 2 pounds.

The program then checks whether the weight is 6 pounds or less.

If true, the shipping charge is assigned a value of `$2.50`.

Examples:

- 2.01 pounds
- 3.5 pounds
- 5.75 pounds
- 6.0 pounds

#### Third Condition – Packages Over 6 Through 10 Pounds

```c
else if (packageWeight <= WEIGHT_10LB)
{
    shippingCharge = CHARGE_10LB;
}
```

This condition is evaluated only when the previous two conditions are false.

The package must therefore weigh more than 6 pounds.

The program checks whether the weight is 10 pounds or less.

If true, the shipping charge is assigned a value of `$3.90`.

Examples:

- 6.01 pounds
- 7.5 pounds
- 9.25 pounds
- 10.0 pounds

#### Final Condition – Packages Over 10 Pounds

```c
else
{
    shippingCharge = CHARGE_OVER_10LB;
}
```

The `else` statement executes when none of the previous conditions are true.

At this point, the package weight must exceed 10 pounds.

The program assigns the shipping charge of `$4.40`.

Examples:

- 10.01 pounds
- 12.5 pounds
- 20.0 pounds

### 4.5 Output – Displaying Shipping Charge

```c
printf("\n");

printf("The shipping charge is $%.2f.\n", shippingCharge);

printf("\n");
```

After selecting the appropriate rate, the program displays the calculated shipping charge.

The format specifier:

```c
%.2f
```

instructs `printf()` to display the floating-point value with exactly two digits after the decimal point.

This formatting is appropriate for displaying monetary amounts.

### 4.6 Program Termination

```c
return 0;
```

If the program completes the shipping calculation successfully, it executes `return 0`.

This terminates the `main()` function and indicates successful program execution.

The program also contains:

```c
return 1;
```

inside the validation statement. This indicates that the program terminated early because the package weight was invalid.

The return values distinguish between successful completion and termination caused by invalid input.

## 5. Operators Used

The program uses assignment, relational, and address-of operators.

| Operator | Category | Example | Purpose |
|---|---|---|---|
| `=` | Assignment | `shippingCharge = CHARGE_2LB;` | Assigns the selected shipping rate. |
| `<=` | Relational | `packageWeight <= WEIGHT_2LB` | Checks whether a package weight is within a threshold. |
| `&` | Address-of | `&packageWeight` | Provides the memory address required by `scanf()`. |

### 5.1 Assignment Operator

The assignment operator (`=`) stores a value in a variable.

For example:

```c
shippingCharge = CHARGE_6LB;
```

This assigns the value stored in `CHARGE_6LB` to `shippingCharge`.

### 5.2 Less-Than-or-Equal Operator

The relational operator (`<=`) compares two values.

It evaluates to true when the left operand is less than or equal to the right operand.

For example:

```c
packageWeight <= WEIGHT_6LB
```

checks whether the package weight is 6 pounds or less.

The result of the comparison determines which conditional branch executes.

### 5.3 Address-of Operator

The address-of operator (`&`) retrieves the memory address of a variable.

```c
scanf("%lf", &packageWeight);
```

This allows `scanf()` to store the entered value in the correct memory location.

## 6. Program Execution Sequence

The program follows this execution sequence:

1. The program enters the `main()` function.
2. Shipping weight thresholds are declared as constants.
3. Shipping charges are declared as constants.
4. `shippingCharge` and `packageWeight` are declared and initialized.
5. The program prompts the user to enter the package weight.
6. The entered value is stored in `packageWeight`.
7. The validation statement checks whether the weight is less than or equal to zero.
8. If invalid, an error message is displayed and the program terminates with `return 1`.
9. If valid, execution continues to the shipping-rate decision structure.
10. The first condition checks whether the weight is 2 pounds or less.
11. If false, the second condition checks whether the weight is 6 pounds or less.
12. If false, the third condition checks whether the weight is 10 pounds or less.
13. If all three conditions are false, the `else` branch assigns the over-10-pound shipping charge.
14. The selected shipping charge is stored in `shippingCharge`.
15. The program displays the shipping charge formatted to two decimal places.
16. The program returns zero and terminates successfully.

## 7. Text-Based Program Flowchart

### 7.1 Main Program Flow

```text
              +-------------------------+
              |          START          |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Declare Constants       |
              | and Variables           |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Prompt for Package      |
              | Weight                  |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | Read packageWeight      |
              +------------+------------+
                           |
                           v
              +-------------------------+
              | packageWeight <= 0?     |
              +------------+------------+
                           |
                    +------+------+
                    |             |
                   YES            NO
                    |             |
                    v             v
          +----------------+  +----------------------+
          | Display Error  |  | Determine Shipping   |
          | Message        |  | Charge               |
          +--------+-------+  +----------+-----------+
                   |                     |
                   v                     v
          +----------------+   +---------------------+
          |   return 1     |   | Display Shipping    |
          +--------+-------+   | Charge               |
                   |           +----------+----------+
                   |                      |
                   |                      v
                   |           +---------------------+
                   |           |     return 0        |
                   |           +----------+----------+
                   |                      |
                   v                      v
          +----------------+   +---------------------+
          |      END       |   |        END          |
          +----------------+   +---------------------+
```

### 7.2 Shipping Rate Decision Logic

```text
             +-------------------------+
             | Begin Shipping Process  |
             +------------+------------+
                          |
                          v
             +-------------------------+
             | packageWeight <= 2.0?   |
             +------------+------------+
                          |
                   +------+------+
                   |             |
                  YES            NO
                   |             |
                   v             v
          +----------------+  +-------------------------+
          | Charge = $1.25 |  | packageWeight <= 6.0?   |
          +--------+-------+  +------------+------------+
                   |                       |
                   |                +------+------+
                   |                |             |
                   |               YES            NO
                   |                |             |
                   |                v             v
                   |       +----------------+  +-------------------------+
                   |       | Charge = $2.50 |  | packageWeight <= 10.0?  |
                   |       +--------+-------+  +------------+------------+
                   |                |                       |
                   |                |                +------+------+
                   |                |                |             |
                   |                |               YES            NO
                   |                |                |             |
                   |                |                v             v
                   |                |       +----------------+  +----------------+
                   |                |       | Charge = $3.90 |  | Charge = $4.40 |
                   |                |       +--------+-------+  +--------+-------+
                   |                |                |                  |
                   +----------------+----------------+------------------+
                                                    |
                                                    v
                                         +-------------------------+
                                         | Display Shipping Charge |
                                         +------------+------------+
                                                      |
                                                      v
                                         +-------------------------+
                                         |          END            |
                                         +-------------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Decision-Making Structures

The program demonstrates how conditional statements control program execution based on user input.

The `if`, `else if`, and `else` statements create a decision structure that selects one shipping rate from four possible outcomes.

### 8.2 Sequential Conditional Evaluation

The shipping-rate conditions are evaluated from top to bottom.

Once a condition evaluates to true, its corresponding block executes and the remaining branches are skipped.

This ensures that only one shipping charge is assigned.

### 8.3 Input Validation

The program validates the package weight before performing the shipping calculation.

This prevents zero and negative values from being accepted as valid package weights.

### 8.4 Constants

The `const` keyword is used to establish fixed weight thresholds and shipping charges.

This improves maintainability by separating business rules from the decision-making logic.

### 8.5 Floating-Point Data

The `double` data type allows the program to process fractional package weights and decimal shipping charges.

### 8.6 Relational Comparisons

The program uses relational comparisons to determine which shipping category applies to the entered weight.

### 8.7 Formatted Input and Output

The program demonstrates how `scanf()` and `printf()` interact with floating-point values.

| Format / Escape Sequence | Purpose |
|---|---|
| `%lf` | Reads a `double` value using `scanf()`. |
| `%.2f` | Displays a floating-point value to two decimal places. |
| `\n` | Moves output to a new line. |
| `&` | Supplies the memory address required by `scanf()`. |

### 8.8 Return Status

The program demonstrates how the return value from `main()` communicates the program's termination status.

- `return 0` indicates successful completion.
- `return 1` indicates termination caused by invalid package weight.

## 9. Program Characteristics and Limitations

### 9.1 Weight Boundaries

The conditional statements establish specific weight ranges.

The exact boundary values are important because each range includes or excludes its endpoints.

| Package Weight | Selected Constant | Charge |
|---:|---|---:|
| 0.00 pounds | Invalid | Error |
| 0.01 pounds | `CHARGE_2LB` | $1.25 |
| 2.00 pounds | `CHARGE_2LB` | $1.25 |
| 2.01 pounds | `CHARGE_6LB` | $2.50 |
| 6.00 pounds | `CHARGE_6LB` | $2.50 |
| 6.01 pounds | `CHARGE_10LB` | $3.90 |
| 10.00 pounds | `CHARGE_10LB` | $3.90 |
| 10.01 pounds | `CHARGE_OVER_10LB` | $4.40 |

### 9.2 Invalid Weight Handling

The program rejects package weights that are less than or equal to zero.

It does not attempt to calculate a shipping charge when the validation condition is true.

### 9.3 No Maximum Weight Restriction

The program does not establish a maximum package weight.

Every valid weight greater than 10 pounds receives the same `$4.40` shipping charge.

### 9.4 No Input Error Checking

The program uses:

```c
scanf("%lf", &packageWeight);
```

It does not check the return value of `scanf()`.

Consequently, it assumes the user enters a valid numerical value. Nonnumeric input is not handled explicitly.

### 9.5 Single Package Processing

The program processes one package per execution.

It does not include a loop for processing multiple packages or calculating combined shipping costs.

### 9.6 Shipping Rate Assignment

The program assigns the appropriate rate directly to `shippingCharge` using the named constants.

It does not calculate shipping costs proportionally based on weight. Instead, it uses fixed charges determined by the applicable weight category.

### 9.7 Monetary Formatting

The shipping charge is displayed using two decimal places.

This ensures that the output consistently represents monetary values, including amounts such as `$1.25`, `$2.50`, `$3.90`, and `$4.40`.

## 10. Overall Summary

Shipping Charges demonstrates how decision-making structures can be used to implement a basic rate-selection system in the C programming language.

The program accepts a package weight, validates that the value is greater than zero, and evaluates the weight against three predefined thresholds. Based on the result, it assigns one of four fixed shipping charges.

The source code demonstrates constants, floating-point variables, standard input/output functions, input validation, relational operators, `if-else if-else` statements, sequential decision evaluation, and program termination status codes.

Overall, the program provides a practical example of how conditional logic can be used to implement business rules and make decisions based on numerical input.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational, instructional, and programming-reference purposes. It is intended to demonstrate C programming concepts, including constants, variables, floating-point data, formatted input/output, input validation, relational operators, conditional statements, decision-making structures, and program termination status codes.

This source code is not intended to be submitted as another student's original work, used to circumvent coursework requirements, or used for plagiarism or academic dishonesty.

Students should maintain academic integrity by understanding the source code, independently completing assigned coursework, and following their institution's academic policies.

The author is not responsible for unauthorized use, academic misconduct, plagiarism, cheating, or any other misuse of this program or its contents.