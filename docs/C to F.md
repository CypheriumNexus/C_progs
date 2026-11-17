# C to F – C Programming Project Documentation

**Programmer:** Brian Lorick  
**Program Name:** C to F  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio 2019  
**Course Topic:** Chapter 6 – Functions  
**Original Date:** April 1, 2024  
**Source File:** `C to F.c`

---

## 1. Program Overview

The **C to F** program is a temperature conversion application that prompts the user to enter a starting and ending temperature in Fahrenheit. It validates both inputs, converts each Fahrenheit temperature within the specified range to Celsius, and displays the results in a formatted table.

The program demonstrates the use of user-defined functions, input validation, `while` loops, `for` loops, conditional statements, arithmetic operations, and formatted console output.

The program follows three primary stages:

1. **Input and Validation** – Collects the starting and ending Fahrenheit temperatures and verifies that both values fall within the permitted range of -100 through 300 degrees. It also ensures that the ending temperature is greater than the starting temperature.
2. **Processing** – Iterates through the temperature range and calls a conversion function to calculate the Celsius equivalent of each Fahrenheit value.
3. **Output** – Displays the Fahrenheit temperatures and their corresponding Celsius conversions in a formatted table.

The program uses a separate function, `fahrenheitToCelsius()`, to perform the conversion calculation. This separates the mathematical operation from the primary program logic.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive | Purpose |
|---|---|
| `#define _CRT_SECURE_NO_WARNINGS` | Suppresses Microsoft Visual Studio warnings associated with certain standard C functions, including `scanf()`. |
| `#include <stdio.h>` | Includes the Standard Input/Output library, providing access to `printf()` and `scanf()`. |

### 2.2 Standard Library Functions

| Function | Purpose |
|---|---|
| `printf()` | Displays prompts, validation messages, table headings, and conversion results. |
| `scanf()` | Accepts integer temperature values entered by the user and stores them in variables. |

The program requires only the standard input/output library. The temperature conversion function is user-defined and does not require an additional library.

## 3. Variables and Data Structures

### 3.1 Integer Variables

| Variable | Data Type | Purpose |
|---|---|---|
| `startTemp` | `int` | Stores the starting Fahrenheit temperature entered by the user. |
| `endTemp` | `int` | Stores the ending Fahrenheit temperature entered by the user. |
| `i` | `int` | Loop counter used to iterate through the Fahrenheit temperature range. |

The two temperature variables are declared inside `main()` and store the user's input.

The variable `i` is declared within the `for` loop and controls the iteration through the selected temperature range.

### 3.2 Floating-Point Variables and Parameters

| Identifier | Data Type | Purpose |
|---|---|---|
| `fahrenheit` | `double` | Function parameter that receives a Fahrenheit temperature for conversion. |
| Function return value | `double` | Returns the calculated Celsius equivalent. |

The `double` data type is used for the conversion function because temperature conversions can produce fractional values.

Although the user enters whole-number Fahrenheit temperatures, the Celsius calculations retain floating-point precision internally.

### 3.3 Data Structures

The program does not use arrays, structures, or other aggregate data structures.

Instead, it processes each temperature individually using a `for` loop and passes the current Fahrenheit value to the conversion function.

## 4. Processing Logic and Statements

### 4.1 User-Defined Conversion Function

The program defines a function named `fahrenheitToCelsius()`.

```c
double fahrenheitToCelsius(double fahrenheit)
{
    return (5.0 / 9.0) * (fahrenheit - 32);
}
```

This function receives a Fahrenheit temperature as a `double` parameter and returns its Celsius equivalent.

The function uses the standard Fahrenheit-to-Celsius conversion formula:

\[
C = \frac{5}{9}(F-32)
\]

Where:

- \(C\) represents the Celsius temperature.
- \(F\) represents the Fahrenheit temperature.
- \(32\) is subtracted from the Fahrenheit value.
- The result is multiplied by the fraction \(5/9\).

The expression:

```c
(5.0 / 9.0)
```

Uses floating-point constants to ensure that the division produces a floating-point result rather than integer division.

The `return` statement sends the calculated Celsius value back to the location where the function was called.

### 4.2 Main Function

```c
int main() {

    int startTemp;
    int endTemp;

    // Input, validation, and processing statements

    return 0;
}
```

The `main()` function is the program's entry point. It controls the sequence of operations, including input collection, validation, temperature iteration, function calls, and output.

The program begins by declaring the two integer variables used to store the starting and ending temperatures.

### 4.3 Collecting the Starting Temperature

```c
printf("Enter a starting Fahrenheit temperature: ");
scanf("%d", &startTemp);
```

The `printf()` statement prompts the user to enter the starting Fahrenheit temperature.

The `scanf()` statement reads the entered integer and stores it in `startTemp`.

The `%d` format specifier indicates that the program expects an integer value.

The address-of operator (`&`) provides the memory address of `startTemp` so that `scanf()` can store the entered value in that variable.

### 4.4 Validating the Starting Temperature

```c
while (startTemp < -100 || startTemp > 300)
{
    printf("   The starting temperature must be between -100 and 300 degrees.\n");
    printf("   Please re-enter the starting temperature: ");
    scanf("%d", &startTemp);
}
```

The program uses a `while` loop to ensure that the starting temperature falls within the permitted range.

The condition:

```c
startTemp < -100 || startTemp > 300
```

Checks whether the entered temperature is below -100 or above 300.

The logical OR operator (`||`) means that either condition being true causes the entire expression to evaluate as true.

If the input is invalid:

1. An error message is displayed.
2. The user is prompted to enter the starting temperature again.
3. `scanf()` reads the replacement value.
4. The loop evaluates the condition again.

The loop continues until the user enters a temperature between -100 and 300, inclusive.

### 4.5 Collecting the Ending Temperature

```c
printf("Enter an ending Fahrenheit temperature: ");
scanf("%d", &endTemp);
```

After the starting temperature passes validation, the program prompts the user for an ending Fahrenheit temperature.

The entered integer is stored in `endTemp`.

### 4.6 Validating the Ending Temperature

```c
while (endTemp < -100 || endTemp > 300 || endTemp <= startTemp)
{
    if (endTemp < -100 || endTemp > 300)
    {
        printf("   The ending temperature must be between -100 and 300 degrees.\n");
    }
    else
    {
        printf("   The ending temperature, %d, must be greater than the starting temperature.\n", endTemp);
    }

    printf("   Please re-enter the ending temperature: ");
    scanf("%d", &endTemp);
}
```

The ending temperature is subject to two validation requirements:

1. It must be between -100 and 300 degrees, inclusive.
2. It must be greater than the starting temperature.

The `while` condition combines three relational expressions using the logical OR operator:

```c
endTemp < -100 || endTemp > 300 || endTemp <= startTemp
```

The loop continues if any of these conditions is true.

Inside the loop, an `if/else` statement determines which error message should be displayed.

**First condition:**

```c
if (endTemp < -100 || endTemp > 300)
```

Checks whether the ending temperature is outside the permitted range.

If true, the program displays a range validation message.

**Second condition:**

```c
else
```

Executes when the ending temperature is within the permitted range but is not greater than the starting temperature.

The program displays a message indicating that the ending temperature must be greater than the starting temperature.

After displaying the appropriate message, the program prompts the user to enter another ending temperature.

This process repeats until both validation requirements are satisfied.

### 4.7 Displaying the Table Header

```c
printf("\nFahrenheit\tCelsius\n");
```

Once both temperatures pass validation, the program displays the table headings.

The escape sequences are used to format the output:

| Escape Sequence | Purpose |
|---|---|
| `\n` | Moves the cursor to a new line. |
| `\t` | Inserts a horizontal tab to separate the columns. |

The resulting output begins with the Fahrenheit and Celsius column labels.

### 4.8 Iterating Through the Temperature Range

```c
for (int i = startTemp; i <= endTemp; i++)
{
    printf("%d\t\t%.1f\n", i, fahrenheitToCelsius(i));
}
```

The program uses a `for` loop to process every integer Fahrenheit temperature between the starting and ending values.

The loop contains three primary components:

| Component | Expression | Purpose |
|---|---|---|
| Initialization | `int i = startTemp` | Initializes the counter to the starting temperature. |
| Condition | `i <= endTemp` | Continues the loop while the counter is less than or equal to the ending temperature. |
| Update | `i++` | Increments the counter by one after each iteration. |

During each iteration, the current Fahrenheit value is passed to `fahrenheitToCelsius()`.

The function calculates and returns the corresponding Celsius temperature.

The `printf()` statement then displays both values:

```c
printf("%d\t\t%.1f\n", i, fahrenheitToCelsius(i));
```

The format specifiers control how the values appear:

- `%d` displays the current Fahrenheit temperature as an integer.
- `\t\t` inserts horizontal spacing between the columns.
- `%.1f` displays the Celsius conversion with one digit after the decimal point.
- `\n` moves the cursor to the next line.

The loop includes the ending temperature because its condition uses `<=` rather than `<`.

### 4.9 Program Termination

```c
printf("\n");

return 0;
```

After the `for` loop completes, the program prints a blank line and returns `0` from `main()`.

This indicates that the program has completed normal execution.

## 5. Operators Used

The program uses relational, logical, arithmetic, assignment, and increment operators.

### 5.1 Relational Operators

| Operator | Name | Purpose |
|---|---|---|
| `<` | Less than | Checks whether a temperature is below -100. |
| `>` | Greater than | Checks whether a temperature exceeds 300. |
| `<=` | Less than or equal to | Validates the ending temperature against the starting temperature and controls the `for` loop. |

### 5.2 Logical Operators

| Operator | Name | Purpose |
|---|---|---|
| `||` | Logical OR | Checks whether any of the validation conditions are true. |

Example:

```c
startTemp < -100 || startTemp > 300
```

The expression evaluates as true if the starting temperature is below -100 or above 300.

The ending-temperature validation also uses logical OR to combine its three conditions.

### 5.3 Arithmetic Operators

| Operator | Name | Purpose |
|---|---|---|
| `-` | Subtraction | Subtracts 32 from the Fahrenheit temperature. |
| `/` | Division | Divides 5.0 by 9.0 in the conversion formula. |
| `*` | Multiplication | Multiplies the conversion fraction by the adjusted Fahrenheit value. |

### 5.4 Assignment and Increment Operators

| Operator | Name | Purpose |
|---|---|---|
| `=` | Assignment | Stores user input in variables and initializes the loop counter. |
| `++` | Increment | Increases the Fahrenheit loop counter by one during each iteration. |

## 6. Program Execution Sequence

The program follows a sequential input-validation-processing-output structure.

| Step | Operation | Description |
|---:|---|---|
| 1 | Program Start | Execution begins in `main()`. |
| 2 | Variable Declaration | Declares `startTemp` and `endTemp`. |
| 3 | Starting Temperature Input | Prompts the user for the starting Fahrenheit temperature. |
| 4 | Starting Temperature Validation | Checks whether the value is between -100 and 300. |
| 5 | Input Retry | If invalid, displays an error and requests another starting temperature. |
| 6 | Ending Temperature Input | Prompts the user for the ending Fahrenheit temperature. |
| 7 | Ending Temperature Validation | Checks the permitted range and verifies that the ending temperature is greater than the starting temperature. |
| 8 | Input Retry | If invalid, displays the appropriate error message and requests another ending temperature. |
| 9 | Table Header | Displays the Fahrenheit and Celsius column headings. |
| 10 | Loop Initialization | Sets the loop counter `i` to the starting temperature. |
| 11 | Loop Condition | Checks whether `i` is less than or equal to `endTemp`. |
| 12 | Function Call | Passes the current Fahrenheit temperature to `fahrenheitToCelsius()`. |
| 13 | Temperature Conversion | Calculates the Celsius equivalent and returns the result. |
| 14 | Display Conversion | Prints the Fahrenheit and Celsius values in the table. |
| 15 | Loop Increment | Increases `i` by one and repeats the process. |
| 16 | Loop Completion | Stops when `i` exceeds the ending temperature. |
| 17 | Program Termination | Prints a blank line and returns `0`. |

## 7. Text-Based Program Flowchart

```text
              +--------------------------+
              |       PROGRAM START      |
              +--------------------------+
                           |
                           v
              +--------------------------+
              |         main()           |
              | Declare startTemp        |
              | Declare endTemp          |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Prompt for starting      |
              | Fahrenheit temperature   |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Read startTemp           |
              +--------------------------+
                           |
                           v
                 +-------------------+
                 | startTemp < -100  |
                 | OR startTemp > 300|
                 +-------------------+
                    |             |
                   YES            NO
                    |             |
                    v             v
          +----------------+  +--------------------------+
          | Display range  |  | Prompt for ending        |
          | error message  |  | Fahrenheit temperature   |
          +----------------+  +--------------------------+
                    |                    |
                    v                    v
          +----------------+  +--------------------------+
          | Request new    |  | Read endTemp             |
          | startTemp      |  +--------------------------+
          +----------------+              |
                    |                     v
                    +-----------> +-------------------+
                                  | Validate endTemp: |
                                  | < -100 OR > 300   |
                                  | OR <= startTemp   |
                                  +-------------------+
                                     |            |
                                    YES           NO
                                     |            |
                                     v            v
                            +----------------+  +----------------------+
                            | Check reason   |  | Display table header |
                            | for invalidity |  +----------------------+
                            +----------------+             |
                                     |                      v
                        +------------+----------+   +----------------------+
                        |                       |   | Initialize i =       |
                        v                       v   | startTemp            |
               +----------------+    +----------------+ +----------------------+
               | Outside range? |    | endTemp <=      |             |
               +----------------+    | startTemp?      |             v
                  |          |       +----------------+     +----------------+
                 YES         NO         |          |        | i <= endTemp?  |
                  |          |         YES         NO       +----------------+
                  v          v          |          |          |           |
          +-------------+ +-------------+          |         YES          NO
          | Display     | | Display     |          |          |           |
          | range error | | must be     |          |          v           v
          +-------------+ | greater     |          |  +----------------+ +----------------+
                  |      +-------------+          |  | Call           | | Print blank    |
                  +-------------+----------------+  | fahrenheitTo   | | line           |
                                |                    | Celsius(i)     | +----------------+
                                v                    +----------------+          |
                       +----------------------+               |                 v
                       | Request new endTemp  |               v        +----------------+
                       +----------------------+      +----------------+ | return 0       |
                                |                     | Calculate     | +----------------+
                                +---------------------+ | Celsius       |          |
                                                       +----------------+          v
                                                               |           +----------------+
                                                               v           |   PROGRAM END  |
                                                       +----------------+
                                                       | Display        |
                                                       | Fahrenheit and |
                                                       | Celsius values |
                                                       +----------------+
                                                               |
                                                               v
                                                       +----------------+
                                                       | Increment i    |
                                                       | i++            |
                                                       +----------------+
                                                               |
                                                               +----> Return
                                                                     to
                                                                 i <= endTemp?
```

## 8. Important Programming Concepts Demonstrated

### 8.1 User-Defined Functions

The program defines `fahrenheitToCelsius()` to perform the temperature conversion.

Separating the calculation into its own function improves modularity and allows the conversion operation to be reused without duplicating the formula.

### 8.2 Function Parameters and Return Values

The conversion function accepts a `double` parameter named `fahrenheit`.

It calculates the Celsius equivalent and returns the result as a `double`.

The function call:

```c
fahrenheitToCelsius(i)
```

Passes the current loop counter as the Fahrenheit argument.

### 8.3 Input Validation

The program uses `while` loops to repeatedly request input until the user enters acceptable values.

This prevents temperatures outside the permitted range and prevents an ending temperature that is less than or equal to the starting temperature from being processed.

### 8.4 While Loops

The two `while` loops are used for input validation.

Unlike a `for` loop, which is generally used when the iteration sequence is defined, a `while` loop continues based on a condition that must become false before execution proceeds.

### 8.5 For Loops

The `for` loop processes each integer Fahrenheit temperature between the starting and ending values.

Its initialization, condition, and increment expressions control the iteration sequence.

### 8.6 Conditional Statements

The program uses an `if/else` statement inside the ending-temperature validation loop to determine which error message should be displayed.

This demonstrates how conditional statements can control program behavior based on different validation conditions.

### 8.7 Logical OR

The logical OR operator (`||`) combines multiple validation conditions.

The program uses it to determine whether a temperature falls outside the permitted range or whether the ending temperature violates the required relationship with the starting temperature.

### 8.8 Floating-Point Arithmetic

The conversion formula uses `5.0 / 9.0` rather than `5 / 9`.

Using decimal constants ensures that the division is performed using floating-point arithmetic, preserving the fractional conversion factor.

### 8.9 Formatted Output

The program uses format specifiers and escape sequences to produce a readable two-column temperature table.

The output uses `%d` for Fahrenheit integers and `%.1f` for Celsius values displayed to one decimal place.

## 9. Program Characteristics and Limitations

| Characteristic | Description |
|---|---|
| Input Quantity | Accepts a starting and ending temperature. |
| Input Data Type | Uses `int` for both temperatures. |
| Permitted Range | -100 through 300 degrees Fahrenheit, inclusive. |
| Range Validation | Uses `while` loops and relational operators. |
| Range Relationship | Ending temperature must be greater than starting temperature. |
| Conversion Function | Uses `fahrenheitToCelsius()`. |
| Conversion Formula | \(C = \frac{5}{9}(F-32)\). |
| Iteration Method | Uses a `for` loop to process the temperature range. |
| Loop Increment | Increases the Fahrenheit value by one degree. |
| Output Format | Displays Fahrenheit and Celsius in a table. |
| Celsius Precision | Displays one decimal place. |
| Program Structure | Uses one user-defined conversion function and `main()`. |
| Termination | Returns `0` after processing the temperature range. |

### 9.1 Inclusive Temperature Boundaries

The validation permits temperatures of exactly -100 and 300 degrees because the conditions reject values below -100 and above 300.

The `for` loop also includes the ending temperature because it uses:

```c
i <= endTemp
```

### 9.2 Ending Temperature Requirement

The ending temperature must be greater than the starting temperature.

If both temperatures are equal, the program rejects the ending temperature and requests another value.

This means the program always processes at least two Fahrenheit values when valid inputs are provided.

### 9.3 Integer Temperature Input

The program uses `int` variables and `%d` input format specifiers.

Therefore, users can enter whole-number Fahrenheit temperatures only. Decimal Fahrenheit input is not supported by the current implementation.

### 9.4 Input Validation Limitations

The program validates the numerical range and relationship between the two temperatures.

However, it does not check whether `scanf()` successfully reads an integer. Nonnumeric input is not handled by a separate error-recovery mechanism.

### 9.5 Output Precision

The conversion function returns a `double`, but the output uses `%.1f`.

This means the Celsius result is displayed with one digit after the decimal point, even though the internal calculation retains additional floating-point precision.

## 10. Overall Summary

The **C to F** program demonstrates how user-defined functions, loops, and input validation can be combined to perform repeated temperature conversions in C.

The program begins by requesting a starting Fahrenheit temperature and validating that it falls between -100 and 300 degrees. It then collects an ending temperature and verifies both its permitted range and its relationship to the starting value.

Once the inputs are valid, a `for` loop iterates through every integer temperature in the selected range. During each iteration, the program calls `fahrenheitToCelsius()`, which applies the Fahrenheit-to-Celsius conversion formula and returns the result.

The program displays each original Fahrenheit value alongside its Celsius equivalent in a formatted table.

The primary programming concepts demonstrated include user-defined functions, function parameters, return values, `while` loops, `for` loops, conditional statements, relational operators, logical operators, arithmetic operations, input validation, and formatted console output.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, including functions, loops, conditional statements, input validation, arithmetic calculations, and formatted output.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.