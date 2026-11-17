# Stock Price – C Program Documentation

| **Program Information** | **Details** |
|---|---|
| Program Name | Stock Price |
| Programmer | Brian Lorick |
| Programming Language | C |
| Development Environment | Microsoft Visual Studio |
| Course Topic | Chapter 2 – Fundamentals |
| Original Date | January 25, 2024 |
| Source File | `Stock Price.c` |

---

## 1. Program Overview

**Stock Price** is a C program designed to calculate the total purchase price of a specified number of stock shares.

The program prompts the user to enter two values:

1. The number of stock shares they intend to purchase.
2. The dollar amount charged for each individual share.

After collecting the information, the program multiplies the number of shares by the price per share to calculate the total amount of money required for the purchase.

The program then displays the number of shares, the individual share price, and the calculated purchase price.

**Example:**

If a user enters 25 shares at $12.50 per share, the program calculates:

\[
25 \times 12.50 = 312.50
\]

The total purchase price is $312.50.

The program demonstrates fundamental C programming concepts, including variable declarations, integer and floating-point data types, standard input/output functions, user input, arithmetic multiplication, assignment statements, and formatted output.

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
| `printf()` | Displays input prompts and the calculated purchase price. |
| `scanf()` | Accepts the number of shares and dollar amount per share. |

No additional libraries are required because the program performs only basic input, multiplication, and output operations.

## 3. Variables and Data Structures

The program declares three variables inside the `main()` function.

### 3.1 Variable Declarations

```c
int stockShares = 0;
double shareAmount = 0.0;
double purchasePrice = 0.0;
```

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `stockShares` | `int` | `0` | Stores the number of stock shares the user intends to purchase. |
| `shareAmount` | `double` | `0.0` | Stores the dollar price of one individual share. |
| `purchasePrice` | `double` | `0.0` | Stores the calculated total purchase price. |

### 3.2 Data Types

The program uses two numerical data types:

- **`int`** – Stores the number of stock shares as a whole number.
- **`double`** – Stores monetary values and the calculated purchase price with decimal precision.

The `int` data type is appropriate for the share count because the program accepts whole-number quantities.

The `double` data type allows the program to process fractional monetary values, such as `$12.50` per share.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
```

The `main()` function is the entry point of the program.

It contains the variable declarations, input statements, multiplication operation, output statements, and final return statement.

The source code is organized into three primary sections:

1. Input
2. Processing
3. Output

### 4.2 Input – Accepting the Number of Shares

```c
printf("Enter the number of shares of stock: ");
scanf("%d", &stockShares);
```

The program first prompts the user to enter the number of stock shares they want to purchase.

The `printf()` function displays the prompt, while `scanf()` accepts the user's input and stores it in `stockShares`.

**Input format specifier: `%d`**

The `%d` conversion specifier instructs `scanf()` to read an integer value.

The address-of operator (`&`) provides the memory address of `stockShares`, allowing `scanf()` to store the entered value directly in that variable.

### 4.3 Input – Accepting the Price Per Share

```c
printf("Enter the dollar amount per share: $");
scanf("%lf", &shareAmount);
```

The program then prompts the user to enter the dollar amount charged for each individual share.

The entered value is stored in `shareAmount`.

**Input format specifier: `%lf`**

The `%lf` conversion specifier instructs `scanf()` to read a `double` value.

Using `double` allows the program to accept decimal prices, such as:

- `$5.25`
- `$12.50`
- `$48.75`
- `$103.99`

### 4.4 Processing – Calculating the Purchase Price

```c
purchasePrice = stockShares * shareAmount;
```

This statement performs the primary calculation of the program.

It multiplies the number of shares by the dollar amount per share.

The resulting value is assigned to `purchasePrice`.

**Mathematical formula:**

\[
\text{Purchase Price}
=
\text{Number of Shares}
\times
\text{Price Per Share}
\]

**Example:**

Given:

```text
stockShares = 25
shareAmount = 12.50
```

The calculation becomes:

\[
25 \times 12.50 = 312.50
\]

The program stores the calculated result in:

```c
purchasePrice
```

The multiplication operation is performed using floating-point arithmetic because `shareAmount` is declared as a `double`.

### 4.5 Output – Displaying the Purchase Information

```c
printf("The amount of money needed to purchase %d shares of stock\n",
       stockShares);

printf("at $%.2lf is $%.2lf.\n",
       shareAmount, purchasePrice);
```

These statements display the number of shares, the price per share, and the total amount required to purchase the shares.

The first statement displays the quantity of shares.

The second statement displays the individual share price and calculated purchase price.

### 4.6 Output Formatting

The program uses the following format specifiers:

| Format Specifier | Purpose |
|---|---|
| `%d` | Displays an integer value. |
| `%.2lf` | Displays a floating-point value to two decimal places. |
| `\n` | Moves the output cursor to the next line. |
| `&` | Supplies the memory address required by `scanf()`. |

The `%.2lf` format specifier ensures that monetary values are displayed with two digits after the decimal point.

For example:

```text
12.5
```

is displayed as:

```text
12.50
```

This formatting provides consistent monetary presentation.

### 4.7 Blank Line Formatting

```c
printf("\n");
```

The program uses an additional newline statement to insert a blank line after the calculated results.

This separates the program output from the console prompt.

### 4.8 Program Termination

```c
return 0;
```

The `return 0` statement terminates the `main()` function and indicates successful program execution.

## 5. Operators Used

The program uses assignment, multiplication, and address-of operators.

| Operator | Category | Example | Purpose |
|---|---|---|---|
| `=` | Assignment | `purchasePrice = stockShares * shareAmount;` | Assigns the calculated purchase price to a variable. |
| `*` | Arithmetic | `stockShares * shareAmount` | Multiplies the share quantity by the price per share. |
| `&` | Address-of | `&stockShares` | Supplies the memory address required by `scanf()`. |

### 5.1 Assignment Operator

The assignment operator (`=`) stores a value in a variable.

For example:

```c
purchasePrice = stockShares * shareAmount;
```

The multiplication expression is evaluated first, and its result is assigned to `purchasePrice`.

### 5.2 Multiplication Operator

The multiplication operator (`*`) performs arithmetic multiplication.

It is used to determine the total purchase cost based on the number of shares and their individual price.

### 5.3 Address-of Operator

The address-of operator (`&`) retrieves the memory address of a variable.

For example:

```c
scanf("%d", &stockShares);
```

This allows `scanf()` to store the user's input directly in the memory location associated with `stockShares`.

## 6. Program Execution Sequence

The program follows this execution sequence:

1. The program enters the `main()` function.
2. Three variables are declared and initialized.
3. The program prompts the user to enter the number of stock shares.
4. The entered quantity is stored in `stockShares`.
5. The program prompts the user to enter the dollar amount per share.
6. The entered price is stored in `shareAmount`.
7. The program multiplies `stockShares` by `shareAmount`.
8. The calculated result is assigned to `purchasePrice`.
9. A blank line is displayed.
10. The program displays the number of shares being purchased.
11. The program displays the individual share price.
12. The program displays the total purchase price.
13. Another blank line is printed.
14. The program returns zero and terminates.

## 7. Text-Based Program Flowchart

### 7.1 Main Program Flow

```text
              +--------------------------+
              |           START          |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Declare Variables        |
              | stockShares              |
              | shareAmount              |
              | purchasePrice            |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Prompt for Number of     |
              | Stock Shares             |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Read Input into          |
              | stockShares              |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Prompt for Dollar Amount |
              | Per Share                |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Read Input into          |
              | shareAmount              |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Calculate Purchase Price |
              | Shares * Price Per Share |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Store Result in          |
              | purchasePrice            |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Display Number of Shares |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              | Display Price Per Share  |
              | and Purchase Price       |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              |        return 0          |
              +-------------+------------+
                            |
                            v
              +--------------------------+
              |            END           |
              +--------------------------+
```

### 7.2 Purchase Price Calculation

```text
       +----------------------------+
       | Receive Number of Shares   |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Receive Price Per Share    |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Multiply Both Values       |
       | Shares * Share Price       |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Store Result in            |
       | purchasePrice              |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Display Purchase Price     |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       |            END             |
       +----------------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Variable Declaration and Initialization

The program demonstrates how variables are declared using specific data types and initialized with starting values.

```c
int stockShares = 0;
```

This statement declares an integer variable and assigns it an initial value of zero.

### 8.2 Integer Data Types

The `int` data type stores the number of shares as a whole-number quantity.

### 8.3 Floating-Point Data Types

The `double` data type allows the program to store monetary values containing decimal components.

This is important because stock prices are not necessarily whole numbers.

### 8.4 Standard Input and Output

The program uses `scanf()` and `printf()` to communicate with the user.

`scanf()` collects the required information, while `printf()` displays the results.

### 8.5 Arithmetic Processing

The program demonstrates multiplication using two variables containing user-provided values.

The result is stored in a third variable for later output.

### 8.6 Assignment Statements

The program uses assignment statements to initialize variables and store the calculated purchase price.

### 8.7 Sequential Execution

The program executes its statements in the order they appear in the source code.

There are no loops, conditional statements, or decision structures.

### 8.8 Formatted Input and Output

The program demonstrates how format specifiers control the interpretation and presentation of numerical values.

| Format / Escape Sequence | Purpose |
|---|---|
| `%d` | Reads or displays an integer. |
| `%lf` | Reads a `double` value using `scanf()`. |
| `%.2lf` | Displays a floating-point value to two decimal places. |
| `\n` | Moves output to a new line. |
| `&` | Supplies the memory address required by `scanf()`. |

## 9. Program Characteristics and Limitations

### 9.1 Whole-Number Share Quantity

The program declares:

```c
int stockShares = 0;
```

This means the program accepts a whole-number quantity of shares.

It does not support fractional share quantities.

### 9.2 Decimal Stock Prices

The `shareAmount` variable uses the `double` data type.

This allows the program to process stock prices containing decimal values.

### 9.3 No Input Validation

The program does not check whether the user enters valid or reasonable values.

For example, it does not prevent:

- Negative share quantities.
- Zero shares.
- Negative stock prices.
- Nonnumeric input.

The source code assumes that the user provides valid numerical information.

### 9.4 No Commission or Additional Fees

The program calculates the purchase price using only the number of shares multiplied by the individual share price.

It does not account for:

- Brokerage commissions.
- Transaction fees.
- Regulatory fees.
- Taxes.
- Other investment-related expenses.

Therefore, the result represents the basic share purchase cost rather than a complete transaction total.

### 9.5 Floating-Point Precision

The program uses `double` for monetary calculations.

Floating-point representations can introduce small precision differences because some decimal values cannot be represented exactly in binary.

The output is formatted to two decimal places, but the underlying calculation is performed using floating-point arithmetic.

### 9.6 Single Transaction Processing

The program calculates the purchase price for one transaction per execution.

It does not contain loops for processing multiple stock purchases or calculating a portfolio's total value.

## 10. Overall Summary

Stock Price demonstrates fundamental C programming concepts through a simple financial calculation application.

The program accepts a stock share quantity and an individual share price, multiplies the two values, and displays the total amount of money required to purchase the shares.

The source code demonstrates variable declarations, integer and floating-point data types, standard input/output functions, assignment statements, arithmetic multiplication, address-of operations, formatted output, and sequential program execution.

Overall, the program provides a practical introduction to collecting numerical input, performing arithmetic calculations, and displaying financial results using the C programming language.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational, instructional, and programming-reference purposes. It is intended to demonstrate fundamental C programming concepts, including variable declarations, integer and floating-point data types, formatted input/output, assignment statements, arithmetic multiplication, and sequential program execution.

This source code is not intended to be submitted as another student's original work, used to circumvent coursework requirements, or used for plagiarism or academic dishonesty.

Students should maintain academic integrity by understanding the source code, independently completing assigned coursework, and following their institution's academic policies.

The author is not responsible for unauthorized use, academic misconduct, plagiarism, cheating, or any other misuse of this program or its contents.