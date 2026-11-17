# How Many – C Programming Project Documentation

**Programmer:** Brian Lorick  
**Program Name:** How Many  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio 2019  
**Course Topic:** Chapter 2 – Fundamentals  
**Original Date:** January 30, 2024  
**Source File:** `How Many.c`

---

## 1. Program Overview

The **How Many** program is a basic C application that calculates how many fast-food menu items a user can afford based on the amount of money they have available.

The program displays a menu containing three food items and their prices:

- Hot Dog with Chili – $1.50
- Hamburger – $3.00
- Chicken Sandwich – $2.75

After displaying the menu, the program prompts the user to enter an available monetary amount. It then calculates the maximum number of each individual menu item the user could purchase with that amount.

The results are displayed as three separate purchasing options.

The program demonstrates fundamental C programming concepts, including variable declarations, constants, user input, arithmetic operations, assignment statements, data types, and formatted console output.

The program follows three primary stages:

1. **Input** – Displays the menu and collects the amount of money available from the user.
2. **Processing** – Divides the available money by each item's price to calculate the maximum affordable quantity.
3. **Output** – Displays the purchasing possibilities for each menu item.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive | Purpose |
|---|---|
| `#define _CRT_SECURE_NO_WARNINGS` | Disables Microsoft Visual Studio warnings associated with certain standard C functions, including `scanf()`. |
| `#include <stdio.h>` | Includes the Standard Input/Output library, providing access to `printf()` and `scanf()`. |

### 2.2 Standard Library Functions

| Function | Purpose |
|---|---|
| `printf()` | Displays the menu, item prices, input prompt, and purchasing calculations. |
| `scanf()` | Accepts the user's monetary amount and stores it in a variable. |

The program uses the standard input/output library for all console interactions. No additional libraries or user-defined functions are required.

## 3. Variables and Data Structures

### 3.1 Integer Variables

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `hotDogNum` | `int` | `0` | Stores the maximum number of hot dogs the user can afford. |
| `chickenSandwichNum` | `int` | `0` | Stores the maximum number of chicken sandwiches the user can afford. |
| `hamburgerNum` | `int` | `0` | Stores the maximum number of hamburgers the user can afford. |

These variables store the calculated quantities of each menu item.

The `int` data type is appropriate because the program calculates whole-number quantities rather than fractional food items.

### 3.2 Floating-Point Variable

| Variable | Data Type | Initial Value | Purpose |
|---|---|---:|---|
| `moneyAmount` | `double` | `0.0` | Stores the amount of money entered by the user. |

The `double` data type allows the program to accept monetary values containing decimal portions, such as `$10.50`.

### 3.3 Constant Variables

| Constant | Data Type | Value | Purpose |
|---|---|---:|---|
| `HOTDOG_PRICE` | `const double` | `1.50` | Defines the price of one hot dog with chili. |
| `CHICKENSANDWICH_PRICE` | `const double` | `2.75` | Defines the price of one chicken sandwich. |
| `HAMBURGER_PRICE` | `const double` | `3.00` | Defines the price of one hamburger. |

The `const` keyword identifies values that should not be modified during program execution.

Using named constants makes the calculations easier to read and maintain. If a menu price changes, its corresponding constant can be updated without modifying the calculation statements.

### 3.4 Data Structures

The program does not use arrays, structures, or other aggregate data structures.

Instead, it uses individual variables to store the available money, menu prices, and calculated quantities.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
{
    // Constant and Variable Declarations

    // Menu Display

    // Input

    // Processing

    // Output

    return 0;
}
```

The `main()` function is the program's entry point. All declarations, input operations, calculations, and output statements are contained within this function.

The parameter `void` indicates that the function does not receive command-line arguments.

The program executes sequentially from the first statement in `main()` to the final `return 0;` statement.

### 4.2 Variable and Constant Declarations

```c
int hotDogNum = 0;
int chickenSandwichNum = 0;
int hamburgerNum = 0;

double moneyAmount = 0.0;

const double HOTDOG_PRICE = 1.50;
const double CHICKENSANDWICH_PRICE = 2.75;
const double HAMBURGER_PRICE = 3.00;
```

The program begins by declaring and initializing its variables and constants.

The integer variables are initialized to zero because they will eventually hold the calculated quantities of each menu item.

The `moneyAmount` variable is initialized to `0.0` and will store the user's input.

The three price constants establish the fixed menu prices used throughout the calculations.

### 4.3 Displaying the Menu

```c
printf("        Fast Food" "\n");
printf("-------------------------" "\n");
printf("Hot Dog w/ Chili....$%.2lf" "\n", HOTDOG_PRICE);
printf("Hamburger...........$%.2lf" "\n", HAMBURGER_PRICE);
printf("Chicken Sandwich....$%.2lf" "\n", CHICKENSANDWICH_PRICE);

printf("" "\n");
```

The program uses multiple `printf()` statements to display the fast-food menu.

Each menu item is displayed with its corresponding constant price.

The format specifier:

```c
%.2lf
```

Displays the monetary value with exactly two digits after the decimal point.

The program also uses `\n` to move to a new line and separate the menu from the input prompt.

The menu prices are displayed in this order:

1. Hot Dog with Chili
2. Hamburger
3. Chicken Sandwich

### 4.4 Collecting User Input

```c
printf("How much money do you have? $");
scanf("%lf", &moneyAmount);
```

The program prompts the user to enter the amount of money they have available.

The `scanf()` statement reads the entered monetary amount and stores it in `moneyAmount`.

The format specifier:

```c
%lf
```

Instructs `scanf()` to read a `double` value.

The address-of operator (`&`) provides the memory address of `moneyAmount`, allowing `scanf()` to store the entered value in that variable.

After collecting the input, the program displays a blank line before proceeding to the calculations.

### 4.5 Calculating Affordable Quantities

The processing stage consists of three arithmetic assignment statements.

```c
hotDogNum = moneyAmount / HOTDOG_PRICE;

hamburgerNum = moneyAmount / HAMBURGER_PRICE;

chickenSandwichNum = moneyAmount / CHICKENSANDWICH_PRICE;
```

Each statement divides the available monetary amount by the price of one menu item.

The resulting value is assigned to the corresponding integer variable.

The calculations follow these formulas:

**Hot Dogs:**

\[
\text{Hot Dog Quantity} =
\frac{\text{Available Money}}{1.50}
\]

**Hamburgers:**

\[
\text{Hamburger Quantity} =
\frac{\text{Available Money}}{3.00}
\]

**Chicken Sandwiches:**

\[
\text{Chicken Sandwich Quantity} =
\frac{\text{Available Money}}{2.75}
\]

Because the destination variables are integers, any fractional portion of the calculated result is discarded during conversion from `double` to `int`.

For example, if the user enters `$10.00`:

| Menu Item | Calculation | Affordable Quantity |
|---|---:|---:|
| Hot Dog with Chili | 10.00 / 1.50 = 6.66... | 6 |
| Hamburger | 10.00 / 3.00 = 3.33... | 3 |
| Chicken Sandwich | 10.00 / 2.75 = 3.63... | 3 |

The program calculates each purchasing option independently. It does not combine different menu items into a single purchase or subtract the cost of one item before calculating another.

### 4.6 Displaying the Results

```c
printf("With $%.2lf, you could buy" "\n", moneyAmount);
printf("  %d Hot Dogs w/ Chili, or" "\n", hotDogNum);
printf("  %d Hamburgers, or" "\n", hamburgerNum);
printf("  %d Chicken Sandwiches" "\n", chickenSandwichNum);

printf("\n");
```

The output stage displays the amount of money entered by the user and the maximum affordable quantity of each menu item.

The program uses the following format specifiers:

| Format Specifier | Purpose |
|---|---|
| `%.2lf` | Displays the available monetary amount with two decimal places. |
| `%d` | Displays the calculated quantity as a whole number. |
| `\n` | Moves the cursor to the next line. |

The word `or` separates the purchasing options, indicating that each quantity represents an independent choice based on the same available monetary amount.

### 4.7 Program Termination

```c
return 0;
```

After displaying the purchasing options, the program returns `0` from `main()`.

This indicates that the program has completed normal execution.

## 5. Operators Used

The program primarily uses arithmetic and assignment operators.

### 5.1 Arithmetic Operators

| Operator | Name | Purpose |
|---|---|---|
| `/` | Division | Divides the available money by each menu item's price to determine the affordable quantity. |

### 5.2 Assignment Operators

| Operator | Name | Purpose |
|---|---|---|
| `=` | Assignment | Assigns initial values to variables and stores the results of the purchasing calculations. |

### 5.3 Type Conversion

The program also demonstrates implicit type conversion.

For example:

```c
hotDogNum = moneyAmount / HOTDOG_PRICE;
```

Both operands in the division are `double` values, so the calculation produces a floating-point result.

The result is then assigned to an `int` variable.

When a floating-point value is converted to an integer, its fractional portion is discarded.

This produces the maximum whole-number quantity that can be purchased with the available amount, assuming valid nonnegative monetary input.

## 6. Program Execution Sequence

The program follows a sequential input-processing-output structure.

| Step | Operation | Description |
|---:|---|---|
| 1 | Program Start | Execution begins in `main()`. |
| 2 | Variable Declaration | Declares the three integer quantity variables and the monetary input variable. |
| 3 | Constant Declaration | Defines the fixed prices for the three menu items. |
| 4 | Menu Display | Displays the fast-food menu and item prices. |
| 5 | Input Prompt | Asks the user how much money they have available. |
| 6 | Input Collection | Reads the monetary amount using `scanf()`. |
| 7 | Hot Dog Calculation | Divides the available money by the hot dog price. |
| 8 | Hamburger Calculation | Divides the available money by the hamburger price. |
| 9 | Chicken Sandwich Calculation | Divides the available money by the chicken sandwich price. |
| 10 | Output Heading | Displays the amount of money entered by the user. |
| 11 | Display Hot Dog Quantity | Displays the maximum number of hot dogs the user can afford. |
| 12 | Display Hamburger Quantity | Displays the maximum number of hamburgers the user can afford. |
| 13 | Display Chicken Sandwich Quantity | Displays the maximum number of chicken sandwiches the user can afford. |
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
              | Declare and initialize   |
              | integer quantity vars    |
              | moneyAmount = 0.0        |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Declare price constants  |
              | Hot Dog = $1.50          |
              | Hamburger = $3.00         |
              | Chicken = $2.75          |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Display Fast Food Menu   |
              | and item prices          |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Prompt user for money    |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Read moneyAmount         |
              | using scanf("%lf", ...)  |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Calculate hotDogNum      |
              | moneyAmount / 1.50       |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Calculate hamburgerNum   |
              | moneyAmount / 3.00       |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Calculate chickenSandwich|
              | moneyAmount / 2.75       |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Display available money  |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Display hot dog quantity |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Display hamburger        |
              | quantity                 |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Display chicken sandwich|
              | quantity                 |
              +--------------------------+
                           |
                           v
              +--------------------------+
              |       return 0;          |
              +--------------------------+
                           |
                           v
              +--------------------------+
              |       PROGRAM END        |
              +--------------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Variable Declaration and Initialization

The program declares variables using the `int` and `double` data types.

Each variable is initialized before it is used. This establishes its initial value and provides storage for user input and calculation results.

### 8.2 Constants

The program uses the `const` keyword to define fixed menu prices.

These values are established once and reused throughout the program rather than repeating numerical price values in the calculation statements.

### 8.3 User Input

The program uses `scanf()` to accept a monetary amount from the user.

The `%lf` format specifier is used because the input variable is declared as a `double`.

### 8.4 Formatted Output

The program uses `printf()` to display the menu, prices, and calculation results.

Format specifiers control how integer and floating-point values are presented.

### 8.5 Arithmetic Operations

The program uses division to determine how many individual menu items can be purchased with the available money.

### 8.6 Assignment Statements

The assignment operator stores the results of the calculations in their corresponding integer variables.

### 8.7 Implicit Type Conversion

The program demonstrates conversion from a floating-point result to an integer when assigning the calculated quantity to an `int` variable.

The fractional portion is discarded, leaving a whole-number quantity.

### 8.8 Sequential Execution

The program executes its statements in order without using loops, conditional statements, or user-defined functions.

The menu is displayed first, followed by input collection, calculations, and output.

### 8.9 Named Constants and Maintainability

Using descriptive constant names such as `HOTDOG_PRICE` and `HAMBURGER_PRICE` makes the program easier to understand.

It also simplifies future maintenance because menu prices can be updated by changing their declarations.

## 9. Program Characteristics and Limitations

| Characteristic | Description |
|---|---|
| Input Method | Console input using `scanf()`. |
| Input Data Type | `double`. |
| Number of Menu Items | Three. |
| Hot Dog Price | $1.50. |
| Hamburger Price | $3.00. |
| Chicken Sandwich Price | $2.75. |
| Quantity Data Type | `int`. |
| Calculation Method | Available money divided by individual menu prices. |
| Output Method | Console output using `printf()`. |
| Program Structure | All operations are contained in `main()`. |
| Control Structures | Sequential execution; no loops or conditional statements. |
| Program Termination | Returns `0` from `main()`. |

### 9.1 Independent Purchasing Calculations

Each menu item is calculated independently using the full amount entered by the user.

The program does not calculate a combined purchase containing multiple types of food.

For example, if the user has `$10.00`, the program reports how many hot dogs, hamburgers, or chicken sandwiches they could purchase individually.

It does not determine how many items of different types could be purchased together.

### 9.2 Whole-Number Quantities

The quantity variables use the `int` data type.

This ensures that the displayed purchasing quantities are whole numbers. Fractional quantities are discarded during the conversion from `double` to `int`.

### 9.3 No Input Validation

The current implementation does not validate the user's monetary input.

It assumes that the user enters a valid numerical amount.

Negative values and nonnumeric input are not handled through dedicated validation logic.

### 9.4 Fixed Menu Prices

The menu prices are defined as constants.

The program does not provide an option to change menu prices during execution.

### 9.5 No Tax or Additional Charges

The calculations use only the listed menu prices.

The program does not account for sales tax, service charges, discounts, or other additional costs.

### 9.6 No Purchase Selection

The program does not allow the user to select an item or complete an actual purchase.

It only calculates and displays the maximum affordable quantity of each individual menu item.

## 10. Overall Summary

The **How Many** program demonstrates fundamental C programming concepts by calculating how many fast-food menu items a user can afford based on an available monetary amount.

The program begins by declaring and initializing its variables and defining three constant menu prices. It displays the menu, prompts the user to enter an amount of money, and stores that input in a `double` variable.

The processing stage uses three arithmetic assignment statements to divide the available money by the individual menu prices. The results are stored in integer variables, which retain only whole-number quantities.

Finally, the program displays the amount of money entered and the maximum number of hot dogs, hamburgers, or chicken sandwiches the user could independently purchase.

The primary programming concepts demonstrated include variable declaration, initialization, constants, data types, user input, formatted output, arithmetic operations, assignment statements, implicit type conversion, and sequential program execution.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, including variable declarations, constants, data types, input/output operations, arithmetic calculations, assignment statements, and type conversion.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.