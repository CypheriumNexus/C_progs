# MPH – C Programming Project Documentation

**Programmer:** Brian Lorick\
**Program Name:** MPH\
**Programming Language:** C\
**Development Environment:** Microsoft Visual Studio\
**Course Topic:** Chapter 2 – Fundamentals\
**Original Date:** January 26, 2024\
**Source File:** `MPH.c`

---

## 1. Program Overview

The **MPH** program is a C application that calculates a vehicle's average speed in miles per hour (MPH) based on the distance traveled and the amount of time required to travel that distance.

The program prompts the user to enter two values:

1. The number of miles driven.
2. The number of minutes it took to drive that distance.

Using these values, the program converts the travel time from minutes to hours and calculates the average speed using the rate formula:

[\
\text{Rate} = \frac{\text{Distance}}{\text{Time}}\
]

The program then displays the distance traveled, the elapsed time, and the calculated speed in miles per hour.

The program demonstrates fundamental C programming concepts, including variable declarations, constants, user input, arithmetic operations, explicit type casting, assignment statements, and formatted console output.

The program follows three primary stages:

1. **Input** – Collects the distance traveled and the time required to travel that distance.
2. **Processing** – Converts minutes into hours and calculates the average speed.
3. **Output** – Displays the trip information and calculated speed in MPH.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive                         | Purpose                                                                                                      |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| `#define _CRT_SECURE_NO_WARNINGS` | Disables Microsoft Visual Studio warnings associated with certain standard C functions, including `scanf()`. |
| `#include <stdio.h>`              | Includes the Standard Input/Output library, providing access to `printf()` and `scanf()`.                    |

### 2.2 Standard Library Functions

| Function   | Purpose                                                                            |
| ---------- | ---------------------------------------------------------------------------------- |
| `printf()` | Displays input prompts, trip information, and the calculated speed.                |
| `scanf()`  | Accepts user input and stores the entered values in their corresponding variables. |

The program uses `<stdio.h>` for console input and output. No additional libraries or user-defined functions are required.

## 3. Variables and Data Structures

### 3.1 Constant Variable

| Constant           | Data Type   | Value | Purpose                                                                                                     |
| ------------------ | ----------- | ----- | ----------------------------------------------------------------------------------------------------------- |
| `MINUTES_TO_HOURS` | `const int` | `60`  | Defines the number of minutes in one hour and provides the conversion factor used in the speed calculation. |

The declaration:

```
const int MINUTES_TO_HOURS = 60;
```

Creates a constant integer that cannot be reassigned during program execution.

Using a named constant makes the time conversion calculation easier to understand and maintain.

### 3.2 Integer Variables

| Variable       | Data Type | Purpose                                                                  |
| -------------- | --------- | ------------------------------------------------------------------------ |
| `milesPerHour` | `int`     | Stores the calculated average speed in miles per hour as a whole number. |
| `numMinutes`   | `int`     | Stores the number of minutes required to travel the entered distance.    |

The `int` data type is used for the travel time and final MPH result.

The calculated speed is explicitly converted to an integer before being stored in `milesPerHour`.

### 3.3 Floating-Point Variable

| Variable      | Data Type | Purpose                                                         |
| ------------- | --------- | --------------------------------------------------------------- |
| `milesDriven` | `double`  | Stores the distance traveled in miles, allowing decimal values. |

The `double` data type supports fractional distance values, such as `12.5` miles.

It also allows the program to perform floating-point arithmetic during the speed calculation.

### 3.4 Data Structures

The program does not use arrays, structures, pointers, or other aggregate data structures.

It uses three individual variables and one constant to store the information required for the calculation.

## 4. Processing Logic and Statements

### 4.1 Main Function

```
int main(void)
{
    // Constant and Variable Declarations

    // INPUT

    // PROCESS

    // OUTPUT

    return 0;
}
```

The `main()` function is the program's entry point.

All variable declarations, input operations, calculations, and output statements are contained within this function.

The parameter `void` indicates that `main()` does not receive command-line arguments.

The program executes sequentially through the input, processing, and output sections.

### 4.2 Constant and Variable Declarations

```
const int MINUTES_TO_HOURS = 60;
int milesPerHour;
int numMinutes;
double milesDriven;
```

The program begins by declaring its constant and variables.

- `MINUTES_TO_HOURS` establishes the conversion factor of 60 minutes per hour.
- `milesPerHour` stores the final calculated speed.
- `numMinutes` stores the elapsed travel time.
- `milesDriven` stores the distance traveled.

The program uses both integer and floating-point data types to accommodate the different types of numerical values involved in the calculation.

### 4.3 Collecting the Distance

```
printf("Enter the number of miles driven: ");
scanf("%lf", &milesDriven);
```

The first input operation prompts the user to enter the distance traveled in miles.

The `scanf()` function reads the entered value and stores it in `milesDriven`.

The `%lf` format specifier instructs `scanf()` to read a `double` value.

The address-of operator (`&`) provides the memory address of `milesDriven`, allowing `scanf()` to store the input in that variable.

### 4.4 Collecting the Travel Time

```
printf("Enter the number of minutes that it took to drive the %.1lf miles: ", milesDriven);
scanf("%d", &numMinutes);
```

After collecting the distance, the program prompts the user to enter the number of minutes required to travel that distance.

The prompt includes the previously entered mileage value.

The `%.1lf` format specifier displays the distance with one digit after the decimal point.

The second `scanf()` statement reads the travel time as an integer using the `%d` format specifier.

The entered value is stored in `numMinutes`.

### 4.5 Calculating Miles Per Hour

```
milesPerHour = (int)(milesDriven / (numMinutes / (double)MINUTES_TO_HOURS));
```

This statement performs the primary calculation of the program.

It calculates the average speed by dividing the distance traveled by the travel time expressed in hours.

The formula is:

[\
\text{MPH} = \frac{\text{Miles Driven}}{\text{Time in Hours}}\
]

Since the user enters time in minutes, the program must convert the minutes into hours before calculating the speed.

The conversion is:

[\
\text{Hours} = \frac{\text{Minutes}}{60}\
]

The complete calculation is:

[\
\text{MPH} = \frac{\text{Miles Driven}}{\text{Minutes}/60}\
]

The program accomplishes this using the following expression:

```
milesDriven / (numMinutes / (double)MINUTES_TO_HOURS)
```

**Breaking down the calculation:**

1. `numMinutes` contains the travel time in minutes.
2. `(double)MINUTES_TO_HOURS` explicitly converts the constant from an integer to a `double`.
3. `numMinutes / (double)MINUTES_TO_HOURS` converts the travel time into hours using floating-point division.
4. `milesDriven` is divided by the calculated number of hours.
5. The resulting speed is explicitly converted to an integer.
6. The integer result is assigned to `milesPerHour`.

### 4.6 Explicit Type Casting

The program uses two important type conversions.

**First conversion:**

```
(double)MINUTES_TO_HOURS
```

This explicitly converts the integer constant `60` into a `double`.

This is important because it ensures that the division involving `numMinutes` uses floating-point arithmetic rather than integer division.

For example:

```
30 / 60
```

Using integer operands produces `0` because the fractional portion is discarded.

However:

```
30 / (double)60
```

Produces `0.5`, correctly representing half an hour.

**Second conversion:**

```
(int)(milesDriven / (numMinutes / (double)MINUTES_TO_HOURS))
```

The calculated speed is explicitly converted from a floating-point value to an integer.

This means any fractional portion of the calculated MPH is discarded rather than rounded to the nearest whole number.

For example:

```
65.8 MPH becomes 65 MPH
```

### 4.7 Displaying the Results

```
printf("Based on a trip of %.1lf miles that took %d minutes,\n", milesDriven, numMinutes);

printf("your speed was %d MPH.\n", milesPerHour);
```

After calculating the speed, the program displays the trip information and the resulting average speed.

The first `printf()` statement displays:

- The distance traveled.
- The number of minutes required to travel that distance.

The second `printf()` statement displays the calculated speed as a whole-number MPH value.

The format specifiers control how the values are displayed:

| Format Specifier | Purpose                                                           |
| ---------------- | ----------------------------------------------------------------- |
| `%.1lf`          | Displays a `double` value with one digit after the decimal point. |
| `%d`             | Displays an integer value.                                        |
| `\n`             | Moves the cursor to the next line.                                |

### 4.8 Program Termination

```
return 0;
```

After displaying the results, the program returns `0` from `main()`.

This indicates that the program has completed normal execution.

## 5. Operators Used

The program uses arithmetic, assignment, and type-conversion operations.

### 5.1 Arithmetic Operators

| Operator | Name     | Purpose                                                                                   |
| -------- | -------- | ----------------------------------------------------------------------------------------- |
| `/`      | Division | Converts minutes into hours and divides the distance by the travel time to calculate MPH. |

### 5.2 Assignment Operator

| Operator | Name       | Purpose                                                                      |
| -------- | ---------- | ---------------------------------------------------------------------------- |
| `=`      | Assignment | Assigns the calculated speed to `milesPerHour` and initializes the constant. |

### 5.3 Type Casting

| Expression                 | Conversion        | Purpose                                                             |
| -------------------------- | ----------------- | ------------------------------------------------------------------- |
| `(double)MINUTES_TO_HOURS` | `int` to `double` | Ensures floating-point division when converting minutes into hours. |
| `(int)(...)`               | `double` to `int` | Converts the calculated speed into a whole-number MPH result.       |

### 5.4 Address-of Operator

| Operator | Name       | Purpose                                                                                                   |
| -------- | ---------- | --------------------------------------------------------------------------------------------------------- |
| `&`      | Address-of | Supplies the memory addresses of `milesDriven` and `numMinutes` to their respective `scanf()` statements. |

## 6. Program Execution Sequence

The program follows a sequential input-processing-output structure.

| Step | Operation               | Description                                                                     |
| ---- | ----------------------- | ------------------------------------------------------------------------------- |
| 1    | Program Start           | Execution begins in `main()`.                                                   |
| 2    | Constant Declaration    | Defines `MINUTES_TO_HOURS` with a value of 60.                                  |
| 3    | Variable Declaration    | Declares `milesPerHour`, `numMinutes`, and `milesDriven`.                       |
| 4    | Distance Prompt         | Requests the number of miles driven.                                            |
| 5    | Distance Input          | Reads the distance as a `double` and stores it in `milesDriven`.                |
| 6    | Time Prompt             | Requests the number of minutes required to travel the entered distance.         |
| 7    | Time Input              | Reads the travel time as an integer and stores it in `numMinutes`.              |
| 8    | Time Conversion         | Converts the travel time from minutes into hours using floating-point division. |
| 9    | Speed Calculation       | Divides the distance by the converted travel time.                              |
| 10   | Type Conversion         | Converts the calculated floating-point speed into an integer.                   |
| 11   | Result Assignment       | Stores the whole-number speed in `milesPerHour`.                                |
| 12   | Trip Information Output | Displays the distance traveled and elapsed time.                                |
| 13   | Speed Output            | Displays the calculated speed in MPH.                                           |
| 14   | Program Termination     | Returns `0` and ends execution.                                                 |

## 7. Text-Based Program Flowchart

```
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
              | Declare constant:        |
              | MINUTES_TO_HOURS = 60    |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Declare variables:       |
              | milesPerHour             |
              | numMinutes               |
              | milesDriven              |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Prompt for miles driven  |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Read milesDriven         |
              | using scanf("%lf", ...)  |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Prompt for minutes       |
              | Include entered mileage  |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Read numMinutes          |
              | using scanf("%d", ...)   |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Convert minutes to hours |
              | numMinutes /             |
              | (double)MINUTES_TO_HOURS |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Calculate average speed  |
              | milesDriven / hours      |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Cast result to int       |
              | (int)(calculated speed)  |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Assign result to         |
              | milesPerHour             |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Display distance driven  |
              | and travel time          |
              +--------------------------+
                           |
                           v
              +--------------------------+
              | Display milesPerHour     |
              | with MPH label           |
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

### 8.1 Variable Declaration

The program declares variables using the `int` and `double` data types.

These variables provide storage for the distance, travel time, and calculated speed.

### 8.2 Constants

The program uses the `const` keyword to define the minutes-to-hours conversion factor.

This prevents the conversion value from being accidentally modified during execution.

### 8.3 User Input

The program uses `scanf()` to collect two values from the user.

The `%lf` format specifier reads the distance as a `double`, while `%d` reads the travel time as an integer.

### 8.4 Formatted Output

The program uses `printf()` to display prompts and the final calculation.

Format specifiers control the presentation of floating-point and integer values.

### 8.5 Arithmetic Operations

The program uses division to convert minutes into hours and calculate average speed.

### 8.6 Explicit Type Casting

The program demonstrates explicit type conversion using `(double)` and `(int)`.

The first conversion ensures accurate floating-point division when converting minutes to hours.

The second conversion changes the calculated speed into a whole-number integer.

### 8.7 Floating-Point Arithmetic

The program uses the `double` data type to retain decimal precision during the time conversion and speed calculation.

This prevents integer division from producing an inaccurate intermediate result.

### 8.8 Sequential Program Execution

The program executes statements in a defined order:

1. Declare variables and constants.
2. Collect the distance.
3. Collect the travel time.
4. Calculate the average speed.
5. Display the result.
6. Terminate execution.

The program does not require loops or conditional statements because the calculation only needs to be performed once.

## 9. Program Characteristics and Limitations

| Characteristic        | Description                                                            |
| --------------------- | ---------------------------------------------------------------------- |
| Input Quantity        | Accepts distance and travel time.                                      |
| Distance Data Type    | `double`.                                                              |
| Travel Time Data Type | `int`.                                                                 |
| Speed Data Type       | `int`.                                                                 |
| Conversion Constant   | 60 minutes per hour.                                                   |
| Calculation Method    | Distance divided by time expressed in hours.                           |
| Type Conversion       | Explicit conversion from `int` to `double` and from `double` to `int`. |
| Output Method         | Console output using `printf()`.                                       |
| Distance Precision    | Displays one decimal place.                                            |
| Speed Precision       | Displays a whole-number MPH result.                                    |
| Program Structure     | All operations are contained in `main()`.                              |
| Control Structures    | Sequential execution; no loops or conditional statements.              |
| Program Termination   | Returns `0` from `main()`.                                             |

### 9.1 Integer Travel Time

The program declares `numMinutes` as an integer.

Therefore, the user is expected to enter a whole number of minutes rather than a fractional time value.

### 9.2 Whole-Number Speed Output

The program explicitly converts the calculated speed to an integer.

Any fractional portion of the calculated speed is discarded.

For example:

| Calculated Speed | Displayed Speed |
| ---------------- | --------------- |
| 45.7 MPH         | 45 MPH          |
| 62.9 MPH         | 62 MPH          |
| 70.5 MPH         | 70 MPH          |
| 85.1 MPH         | 85 MPH          |

The program truncates the result rather than rounding it.

### 9.3 No Input Validation

The current implementation does not validate the user's distance or travel time.

It assumes that the user enters valid numerical values.

The program does not prevent:

- Negative mileage.
- Zero mileage.
- Negative travel time.
- Zero travel time.
- Nonnumeric input.

### 9.4 Division by Zero

The calculation divides the distance by the travel time converted into hours.

If the user enters zero minutes, the denominator becomes zero.

The program does not contain a conditional statement to prevent division by zero. A zero-minute input can therefore cause an invalid floating-point calculation.

### 9.5 No Fractional Travel Time

Because `numMinutes` is declared as an `int`, the program does not support travel times containing fractional minutes.

A more flexible implementation could use a `double` variable for travel time.

### 9.6 No Rounding

The final speed is converted to an integer using an explicit type cast.

This discards the fractional portion rather than rounding to the nearest whole number.

### 9.7 Average Speed Assumption

The calculation uses total distance divided by total travel time.

It produces an average speed for the trip, not an instantaneous vehicle speed or a measurement of the vehicle's speed at a particular moment.

## 10. Overall Summary

The **MPH** program demonstrates fundamental C programming concepts by calculating average vehicle speed using distance and elapsed travel time.

The program begins by declaring a constant representing the number of minutes in an hour and three variables used to store the distance, travel time, and calculated speed.

It prompts the user to enter the number of miles driven and the number of minutes required to travel that distance.

During processing, the program converts the travel time from minutes into hours using explicit type casting to ensure floating-point division. It then divides the distance by the converted travel time to calculate the average speed.

The calculated floating-point result is explicitly converted to an integer and stored in `milesPerHour`. Finally, the program displays the distance traveled, the elapsed time, and the calculated speed in MPH.

The primary programming concepts demonstrated include variable declarations, constants, data types, console input and output, arithmetic operations, assignment statements, explicit type casting, floating-point arithmetic, and sequential program execution.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, including variable declarations, constants, data types, input/output operations, arithmetic calculations, explicit type casting, and formatted output.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.

Add the complete source codeCorrect the division-by-zero explanation