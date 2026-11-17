# Progs 2, 3, 4 – C Programming Project Documentation

**Programmer:** Brian Lorick  
**Program Name:** Progs 2, 3, 4  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio 2019  
**Course Topic:** Chapter 6 – Functions  
**Original Date:** April 8, 2024  
**Source File:** `Progs 2, 3, 4.c`

---

## 1. Program Overview

The **Progs 2, 3, 4** program is a menu-driven C application that combines three separate programming exercises into one executable program. It allows the user to select and execute individual operations through a console-based menu.

The application demonstrates modular programming by separating each exercise into its own user-defined function. A central menu controls which function executes based on the user's selection.

The program provides three options:

1. **Split Double** – Accepts a decimal number and separates its integer and fractional portions.
2. **Minutes, Hours, Days** – Accepts a number of seconds and calculates its equivalent in minutes, hours, and days.
3. **Calories Burned** – Calculates calories burned over different running durations using iterative loop structures.

The application also provides an exit option. The menu continues displaying until the user enters `-1`.

The program demonstrates fundamental C programming concepts, including function prototypes, function calls, parameter passing, return values, `switch` statements, `do-while` loops, `for` loops, arithmetic operations, type casting, input/output operations, and variable scope.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive | Purpose |
|---|---|
| `#define _CRT_SECURE_NO_WARNINGS` | Disables Microsoft Visual Studio warnings associated with certain standard C functions, including `scanf()`. |
| `#include <stdio.h>` | Includes the Standard Input/Output library, providing access to `printf()` and `scanf()`. |

### 2.2 Standard Library Functions

| Function | Purpose |
|---|---|
| `printf()` | Displays the menu, prompts, calculations, results, and error messages. |
| `scanf()` | Accepts user input and stores the entered values in variables. |

The program uses `<stdio.h>` for all console input and output operations.

### 2.3 User-Defined Functions

The program contains five user-defined functions.

| Function | Return Type | Parameters | Purpose |
|---|---|---|---|
| `main()` | `int` | None | Controls the main menu loop and overall program execution. |
| `displayMenu()` | `int` | None | Displays the menu, collects the user's selection, and returns the choice. |
| `executeChoice()` | `void` | `int choice` | Uses a `switch` statement to execute the selected exercise. |
| `splitDouble()` | `void` | None | Separates a decimal number into integer and fractional portions. |
| `minutesHoursDays()` | `void` | None | Converts an entered number of seconds into minutes, hours, and days. |
| `caloriesBurned()` | `void` | None | Calculates and displays calories burned using iterative loops. |

## 3. Variables and Data Structures

### 3.1 Main Function Variables

| Variable | Data Type | Purpose |
|---|---|---|
| `choice` | `int` | Stores the menu option selected by the user. |

The `choice` variable controls the application's menu selection and determines whether the program continues or terminates.

### 3.2 Display Menu Variables

| Variable | Data Type | Purpose |
|---|---|---|
| `choice` | `int` | Stores the user's menu selection before returning it to `main()`. |

The `displayMenu()` function maintains its own local `choice` variable. Its value is returned to the calling function.

### 3.3 Execute Choice Parameters

| Parameter | Data Type | Purpose |
|---|---|---|
| `choice` | `int` | Receives the menu selection passed from `main()` and determines which function to execute. |

### 3.4 Split Double Variables

| Variable | Data Type | Purpose |
|---|---|---|
| `number` | `double` | Stores the decimal number entered by the user. |

The program uses `double` to preserve the fractional portion of the entered number.

The integer portion is obtained through explicit type casting, while the fractional portion is calculated by subtracting the integer portion from the original value.

### 3.5 Minutes, Hours, Days Variables

| Variable | Data Type | Purpose |
|---|---|---|
| `seconds` | `int` | Stores the number of seconds entered by the user. |
| `minutes` | `double` | Stores the converted number of minutes. |
| `hours` | `double` | Stores the converted number of hours. |
| `days` | `double` | Stores the converted number of days. |

The conversion variables use `double` to preserve fractional results during the calculations.

### 3.6 Calories Burned Variables

| Variable | Data Type | Purpose |
|---|---|---|
| `i` | `int` | Controls the running-duration iteration in the loop structures. |

The variable `i` represents the number of minutes spent running.

It begins at 5 and increases by 3 during each iteration until the value exceeds 20.

The program declares `i` separately within the different loop sections. The `for` loop declarations have their own loop scope, while the variable used by the `do-while` loop is declared within the function.

### 3.7 Data Structures

The program does not use arrays, structures, linked lists, or dynamically allocated memory.

Instead, it uses individual variables, function parameters, and local variables within each function.

## 4. Processing Logic and Statements

### 4.1 Main Function – Program Control

```c
int main()
{
    int choice;

    do
    {
        choice = displayMenu();

        if (choice > 0 && choice < 5)
        {
            executeChoice(choice);
        }
        else if (choice != -1)
        {
            printf("Invalid choice. Please enter a valid menu option.\n\n");
        }
    }
    while (choice != -1);

    printf("Good bye!\n");
    printf("\n");

    return 0;
}
```

The `main()` function controls the application's overall execution.

It uses a `do-while` loop to repeatedly display the menu and process the user's selection.

The loop executes the menu at least once before evaluating its continuation condition.

**Program execution:**

1. Calls `displayMenu()` to display the menu and collect the user's selection.
2. Stores the returned selection in `choice`.
3. Uses an `if` statement to determine whether the selection is within the accepted numerical range.
4. Calls `executeChoice()` when the selection is between 1 and 4.
5. Displays an error message for invalid selections other than `-1`.
6. Repeats the menu while `choice` is not equal to `-1`.
7. Displays the exit message when the user chooses to quit.

The actual menu only provides options 2, 3, and 4. Although the numerical validation accepts the range from 1 through 4, selecting option 1 does not execute an exercise because no corresponding `case 1` exists in `executeChoice()`.

### 4.2 Display Menu Function – `displayMenu()`

```c
int displayMenu()
{
    int choice;

    printf("Progs 2, 3, 4 Menu\n");
    printf("------------------------\n");
    printf("2 - Split Double\n");
    printf("3 - Minutes, Hours, Days\n");
    printf("4 - Calories Burned\n");
    printf("\n");
    printf("Enter a choice (-1 to quit): ");

    scanf("%d", &choice);

    printf("\n");

    return choice;
}
```

The `displayMenu()` function displays the available program options and collects the user's selection.

It returns an integer representing the selected menu option.

**Menu options:**

| Selection | Program | Function Called |
|---:|---|---|
| 2 | Split Double | `splitDouble()` |
| 3 | Minutes, Hours, Days | `minutesHoursDays()` |
| 4 | Calories Burned | `caloriesBurned()` |
| -1 | Exit | Returns control to `main()` for termination. |

The function uses `scanf()` with `%d` to read an integer value.

The `return choice;` statement sends the selection back to `main()`.

### 4.3 Execute Choice Function – `executeChoice()`

```c
void executeChoice(int choice)
{
    switch (choice)
    {
    case 2:
        splitDouble();
        break;

    case 3:
        minutesHoursDays();
        break;

    case 4:
        caloriesBurned();
        break;
    }
}
```

The `executeChoice()` function receives the selected menu option through its `choice` parameter.

It uses a `switch` statement to determine which program function should execute.

Each `case` represents a possible menu selection.

| Case | Function Executed | Description |
|---|---|---|
| `case 2` | `splitDouble()` | Separates a decimal number into two portions. |
| `case 3` | `minutesHoursDays()` | Performs time conversions. |
| `case 4` | `caloriesBurned()` | Calculates calories burned using loops. |

The `break` statements terminate the selected case and prevent execution from falling through into another case.

The function uses `void` because it performs an operation without returning a value.

### 4.4 Program 2 – Split Double

#### 4.4.1 Function Overview

```c
void splitDouble()
{
    double number;

    printf("Enter a number that includes a decimal point: ");
    scanf("%lf", &number);

    printf("The integer part of %.6lf is %d.\n",
           number, (int)number);

    printf("The decimal part of %.6lf is %.6lf.\n\n",
           number, number - (int)number);
}
```

The `splitDouble()` function accepts a decimal number from the user and separates it into its integer and fractional portions.

The program uses a `double` variable to store the entered number.

#### 4.4.2 Input Collection

```c
double number;

printf("Enter a number that includes a decimal point: ");
scanf("%lf", &number);
```

The program prompts the user to enter a number containing a decimal point.

The `%lf` format specifier instructs `scanf()` to read a `double` value.

The address-of operator (`&`) supplies the memory address of `number` so that the entered value can be stored.

#### 4.4.3 Extracting the Integer Portion

```c
(int)number
```

The program uses explicit type casting to convert the `double` value into an integer.

When a floating-point number is converted to an integer, its fractional portion is discarded.

For example:

```text
Original number:  125.75
Integer portion:  125
```

The integer portion is displayed using `%d`.

#### 4.4.4 Extracting the Fractional Portion

```c
number - (int)number
```

The program calculates the fractional portion by subtracting the integer portion from the original decimal value.

The mathematical operation is:

\[
\text{Fractional Portion} =
\text{Original Number} - \text{Integer Portion}
\]

Example:

\[
125.75 - 125 = 0.75
\]

The result is displayed using `%.6lf`, which formats the fractional value to six decimal places.

**Important:** The operation extracts the signed fractional remainder rather than an absolute decimal component. For negative inputs, the result can be negative.

### 4.5 Program 3 – Minutes, Hours, Days

#### 4.5.1 Function Overview

```c
void minutesHoursDays()
{
    int seconds;

    printf("Enter the number of seconds: ");
    scanf("%d", &seconds);

    if (seconds <= 0)
    {
        printf("Invalid input. Number of seconds must be greater than 0.\n\n");
        return;
    }

    double minutes = seconds / 60.0;
    double hours = minutes / 60.0;
    double days = hours / 24.0;

    printf("The number of seconds you entered, %d, is %.2lf minutes.\n",
           seconds, minutes);

    printf("The number of seconds you entered, %d, is %.2lf hours.\n\n",
           seconds, hours);
}
```

The `minutesHoursDays()` function accepts a number of seconds and calculates its equivalent in minutes, hours, and days.

The function validates the input before performing the calculations.

#### 4.5.2 Input Collection

```c
int seconds;

printf("Enter the number of seconds: ");
scanf("%d", &seconds);
```

The program prompts the user to enter a number of seconds.

The `%d` format specifier reads an integer and stores it in `seconds`.

#### 4.5.3 Input Validation

```c
if (seconds <= 0)
{
    printf("Invalid input. Number of seconds must be greater than 0.\n\n");
    return;
}
```

The program uses an `if` statement to verify that the entered number of seconds is greater than zero.

If the value is zero or negative:

1. An error message is displayed.
2. The `return` statement exits `minutesHoursDays()`.
3. The program returns control to the menu loop in `main()`.

The `return` statement does not terminate the entire application. It only exits the currently executing function.

#### 4.5.4 Converting Seconds to Minutes

```c
double minutes = seconds / 60.0;
```

The program divides the entered number of seconds by 60 to calculate the equivalent number of minutes.

\[
\text{Minutes} = \frac{\text{Seconds}}{60}
\]

The use of `60.0` ensures floating-point division.

#### 4.5.5 Converting Minutes to Hours

```c
double hours = minutes / 60.0;
```

The program divides the calculated minutes by 60 to determine the equivalent number of hours.

\[
\text{Hours} = \frac{\text{Minutes}}{60}
\]

The result is stored in the `hours` variable.

#### 4.5.6 Converting Hours to Days

```c
double days = hours / 24.0;
```

The program divides the calculated hours by 24 to determine the equivalent number of days.

\[
\text{Days} = \frac{\text{Hours}}{24}
\]

The result is stored in `days`.

**Source-code observation:** Although the program calculates the value of `days`, it does not display that value. The current output statements display only minutes and hours.

#### 4.5.7 Displaying the Results

```c
printf("The number of seconds you entered, %d, is %.2lf minutes.\n",
       seconds, minutes);

printf("The number of seconds you entered, %d, is %.2lf hours.\n\n",
       seconds, hours);
```

The program displays the original number of seconds and its corresponding minute and hour conversions.

The `%.2lf` format specifier displays floating-point values to two decimal places.

### 4.6 Program 4 – Calories Burned

#### 4.6.1 Function Overview

```c
void caloriesBurned()
{
    printf("You burn 3.9 calories every minute you run.\n");
    printf("This shows how many calories you burn if you ran for 5 to 20 minutes.\n\n");

    printf("        Minutes Calories\n");

    // Iterative calculations
}
```

The `caloriesBurned()` function calculates the number of calories burned based on a running rate of 3.9 calories per minute.

It displays the results for running durations beginning at 5 minutes and increasing in increments of 3 minutes.

The program demonstrates three loop structures:

1. A `for` loop labeled as a `while` loop.
2. A `do-while` loop.
3. A second `for` loop.

Each section calculates calories using the same formula.

\[
\text{Calories Burned} = 3.9 \times \text{Minutes}
\]

#### 4.6.2 First Iteration Section – `for` Loop

```c
printf("Using a while loop\n");

for (int i = 5; i <= 20; i += 3)
{
    printf("%12d %8.2f\n", i, 3.9 * i);
}
```

The first iteration section is labeled `Using a while loop`, but the actual source code uses a `for` loop.

The loop begins at 5 minutes and continues while `i` is less than or equal to 20.

The update expression:

```c
i += 3
```

Increases the running duration by three minutes during each iteration.

The resulting values are:

```text
5, 8, 11, 14, 17, 20
```

For each value, the program multiplies the number of minutes by 3.9 to calculate calories burned.

#### 4.6.3 Second Iteration Section – `do-while` Loop

```c
printf("Using a do-while loop\n");

int i = 5;

do
{
    printf("%12d %8.2f\n", i, 3.9 * i);
    i += 3;
}
while (i <= 20);
```

The second section demonstrates a `do-while` loop.

Unlike a standard `while` loop, a `do-while` loop evaluates its continuation condition after executing the loop body.

The variable `i` is initialized to 5 before the loop begins.

During each iteration:

1. The current running duration is displayed.
2. Calories burned are calculated using `3.9 * i`.
3. The variable `i` increases by three.
4. The condition `i <= 20` is evaluated.

The loop continues until the condition becomes false.

Because the condition is evaluated after the loop body, the `do-while` loop always executes at least once.

#### 4.6.4 Third Iteration Section – `for` Loop

```c
printf("Using a for loop\n");

for (int i = 5; i <= 20; i += 3)
{
    printf("%12d %8.2f\n", i, 3.9 * i);
}
```

The third section demonstrates another `for` loop.

It uses the same initialization, condition, and increment values as the first loop.

The loop begins at 5 minutes, increases by three minutes, and stops after processing 20 minutes.

This section produces the same numerical results as the previous two iteration sections.

#### 4.6.5 Calories Calculation

All three loop sections use the same calculation:

```c
3.9 * i
```

The variable `i` represents the number of minutes spent running.

The multiplication calculates the calories burned at a rate of 3.9 calories per minute.

| Running Time | Calculation | Calories Burned |
|---:|---:|---:|
| 5 minutes | 3.9 × 5 | 19.50 |
| 8 minutes | 3.9 × 8 | 31.20 |
| 11 minutes | 3.9 × 11 | 42.90 |
| 14 minutes | 3.9 × 14 | 54.60 |
| 17 minutes | 3.9 × 17 | 66.30 |
| 20 minutes | 3.9 × 20 | 78.00 |

#### 4.6.6 Formatted Output

```c
printf("%12d %8.2f\n", i, 3.9 * i);
```

The program uses formatted output to align the minutes and calories into two columns.

| Format Specifier | Purpose |
|---|---|
| `%12d` | Displays the integer value in a field with a width of 12 characters. |
| `%8.2f` | Displays the floating-point calorie value in a field with a width of 8 characters and two decimal places. |
| `\n` | Moves to the next output line. |

The field widths create spacing between the columns and improve table readability.

## 5. Operators Used

The program uses relational, logical, arithmetic, assignment, increment, and type-conversion operations.

### 5.1 Relational Operators

| Operator | Name | Purpose |
|---|---|---|
| `>` | Greater than | Determines whether a menu selection falls within the accepted numerical range. |
| `<` | Less than | Used with the menu selection condition. |
| `!=` | Not equal to | Determines whether the user has selected the exit option. |
| `<=` | Less than or equal to | Validates seconds and controls loop termination conditions. |

### 5.2 Logical Operators

| Operator | Name | Purpose |
|---|---|---|
| `&&` | Logical AND | Requires both menu-selection conditions to be true before executing a selection. |

Example:

```c
choice > 0 && choice < 5
```

Both comparisons must evaluate to true for the program to call `executeChoice()`.

### 5.3 Arithmetic Operators

| Operator | Name | Purpose |
|---|---|---|
| `+` | Addition | Adds no separate values directly in the calculations; used indirectly through compound assignment where applicable. |
| `-` | Subtraction | Calculates the fractional portion of a decimal number. |
| `*` | Multiplication | Calculates calories burned by multiplying minutes by 3.9. |
| `/` | Division | Converts seconds into minutes, hours, and days. |

### 5.4 Assignment Operators

| Operator | Name | Purpose |
|---|---|---|
| `=` | Assignment | Assigns input values, initializes variables, and stores calculation results. |
| `+=` | Addition assignment | Increases the running-duration counter by three minutes during the calorie loops. |

### 5.5 Increment and Type Conversion

| Expression | Purpose |
|---|---|
| `(int)number` | Converts the decimal number to an integer, discarding its fractional portion. |
| `i += 3` | Adds three to the current running-duration value. |

## 6. Program Execution Sequence

The program follows a menu-driven execution structure.

| Step | Operation | Description |
|---:|---|---|
| 1 | Program Start | Execution begins in `main()`. |
| 2 | Variable Declaration | Declares the menu selection variable `choice`. |
| 3 | Display Menu | Calls `displayMenu()` to present the available exercises. |
| 4 | Collect Selection | Reads the user's menu choice and returns it to `main()`. |
| 5 | Validate Selection | Checks whether the selection is between 1 and 4. |
| 6 | Execute Selection | Calls `executeChoice()` when the selection is within the accepted numerical range. |
| 7 | Switch Evaluation | Uses a `switch` statement to identify the selected exercise. |
| 8 | Program 2 | Calls `splitDouble()` when the user selects option 2. |
| 9 | Program 3 | Calls `minutesHoursDays()` when the user selects option 3. |
| 10 | Program 4 | Calls `caloriesBurned()` when the user selects option 4. |
| 11 | Invalid Selection | Displays an error message for invalid selections other than `-1`. |
| 12 | Menu Repetition | Repeats the menu while the selection is not `-1`. |
| 13 | Exit Message | Displays `Good bye!` when the user chooses to quit. |
| 14 | Program Termination | Returns `0` and ends execution. |

## 7. Text-Based Program Flowchart

```text
                    +-------------------------+
                    |      PROGRAM START      |
                    +-------------------------+
                               |
                               v
                    +-------------------------+
                    |         main()          |
                    +-------------------------+
                               |
                               v
                    +-------------------------+
                    | Initialize do-while     |
                    | menu control loop       |
                    +-------------------------+
                               |
                               v
                    +-------------------------+
                    | Call displayMenu()      |
                    +-------------------------+
                               |
                               v
                    +-------------------------+
                    | Display menu options    |
                    | 2, 3, 4, and -1         |
                    +-------------------------+
                               |
                               v
                    +-------------------------+
                    | Read user selection     |
                    | Return choice           |
                    +-------------------------+
                               |
                               v
                    +-------------------------+
                    | choice > 0 AND          |
                    | choice < 5?             |
                    +-------------------------+
                         |              |
                        YES             NO
                         |              |
                         v              v
              +-------------------+  +----------------------+
              | Call              |  | Is choice != -1?     |
              | executeChoice()   |  +----------------------+
              +-------------------+       |            |
                         |               YES           NO
                         v                |            |
              +-------------------+       v            |
              | Evaluate switch   | +----------------+ |
              | (choice)          | | Display invalid| |
              +-------------------+ | choice message | |
                 |        |     |    +----------------+ |
                 |        |     |            |          |
                 v        v     v            |          |
          +---------+ +---------+ +---------+ |          |
          | Case 2  | | Case 3  | | Case 4  | |          |
          +---------+ +---------+ +---------+ |          |
              |          |           |        |          |
              v          v           v        |          |
        +----------+ +----------+ +----------+ |          |
        | Split    | | Minutes, | | Calories | |          |
        | Double   | | Hours,   | | Burned   | |          |
        +----------+ | Days     | +----------+ |          |
                     +----------+              |          |
              |          |           |        |          |
              +----------+-----------+--------+          |
                         |                                |
                         v                                |
              +-------------------------+                 |
              | Evaluate while         |<----------------+
              | choice != -1           |
              +-------------------------+
                         |
                 +-------+-------+
                 |               |
                YES              NO
                 |               |
                 v               v
        +----------------+ +----------------------+
        | Display menu   | | Display "Good bye!"  |
        | again          | +----------------------+
        +----------------+          |
                 |                  v
                 +--------> +----------------------+
                            |      return 0;       |
                            +----------------------+
                                      |
                                      v
                            +----------------------+
                            |      PROGRAM END     |
                            +----------------------+
```

### 7.1 Program 2 – Split Double Flowchart

```text
             +-------------------------+
             | Call splitDouble()      |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Declare double number   |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Prompt for decimal      |
             | number                  |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Read number using scanf |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Convert number to int   |
             | (int)number             |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Display integer portion |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Calculate fractional    |
             | portion:                |
             | number - (int)number    |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Display fractional      |
             | portion                 |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Return to main menu     |
             +-------------------------+
```

### 7.2 Program 3 – Minutes, Hours, Days Flowchart

```text
             +-------------------------+
             | Call minutesHoursDays() |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Declare seconds         |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Prompt for seconds      |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Read seconds            |
             +-------------------------+
                         |
                         v
                  +--------------+
                  | seconds <= 0?|
                  +--------------+
                    |          |
                   YES         NO
                    |          |
                    v          v
           +----------------+  +----------------------+
           | Display error  |  | Calculate minutes    |
           | Return from    |  | seconds / 60.0       |
           | function       |  +----------------------+
           +----------------+             |
                    |                     v
                    |          +----------------------+
                    |          | Calculate hours      |
                    |          | minutes / 60.0       |
                    |          +----------------------+
                    |                     |
                    |                     v
                    |          +----------------------+
                    |          | Calculate days       |
                    |          | hours / 24.0         |
                    |          +----------------------+
                    |                     |
                    |                     v
                    |          +----------------------+
                    |          | Display minutes      |
                    |          +----------------------+
                    |                     |
                    |                     v
                    |          +----------------------+
                    |          | Display hours        |
                    |          +----------------------+
                    |                     |
                    +---------------------+
                                          |
                                          v
                              +----------------------+
                              | Return to main menu  |
                              +----------------------+
```

### 7.3 Program 4 – Calories Burned Flowchart

```text
             +-------------------------+
             | Call caloriesBurned()   |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Display calorie rate   |
             | 3.9 calories per minute|
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Display table headings |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | First section:          |
             | for loop labeled        |
             | "while loop"            |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Initialize i = 5        |
             +-------------------------+
                         |
                         v
                  +--------------+
                  | i <= 20?     |
                  +--------------+
                    |          |
                   YES         NO
                    |          |
                    v          |
             +----------------+|
             | Calculate       ||
             | calories = 3.9*i||
             +----------------+|
                    |          |
                    v          |
             +----------------+|
             | Display result ||
             +----------------+|
                    |          |
                    v          |
             +----------------+|
             | i += 3         |+
             +----------------+
                    |
                    +----> Repeat condition
                              |
                              v
             +-------------------------+
             | Second section:         |
             | do-while loop           |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Initialize i = 5        |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Calculate calories      |
             | Display result          |
             +-------------------------+
                         |
                         v
             +-------------------------+
             | Increment i by 3        |
             +-------------------------+
                         |
                         v
                  +--------------+
                  | i <= 20?     |
                  +--------------+
                    |          |
                   YES         NO
                    |          |
                    +----+     |
                         |     |
                         v     v
                  Repeat    Third section
                            for loop
                               |
                               v
                    +----------------------+
                    | Repeat 5-to-20       |
                    | minute calculation   |
                    +----------------------+
                               |
                               v
                    +----------------------+
                    | Return to main menu  |
                    +----------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Modular Programming

The program separates its operations into individual functions.

Each function has a specific responsibility, allowing the main function to coordinate the application without containing all of the individual exercise logic.

### 8.2 Function Prototypes

The program declares function prototypes before `main()`.

```c
int displayMenu();
void executeChoice(int choice);
void splitDouble();
void minutesHoursDays();
void caloriesBurned();
```

These declarations inform the compiler of the functions' names, return types, and parameters before they are called.

### 8.3 Function Calls and Parameter Passing

The program demonstrates calling functions from other functions.

The `executeChoice()` function receives the menu selection as an integer parameter.

This demonstrates how information can be passed between functions.

### 8.4 Return Values

The `displayMenu()` function returns an integer representing the user's selection.

The `main()` function receives and stores that value in `choice`.

The other exercise functions use `void` because they perform their operations without returning a value.

### 8.5 Do-While Loops

The main menu uses a `do-while` loop to ensure the menu displays at least once.

The loop continues until the user enters `-1`.

The calories exercise also uses a `do-while` loop to calculate calories burned at different running durations.

### 8.6 For Loops

The calorie calculations demonstrate `for` loops.

The loop initialization, condition, and update expressions control the running-duration values.

### 8.7 Switch Statements

The `switch` statement in `executeChoice()` selects which exercise function to execute based on the user's menu selection.

Each `case` corresponds to an available exercise.

### 8.8 If/Else Decision Structures

The program uses `if` and `else if` statements to validate menu selections and determine whether the user has entered an acceptable option.

The `minutesHoursDays()` function also uses an `if` statement to validate the entered number of seconds.

### 8.9 Type Casting

The `splitDouble()` function uses explicit type casting to convert a floating-point number into an integer.

This demonstrates how data types can be converted to perform different calculations.

### 8.10 Arithmetic Operations

The program uses addition, subtraction, multiplication, and division to perform its calculations.

These operations are demonstrated across the three individual exercises.

### 8.11 Variable Scope

The program demonstrates local variable scope.

Variables declared inside a function are generally accessible only within that function or their containing block.

The `i` variables used by the separate calorie loop sections demonstrate how variables can be declared independently within different scopes.

### 8.12 Input Validation

The `minutesHoursDays()` function checks whether the entered number of seconds is positive.

If the value is invalid, the function displays an error message and exits without performing the conversions.

### 8.13 Iterative Calculation

The `caloriesBurned()` function demonstrates how a loop can repeat a mathematical calculation using different input values.

The same calorie formula is applied to each running duration.

## 9. Program Characteristics and Limitations

| Characteristic | Description |
|---|---|
| Application Type | Menu-driven console application. |
| Programming Language | C. |
| Number of Exercises | Three. |
| Menu Options | 2, 3, and 4. |
| Exit Option | `-1`. |
| Main Control Structure | `do-while` loop. |
| Function Selection | `switch` statement. |
| Input Method | `scanf()`. |
| Output Method | `printf()`. |
| User-Defined Functions | Five, excluding `main()`. |
| Iteration Structures | `for` and `do-while` loops. |
| Decision Structures | `if`, `else if`, and `switch`. |
| Program Termination | Returns `0` from `main()`. |

### 9.1 Menu Selection Limitation

The main function checks whether the menu selection is greater than zero and less than five.

However, the actual menu only contains options 2, 3, and 4.

Selecting `1` passes the numerical validation but does not match any `switch` case. The program therefore returns to the menu without executing an exercise.

### 9.2 Input Validation Limitations

The program uses `scanf()` to collect menu selections and numerical values.

It does not check the return values of `scanf()` to determine whether the user entered valid numerical data.

Nonnumeric input is not handled through a dedicated error-recovery mechanism.

### 9.3 Split Double Limitations

The `splitDouble()` function accepts a decimal value but does not validate the input.

The integer portion is obtained through type casting, which truncates the fractional portion toward zero.

For negative values, the fractional portion may also be negative.

### 9.4 Minutes, Hours, Days Output Limitation

The `minutesHoursDays()` function calculates three conversions:

- Minutes
- Hours
- Days

However, the source code only displays minutes and hours.

The `days` variable is calculated but is not used in an output statement.

### 9.5 Calories Loop Label Discrepancy

The first calorie calculation section displays the heading:

```text
Using a while loop
```

However, the actual source code uses a `for` loop.

The program therefore contains two `for` loops and one `do-while` loop, rather than one `while`, one `do-while`, and one `for` loop.

### 9.6 Repeated Calorie Calculations

The three calorie sections perform the same calculation using the same running durations.

The repetition appears intentional for demonstrating different loop structures, but the first section's label does not match its implementation.

### 9.7 Fixed Running Duration

The calorie calculation begins at 5 minutes and ends at 20 minutes, increasing by three minutes each iteration.

These values are hardcoded into the loop structures and cannot be changed through user input.

### 9.8 Function Return Behavior

The exercise functions use `void` return types.

When an exercise finishes, execution returns to the main menu loop rather than terminating the application.

The `return` statement inside `minutesHoursDays()` exits only that function.

## 10. Overall Summary

The **Progs 2, 3, 4** application demonstrates how multiple C programming exercises can be organized into a single menu-driven program using modular programming and user-defined functions.

The application begins in `main()`, where a `do-while` loop repeatedly calls `displayMenu()` to collect the user's selection. The selected option is passed to `executeChoice()`, which uses a `switch` statement to call the appropriate exercise function.

The first exercise, `splitDouble()`, demonstrates floating-point input, explicit type casting, and arithmetic subtraction to separate the integer and fractional portions of a decimal number.

The second exercise, `minutesHoursDays()`, demonstrates input validation and sequential time conversions using floating-point division. It calculates minutes, hours, and days, although the current implementation only displays the minute and hour results.

The third exercise, `caloriesBurned()`, demonstrates iterative calculations using `for` and `do-while` loops. It calculates calories burned at 3.9 calories per minute for running durations between 5 and 20 minutes.

The primary programming concepts demonstrated include modular programming, function prototypes, function calls, parameters, return values, variable scope, `switch` statements, conditional statements, `do-while` loops, `for` loops, arithmetic operations, type casting, input validation, and formatted console output.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, including modular programming, functions, function prototypes, parameter passing, decision-making structures, loops, arithmetic operations, type casting, variable scope, and console input/output.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.