# 2D Rainfall – Program Notes & Flowchart

**Programmer:** Brian Lorick  
**Source File:** `2D Rainfall.c`  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio 2019  
**Course Topic:** Chapter 5 – Arrays  
**Program Type:** Console Application

---

## 1. Program Overview

The 2D Rainfall program demonstrates the use of two-dimensional arrays to store and process rainfall measurements collected over a five-year period.

The program contains rainfall measurements for 12 months across five years, resulting in 60 individual data values. It processes these measurements to calculate:

- Total rainfall accumulated during each year.
- Average rainfall received during each month across all five years.
- A formatted display of the original rainfall measurements.
- A yearly rainfall summary and monthly average summary.

The program uses nested `for` loops to access the two-dimensional array and accumulate rainfall totals.

## 2. Libraries and Header Files

```c
#include <stdio.h>
```

**stdio.h – Standard Input/Output Library**

Provides access to standard input/output functions. The program primarily uses `printf()` to display rainfall measurements, yearly totals, monthly averages, and formatted headings.

No user input is required because all rainfall measurements are initialized directly within the program.

## 3. Variables and Data Structures

The program uses three arrays and two loop-control variables.

| Variable | Data Type | Purpose |
|---|---|---|
| `rainfall[5][12]` | double | Stores rainfall measurements for five years and twelve months. |
| `yearlyTotal[5]` | double | Stores accumulated rainfall for each year. |
| `monthlyTotal[12]` | double | Stores accumulated rainfall for each month across all five years. |
| `year` | int | Controls the yearly iterations. |
| `month` | int | Controls the monthly iterations. |

### A. Two-Dimensional Array: rainfall

```c
double rainfall[5][12] =
{
    {0.88, 1.11, 2.01, 3.64, 6.44, 5.58, 4.23, 4.34, 4.00, 2.05, 1.48, 0.77},
    {0.76, 0.94, 2.09, 3.29, 4.68, 3.52, 3.52, 4.82, 3.72, 2.21, 1.24, 0.80},
    {0.67, 0.80, 1.75, 2.70, 4.01, 3.88, 3.72, 3.78, 3.55, 1.88, 1.21, 0.61},
    {0.82, 0.80, 1.99, 3.05, 4.19, 4.44, 3.98, 4.57, 3.43, 2.32, 1.61, 0.75},
    {0.72, 0.90, 1.71, 2.02, 2.33, 2.98, 2.65, 2.99, 2.55, 1.99, 1.05, 0.92}
};
```

The two-dimensional array contains five rows and twelve columns.

- Rows represent individual years.
- Columns represent individual months.
- Each element stores an individual rainfall measurement.
- The `double` data type allows decimal values to be stored.

Individual array elements are accessed using two indexes:

```c
rainfall[year][month]
```

For example, `rainfall[0][0]` accesses the January rainfall measurement for the first year.

### B. Accumulator Arrays

```c
double yearlyTotal[5] = {0};
double monthlyTotal[12] = {0};
```

These arrays are initialized to zero before calculations begin.

- `yearlyTotal` accumulates the rainfall measurements across each row.
- `monthlyTotal` accumulates rainfall measurements from the same month across all five years.

Initializing the arrays to zero ensures that calculations begin with a clean starting value.

## 4. Processing Logic and Statements

### A. Nested for Loops

The program uses nested `for` loops to process the rainfall data.

```c
for (int year = 0; year < 5; year++)
{
    for (int month = 0; month < 12; month++)
    {
        yearlyTotal[year] += rainfall[year][month];
        monthlyTotal[month] += rainfall[year][month];
    }
}
```

**Outer Loop – Year**

- Starts at index `0`.
- Continues while `year` is less than `5`.
- Increments the year index after each iteration.
- Processes one row of the rainfall array at a time.

**Inner Loop – Month**

- Starts at index `0`.
- Continues while `month` is less than `12`.
- Increments the month index.
- Processes all twelve monthly measurements for the current year.

The nested loops execute 60 times in total, processing every rainfall measurement.

### B. Accumulation Operators

```c
yearlyTotal[year] += rainfall[year][month];
monthlyTotal[month] += rainfall[year][month];
```

The `+=` compound assignment operator adds the current rainfall measurement to the existing accumulator value.

These statements perform two separate calculations:

1. Add the monthly measurement to the corresponding year's total.
2. Add the monthly measurement to the corresponding month's total across all five years.

### C. Formatted Output

The program uses `printf()` to display the rainfall table and calculated results.

Examples:

```c
printf("%.2f  ", rainfall[year][month]);
```

```c
printf("201%d  %.2f\n", year + 5, yearlyTotal[year]);
```

Formatting elements:

| Element | Function |
|---|---|
| `%d` | Displays an integer. |
| `%f` | Displays a floating-point value. |
| `%.2f` | Displays a decimal value rounded to two decimal places. |
| `\n` | Moves output to the next line. |
| `\n\n` | Adds a blank line. |

The year is displayed using `year + 5`, producing 2015 through 2019.

### D. Monthly Average Calculation

```c
for (int month = 0; month < 12; month++)
{
    printf(" %.2f ", monthlyTotal[month] / 5);
}
```

The program calculates the average rainfall for each month by dividing its accumulated total by five.

**Mathematical Formula:**

\[
\text{Monthly Average} =
\frac{\text{Total Rainfall for Month}}{5}
\]

The divisor is five because the program contains five years of rainfall measurements.

## 5. Operators Used

| Operator | Name | Purpose |
|---|---|---|
| `=` | Assignment | Initializes variables and arrays. |
| `<` | Less Than | Controls loop termination. |
| `++` | Increment | Advances loop counters. |
| `+=` | Addition Assignment | Accumulates rainfall totals. |
| `/` | Division | Calculates monthly averages. |
| `+` | Addition | Generates displayed year values. |

## 6. Program Execution Sequence

1. The program enters `main()`.
2. The rainfall array is initialized with 60 predefined measurements.
3. The yearly and monthly accumulator arrays are initialized to zero.
4. Nested `for` loops process all rainfall measurements.
5. Yearly rainfall totals are accumulated.
6. Monthly rainfall totals are accumulated.
7. The program displays the rainfall table.
8. A loop displays the total rainfall for each year.
9. Another loop calculates and displays the average rainfall for each month.
10. The program returns `0` and terminates.

## 7. Text-Based Program Flowchart

The following flowchart represents the program's execution logic, including array initialization, nested loops, accumulation, output, and termination.

```text
+--------------------------------------+
|                START                 |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
|              main()                  |
|          Program Begins              |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Initialize 2D Rainfall Array         |
| rainfall[5][12]                      |
| Store 60 Rainfall Measurements       |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Initialize Accumulator Arrays        |
| yearlyTotal[5] = 0                   |
| monthlyTotal[12] = 0                 |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Initialize Year Counter              |
| year = 0                             |
+--------------------------------------+
                  |
                  v
          +------------------+
          |    year < 5 ?    |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Initialize Month Counter             |
| month = 0                            |
+--------------------------------------+
              |
              v
          +------------------+
          |   month < 12 ?   |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Access Rainfall Array                |
| rainfall[year][month]                |
+--------------------------------------+
              |
              v
+--------------------------------------+
| Add Rainfall to Yearly Total         |
| yearlyTotal[year] +=                 |
| rainfall[year][month]                |
+--------------------------------------+
              |
              v
+--------------------------------------+
| Add Rainfall to Monthly Total        |
| monthlyTotal[month] +=               |
| rainfall[year][month]                |
+--------------------------------------+
              |
              v
+--------------------------------------+
| Increment Month Counter              |
| month++                              |
+--------------------------------------+
              |
              +------> Return to
                       month < 12?
                            |
                            |
                 NO         v
                 |   +------------------+
                 |   | Increment Year   |
                 |   | year++           |
                 |   +------------------+
                 |           |
                 |           +----> Return to
                 |                  year < 5?
                 |
                 v
+--------------------------------------+
| Display Rainfall Table               |
| Print Month Headings                 |
| Display 5 Years of Measurements      |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Display Yearly Rainfall Totals       |
| Loop Through yearlyTotal[5]          |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Display Monthly Rainfall Averages    |
| Loop Through monthlyTotal[12]        |
| Divide Each Total by 5               |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
|              return 0               |
|          Program Terminates          |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
|                 END                  |
+--------------------------------------+
```

## 8. Important Programming Concepts Demonstrated

| Concept | Application |
|---|---|
| Two-Dimensional Arrays | Organizes rainfall data by year and month. |
| Array Initialization | Populates the array with predefined values. |
| Nested Iteration | Processes rows and columns. |
| Accumulator Variables | Maintains running rainfall totals. |
| Arithmetic Operations | Calculates totals and averages. |
| Formatted Output | Displays organized rainfall information. |
| Loop Control | Controls the number of years and months processed. |
| Function Structure | Uses `main()` as the program entry point. |

## 9. Program Characteristics

| Category | Description |
|---|---|
| Input | None; data is hardcoded into the array. |
| Processing | Accumulates rainfall measurements and calculates averages. |
| Output | Rainfall table, yearly totals, and monthly averages. |
| Primary Data Structure | Two-dimensional array. |
| Iteration | Nested `for` loops. |
| Conditional Statements | No `if/else` statements are used. Loop conditions control execution. |
| Functions | `main()` is the program entry point. |
| Termination | `return 0`. |

## 10. Overall Summary

The 2D Rainfall program demonstrates how two-dimensional arrays can organize and process related numerical data. Using nested `for` loops, the program accesses 60 predefined rainfall measurements, calculates the total rainfall for each year, and accumulates rainfall by month across five years. The monthly averages are calculated by dividing each monthly accumulation by five. Finally, `printf()` displays the original measurements, yearly totals, and monthly averages in a formatted table.

The program demonstrates array indexing, nested iteration, accumulator variables, compound assignment operators, and basic arithmetic operations in C. It provides a practical example of applying two-dimensional arrays to organize and analyze numerical information.

---

**Educational Disclaimer:** These programs and notes are provided for educational and reference purposes. They are not intended to encourage plagiarism, academic dishonesty, or the unauthorized submission of another person's work. Always maintain academic integrity and follow your institution's academic policies when referencing or adapting programming examples.