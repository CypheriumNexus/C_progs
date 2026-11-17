# Sales Commission – C Program Documentation

| **Program Information** | **Details** |
|---|---|
| Program Name | Sales Commission |
| Programmer | Brian Lorick |
| Programming Language | C |
| Development Environment | Microsoft Visual Studio |
| Course Topic | Chapter 4 – Repetition |
| Original Date | February 28, 2024 |
| Source File | `Sales Commission.c` |

---

## 1. Program Overview

**Sales Commission** is a C program that calculates a salesperson's weekly salary based on a fixed base salary and a commission earned from accumulated sales.

The program demonstrates two types of repetition structures:

- **Pre-test loop (`while`)** – Evaluates the loop condition before executing the loop body.
- **Post-test loop (`do-while`)** – Executes the loop body before evaluating the loop condition.

Both loops use sentinel-controlled input. The user enters sales amounts, and the program continues processing entries until a negative value is entered.

The program calculates and displays the salesperson's weekly salary after each accepted sales entry. Once the sentinel value terminates the loop, the program displays the total sales and average sales amount.

The program executes both loop implementations independently, resetting the appropriate variables before beginning the second demonstration.

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

The `stdio.h` header file provides the standard input/output functions used by the program.

| Function | Purpose |
|---|---|
| `printf()` | Displays prompts, salary calculations, totals, averages, and explanatory messages. |
| `scanf()` | Accepts sales amounts entered by the user. |

## 3. Variables and Data Structures

The program uses constant values, floating-point variables, and an integer counter to perform its calculations.

### 3.1 Constants

```c
const double BASE_SALARY = 200.00;
const double COMMISSION_RATE = 0.09;
const double SENTINEL_VALUE = 0.0;
```

These constants establish the fixed values used throughout the program.

| Constant | Data Type | Value | Purpose |
|---|---|---:|---|
| `BASE_SALARY` | `const double` | 200.00 | Establishes the fixed base salary. |
| `COMMISSION_RATE` | `const double` | 0.09 | Establishes the commission rate of 9%. |
| `SENTINEL_VALUE` | `const double` | 0.0 | Establishes the comparison boundary used to control loop execution. |

The `const` keyword prevents these values from being modified during program execution.

### 3.2 Variable Declarations

```c
double totalSales = 0.0;
double salesInput = 0.0;
double weeklySalary = 0.0;
int numCount = 0;
```

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `totalSales` | `double` | `0.0` | Accumulates accepted sales amounts. |
| `salesInput` | `double` | `0.0` | Stores each individual sales amount entered by the user. |
| `weeklySalary` | `double` | `0.0` | Stores the calculated weekly salary. |
| `numCount` | `int` | `0` | Counts the number of accepted sales entries. |

### 3.3 Data Types

The program uses two primary data types:

- **`double`** – Stores monetary values and calculations with decimal precision.
- **`int`** – Stores the number of accepted sales entries.

Using `double` allows the program to perform commission and salary calculations without restricting values to whole numbers.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
```

The `main()` function is the entry point of the program.

It contains all variable declarations, input operations, calculations, conditional statements, loop structures, and output operations.

The program demonstrates two separate methods of implementing sentinel-controlled repetition.

### 4.2 Pre-Test Loop – While Statement

```c
while (salesInput >= SENTINEL_VALUE)
{
    totalSales += salesInput;
    numCount++;

    weeklySalary = BASE_SALARY +
                   (totalSales * COMMISSION_RATE);

    printf("The person receives $%.2lf.\n\n", weeklySalary);

    printf("Enter the amount of sales (negative to quit): $");
    scanf("%lf", &salesInput);
}
```

A `while` loop is classified as a pre-test loop because its condition is evaluated before the loop body executes.

The program first prompts the user for an initial sales amount and stores it in `salesInput`.

The loop condition:

```c
salesInput >= SENTINEL_VALUE
```

determines whether the entered value should be processed.

Since `SENTINEL_VALUE` equals `0.0`, the loop continues when the entered sales amount is zero or positive.

**Execution sequence:**

1. The program prompts the user for an initial sales amount.
2. The input is stored in `salesInput`.
3. The `while` condition evaluates whether the value is greater than or equal to zero.
4. If the condition is true, the sales amount is added to `totalSales`.
5. The `numCount` counter is incremented.
6. The weekly salary is calculated.
7. The salary is displayed.
8. The program prompts for another sales amount.
9. The new input replaces the previous value in `salesInput`.
10. The condition is evaluated again.

When a negative amount is entered, the condition becomes false and the loop terminates.

**Important characteristic:** The initial input operation occurs before the loop. This means the `while` loop can terminate without executing its body if the first value entered is negative.

### 4.3 Accumulating Total Sales

```c
totalSales += salesInput;
```

The compound assignment operator adds the current sales amount to the accumulated total.

This is equivalent to:

```c
totalSales = totalSales + salesInput;
```

The variable `totalSales` retains the accumulated value between loop iterations.

### 4.4 Counting Sales Entries

```c
numCount++;
```

The increment operator increases `numCount` by one each time a valid sales entry is processed.

The counter is used later to calculate the average sales amount.

A negative sentinel value does not increment the counter because it is never processed inside the loop.

### 4.5 Calculating Weekly Salary

```c
weeklySalary = BASE_SALARY +
               (totalSales * COMMISSION_RATE);
```

This statement calculates the salesperson's weekly salary using the base salary and accumulated commission.

**Formula:**

\[
\text{Weekly Salary}
=
\text{Base Salary}
+
(\text{Total Sales}\times\text{Commission Rate})
\]

Using the program's constants:

\[
\text{Weekly Salary}
=
200.00+(\text{Total Sales}\times0.09)
\]

The calculation uses accumulated sales rather than only the most recent sales entry.

Therefore, the displayed salary increases as additional accepted sales amounts are entered.

### 4.6 Displaying Weekly Salary

```c
printf("The person receives $%.2lf.\n\n", weeklySalary);
```

This statement displays the calculated weekly salary.

The `%.2lf` format specifier displays the floating-point value to two decimal places, which is appropriate for presenting monetary amounts.

### 4.7 Displaying Total Sales

After the `while` loop terminates, the program displays the accumulated sales amount:

```c
printf("\nThe total of the sales was $%.2lf.\n", totalSales);
```

The value of `totalSales` represents the sum of all accepted sales entries during the pre-test loop.

### 4.8 Conditional Statement – Checking Sales Count

```c
if (numCount > 0)
    printf("The average sales was $%.2lf.\n\n",
           totalSales / numCount);

else
    printf("No sales were entered.\n\n");
```

This `if-else` statement checks whether any sales entries were processed.

**If `numCount > 0`:**

The program divides total sales by the number of accepted entries to calculate average sales.

**If `numCount` equals zero:**

The program displays a message indicating that no sales were entered.

This condition prevents division by zero.

**Average sales formula:**

\[
\text{Average Sales}
=
\frac{\text{Total Sales}}{\text{Number of Sales Entries}}
\]

### 4.9 Resetting Variables

```c
totalSales = 0.0;
numCount = 0;
```

Before executing the post-test loop, the program resets the accumulated sales and counter variables.

This ensures that the second loop begins with a clean set of values rather than continuing with the totals from the first loop.

The `salesInput` and `weeklySalary` variables are not explicitly reset at this point. However, the post-test loop obtains a new sales input before processing it, and the salary is recalculated for every accepted entry.

### 4.10 Post-Test Loop – Do-While Statement

```c
do
{
    printf("Enter the amount of sales (negative to quit): $");
    scanf("%lf", &salesInput);

    if (salesInput >= SENTINEL_VALUE)
    {
        totalSales += salesInput;
        numCount++;

        weeklySalary = BASE_SALARY +
                       (totalSales * COMMISSION_RATE);

        printf("The person receives $%.2lf.\n\n", weeklySalary);
    }
}
while (salesInput >= SENTINEL_VALUE);
```

A `do-while` loop is classified as a post-test loop because its condition is evaluated after the loop body executes.

Unlike the `while` loop, the `do-while` loop always executes its body at least once.

The program prompts for input at the beginning of the loop, then evaluates the entered amount using an `if` statement.

**Execution sequence:**

1. The loop begins.
2. The user is prompted to enter a sales amount.
3. The input is stored in `salesInput`.
4. The `if` statement checks whether the amount is greater than or equal to zero.
5. If true, the amount is added to `totalSales`.
6. The sales counter is incremented.
7. The weekly salary is calculated and displayed.
8. The loop condition is evaluated.
9. If the value is zero or positive, the loop repeats.
10. If the value is negative, the loop terminates.

The `if` statement is necessary because the `do-while` body executes before the loop condition is evaluated. Without the `if` statement, the negative sentinel value would also be processed as a sales entry.

### 4.11 Comparing Pre-Test and Post-Test Loops

| Characteristic | `while` Loop | `do-while` Loop |
|---|---|---|
| Loop Type | Pre-test | Post-test |
| Condition Evaluated | Before the loop body | After the loop body |
| Minimum Executions | Zero | One |
| Initial Input | Before the loop | Inside the loop |
| Input Repetition | At the bottom of the loop | At the top of the loop |
| Sentinel Handling | Loop condition prevents negative input from processing. | An `if` statement prevents negative input from processing. |
| Termination | Condition becomes false. | Condition becomes false. |

The program uses both structures to demonstrate how the same general task can be implemented using different repetition statements.

## 5. Operators Used

The program uses assignment, arithmetic, relational, and increment operators.

| Operator | Category | Example | Purpose |
|---|---|---|---|
| `=` | Assignment | `totalSales = 0.0;` | Assigns values to variables. |
| `+=` | Compound assignment | `totalSales += salesInput;` | Adds an amount to accumulated sales. |
| `*` | Arithmetic | `totalSales * COMMISSION_RATE` | Calculates commission. |
| `+` | Arithmetic | `BASE_SALARY + commission` | Adds commission to base salary. |
| `/` | Arithmetic | `totalSales / numCount` | Calculates average sales. |
| `>=` | Relational | `salesInput >= SENTINEL_VALUE` | Determines whether an amount should be processed or the loop should continue. |
| `>` | Relational | `numCount > 0` | Checks whether any sales were entered. |
| `++` | Increment | `numCount++` | Increases the sales counter. |

### 5.1 Assignment Operator

The assignment operator (`=`) stores a value in a variable.

For example:

```c
totalSales = 0.0;
```

This initializes or resets the accumulated sales value.

### 5.2 Compound Assignment Operator

The `+=` operator adds a value to an existing variable.

```c
totalSales += salesInput;
```

It is equivalent to:

```c
totalSales = totalSales + salesInput;
```

### 5.3 Arithmetic Operators

The program uses multiplication, addition, and division to calculate commission, salary, and average sales.

### 5.4 Relational Operators

The `>=` and `>` operators compare numerical values and produce Boolean results.

These comparisons control loop repetition and conditional execution.

### 5.5 Increment Operator

The `++` operator increases the sales counter by one.

It allows the program to track how many sales entries have been processed.

## 6. Program Execution Sequence

The program follows two separate processing cycles.

### 6.1 Pre-Test Processing Sequence

1. The program enters `main()`.
2. Constants and variables are declared and initialized.
3. The program displays the pre-test loop explanation.
4. The user is prompted for an initial sales amount.
5. The input is stored in `salesInput`.
6. The `while` condition checks whether the amount is greater than or equal to zero.
7. If valid, the sales amount is added to `totalSales`.
8. The `numCount` counter is incremented.
9. The weekly salary is calculated.
10. The calculated salary is displayed.
11. The program prompts for another sales amount.
12. The loop repeats until a negative value is entered.
13. The program displays total sales.
14. The `if-else` statement determines whether average sales can be calculated.
15. The average is displayed, or a no-sales message is displayed.

### 6.2 Post-Test Processing Sequence

1. The program resets `totalSales` and `numCount`.
2. The program displays the post-test loop explanation.
3. The `do` block begins executing.
4. The user is prompted for a sales amount.
5. The input is stored in `salesInput`.
6. The `if` statement checks whether the amount is greater than or equal to zero.
7. If valid, the amount is added to `totalSales`.
8. The sales counter is incremented.
9. The weekly salary is recalculated and displayed.
10. The `while` condition evaluates the entered amount.
11. The loop repeats until a negative value is entered.
12. The program displays total sales.
13. The `if-else` statement checks whether sales entries were processed.
14. The average is calculated and displayed, or the no-sales message is displayed.
15. The program returns zero and terminates.

## 7. Text-Based Program Flowcharts

### 7.1 Main Program Flow

```text
              +----------------------+
              |        START         |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | Declare Constants    |
              | and Variables        |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | Display While Loop   |
              | Explanation          |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | Prompt for Sales     |
              | and Read Input       |
              +----------+-----------+
                         |
                         v
              +----------------------+
              | salesInput >= 0?     |
              +----------+-----------+
                         |
                  +------+------+
                  |             |
                 YES            NO
                  |             |
                  v             v
        +------------------+  +----------------------+
        | Accumulate Sales |  | Display Total Sales  |
        | Increment Count  |  +----------+-----------+
        +--------+---------+             |
                 |                       v
                 v              +----------------------+
        +------------------+    | numCount > 0?         |
        | Calculate Salary |    +----------+-----------+
        | and Display      |               |
        +--------+---------+        +------+------+
                 |                  |             |
                 v                 YES            NO
        +------------------+        |             |
        | Prompt for Next  |        v             v
        | Sales Input      |  +-------------+  +----------------+
        +--------+---------+  | Calculate   |  | Display No     |
                 |            | Average     |  | Sales Message  |
                 +---------->+-------------+  +-------+--------+
                       Return to Condition          |
                                                    v
                                      +----------------------+
                                      | Reset Total and Count|
                                      +----------+-----------+
                                                 |
                                                 v
                                      +----------------------+
                                      | Execute Do-While     |
                                      | Processing           |
                                      +----------+-----------+
                                                 |
                                                 v
                                      +----------------------+
                                      | Display Post-Test    |
                                      | Results              |
                                      +----------+-----------+
                                                 |
                                                 v
                                      +----------------------+
                                      |      return 0        |
                                      +----------+-----------+
                                                 |
                                                 v
                                      +----------------------+
                                      |         END          |
                                      +----------------------+
```

### 7.2 Pre-Test While Loop

```text
       +--------------------------+
       | Prompt for Initial Sales |
       | and Read Input           |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | salesInput >= 0?         |
       +------------+-------------+
                    |
              +-----+-----+
              |           |
             YES          NO
              |           |
              v           v
       +----------------+  +----------------------+
       | Add Sales to   |  | Exit While Loop      |
       | totalSales     |  +----------------------+
       +--------+-------+
                |
                v
       +--------------------------+
       | Increment numCount       |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Calculate Weekly Salary  |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Display Weekly Salary    |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Prompt for Next Sales    |
       | and Read Input           |
       +------------+-------------+
                    |
                    +------> Return to Condition
```

### 7.3 Post-Test Do-While Loop

```text
       +--------------------------+
       | Begin Do-While Loop      |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Prompt for Sales Input   |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | Read Sales Amount        |
       +------------+-------------+
                    |
                    v
       +--------------------------+
       | salesInput >= 0?         |
       +------------+-------------+
                    |
              +-----+-----+
              |           |
             YES          NO
              |           |
              v           |
       +----------------+ |
       | Add Sales to   | |
       | totalSales     | |
       +--------+-------+ |
                |         |
                v         |
       +----------------+ |
       | Increment      | |
       | numCount       | |
       +--------+-------+ |
                |         |
                v         |
       +----------------+ |
       | Calculate      | |
       | Weekly Salary  | |
       +--------+-------+ |
                |         |
                v         |
       +----------------+ |
       | Display Salary | |
       +--------+-------+ |
                |         |
                +---------+
                    |
                    v
       +--------------------------+
       | salesInput >= 0?         |
       +------------+-------------+
                    |
              +-----+-----+
              |           |
             YES          NO
              |           |
              v           v
       Return to Do     Exit Loop
       Block
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Pre-Test Repetition

A `while` loop evaluates its condition before executing its statements.

This makes it possible for the loop to execute zero times if the initial condition is false.

The program uses this structure to process sales entries until a negative sentinel value is encountered.

### 8.2 Post-Test Repetition

A `do-while` loop executes its statements before evaluating its condition.

This guarantees at least one execution of the loop body.

The program demonstrates how an internal `if` statement can prevent an invalid sentinel value from being processed.

### 8.3 Sentinel-Controlled Loops

A sentinel value is a special input value used to terminate a repetition structure.

In this program:

```c
const double SENTINEL_VALUE = 0.0;
```

The constant establishes zero as the comparison boundary.

However, the actual terminating input is any negative number because both loops continue while the entered amount is greater than or equal to zero.

The negative value is not included in the total or sales count.

### 8.4 Accumulator Variables

The `totalSales` variable functions as an accumulator.

Each accepted sales amount is added to the existing total until the loop terminates.

### 8.5 Counter Variables

The `numCount` variable tracks the number of accepted sales entries.

It is incremented each time a nonnegative amount is processed.

### 8.6 Conditional Statements

The program uses `if-else` statements to control processing and prevent invalid calculations.

The `if` statement inside the post-test loop prevents negative input from being included in sales totals.

The `if-else` statement after each loop prevents division by zero when calculating average sales.

### 8.7 Constants

The program uses `const` declarations to establish fixed values.

This improves readability and makes it easier to modify the salary structure without changing the calculation statements individually.

### 8.8 Formatted Input and Output

The program uses the following format specifiers and escape sequences:

| Format / Escape Sequence | Purpose |
|---|---|
| `%lf` | Reads a `double` value using `scanf()`. |
| `%.2lf` | Displays a floating-point value to two decimal places. |
| `\n` | Moves output to a new line. |
| `\t` | Inserts horizontal tab spacing. |
| `&` | Supplies a variable's memory address to `scanf()`. |

## 9. Program Characteristics and Limitations

### 9.1 Salary Calculation Uses Accumulated Sales

The program calculates weekly salary using the accumulated sales total:

```c
weeklySalary = BASE_SALARY +
               (totalSales * COMMISSION_RATE);
```

This means each displayed salary represents the base salary plus commission on all accepted sales entered so far.

It does not calculate commission independently for each individual transaction.

### 9.2 Zero Is Accepted as a Sales Entry

The loop condition is:

```c
salesInput >= SENTINEL_VALUE
```

Since the sentinel constant is zero, a sales amount of zero is accepted and counted as an entry.

A negative amount is required to terminate either loop.

### 9.3 The Two Loops Are Separate Demonstrations

The program runs the `while` loop first and the `do-while` loop second.

It resets `totalSales` and `numCount` between the two demonstrations, allowing each loop to calculate its own totals and average independently.

The user must enter sales information again during the second demonstration.

### 9.4 Average Sales Represents Average Entry Size

The program calculates:

```c
totalSales / numCount
```

This produces the average of the accepted sales entries.

It does not represent an average across a fixed number of days, weeks, or months.

### 9.5 Input Validation

The program does not check the return value of `scanf()`.

It assumes the user enters valid numerical sales amounts. Nonnumeric input and input errors are not handled explicitly.

### 9.6 Negative Sales Values Cannot Be Entered as Transactions

Any negative value terminates the loop and is not included in the calculations.

This is appropriate for the program's sentinel-controlled design, but it means the program cannot represent refunds, returns, or negative adjustments as sales transactions.

### 9.7 Commission Calculation

The commission rate is stored as:

```c
const double COMMISSION_RATE = 0.09;
```

The value `0.09` represents 9% when used as a multiplier.

For example, if total sales equal $1,000:

\[
200+(1000\times0.09)=290
\]

The calculated weekly salary would be $290.00.

## 10. Overall Summary

Sales Commission demonstrates how repetition structures can be used to process an unknown number of user-entered values.

The program calculates a salesperson's weekly salary using a fixed base salary of $200.00 and a commission rate of 9% applied to accumulated sales.

It implements the same general sales-processing task using both a pre-test `while` loop and a post-test `do-while` loop. Negative input serves as the termination signal, while accumulator and counter variables track total sales and the number of accepted entries.

The program also demonstrates constants, variable initialization, compound assignment, arithmetic calculations, relational operators, conditional statements, formatted input/output, and division-by-zero prevention.

Overall, this program provides a practical comparison of pre-test and post-test repetition structures and illustrates how sentinel-controlled loops can process user input until a termination condition is met.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational, instructional, and programming-reference purposes. It is intended to demonstrate C programming concepts, including pre-test and post-test loops, sentinel-controlled repetition, constants, variables, accumulators, counters, conditional statements, arithmetic operations, and formatted input/output.

This source code is not intended to be submitted as another student's original work, used to circumvent coursework requirements, or used for plagiarism or academic dishonesty.

Students should maintain academic integrity by understanding the source code, independently completing assigned coursework, and following their institution's academic policies.

The author is not responsible for unauthorized use, academic misconduct, plagiarism, cheating, or any other misuse of this program or its contents.