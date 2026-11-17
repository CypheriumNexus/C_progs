# 2D Sum of Columns – Program Notes & Flowchart

**Programmer:** Brian Lorick  
**Source File:** `2D Sum of Columns.c`  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio 2019  
**Course Topic:** Chapter 5 – Arrays  
**Program Type:** Console Application

---

## 1. Program Overview

The 2D Sum of Columns program demonstrates the use of two-dimensional arrays to store, organize, and manipulate integer values.

The program declares a 10 × 10 integer array and populates it with sequential numbers ranging from 1 to 100. Once populated, the program displays the complete array in a formatted table before calculating the sums of two specific columns: the fourth and ninth columns.

The program demonstrates:

- Two-dimensional array declaration and initialization.
- Nested `for` loops for populating and displaying array elements.
- Sequential data assignment using a counter variable.
- Array indexing to access specific columns.
- Accumulator variables for calculating column totals.
- Formatted console output using `printf()`.

## 2. Libraries and Header Files

```c
#include <stdio.h>
```

**stdio.h – Standard Input/Output Library**

Provides access to standard input/output functions. The program uses `printf()` to display the array contents, column totals, and formatted output.

No user input is required because all array values are generated internally.

## 3. Variables and Data Structures

The program uses a two-dimensional integer array, loop-control variables, a counter, and two accumulator variables.

| Variable | Data Type | Purpose |
|---|---|---|
| `array[10][10]` | int | Stores 100 sequential integer values. |
| `row` | int | Controls iteration through array rows. |
| `col` | int | Controls iteration through array columns. |
| `count` | int | Generates sequential values from 1 to 100. |
| `sumFourthCol` | int | Accumulates the sum of the fourth column. |
| `sumNinethCol` | int | Accumulates the sum of the ninth column. |

### A. Two-Dimensional Array

```c
int array[10][10];
```

The array is declared with ten rows and ten columns, providing storage for 100 integer elements.

- Rows represent horizontal groups of values.
- Columns represent vertical groups of values.
- Each element is accessed using two indexes.
- The `int` data type stores whole-number values.

Individual array elements are accessed using:

```c
array[row][col]
```

For example, `array[0][3]` accesses the fourth element in the first row.

**Important:** C arrays use zero-based indexing. Therefore, the fourth column is index `3`, and the ninth column is index `8`.

### B. Accumulator Variables

```c
int sumFourthCol = 0;
int sumNinethCol = 0;
```

These variables store the calculated totals for the selected columns.

Both are initialized to zero to ensure accumulation begins with a clean starting value.

- `sumFourthCol` stores the sum of the fourth column.
- `sumNinethCol` stores the sum of the ninth column.

### C. Counter Variable

```c
int count = 1;
```

The counter begins at one and supplies sequential values to the array during initialization.

The counter increases after each assignment, eventually populating the array with values from 1 through 100.

## 4. Processing Logic and Statements

### A. Populating the Two-Dimensional Array

```c
int count = 1;

for (row = 0; row < 10; row++)
{
    for (col = 0; col < 10; col++)
    {
        array[row][col] = count++;
    }
}
```

The program uses nested `for` loops to populate the array.

**Outer Loop – Rows**

- Begins at index `0`.
- Continues while `row` is less than `10`.
- Increments the row counter after each iteration.
- Processes one row at a time.

**Inner Loop – Columns**

- Begins at index `0`.
- Continues while `col` is less than `10`.
- Increments the column counter.
- Assigns values to all ten columns in the current row.

**Counter Operation**

```c
array[row][col] = count++;
```

The assignment operator stores the current counter value in the array element. The postfix increment operator (`++`) then increases the counter by one.

This results in the array being populated sequentially:

```text
 1   2   3   4   5   6   7   8   9  10
11  12  13  14  15  16  17  18  19  20
21  22  23  24  25  26  27  28  29  30
31  32  33  34  35  36  37  38  39  40
41  42  43  44  45  46  47  48  49  50
51  52  53  54  55  56  57  58  59  60
61  62  63  64  65  66  67  68  69  70
71  72  73  74  75  76  77  78  79  80
81  82  83  84  85  86  87  88  89  90
91  92  93  94  95  96  97  98  99 100
```

The nested loops execute 100 times, assigning one value to each array element.

### B. Displaying the Array

```c
printf("The contents of a 2-dimensional array, populated with the values 1 to 100...\n");

for (row = 0; row < 10; row++)
{
    for (col = 0; col < 10; col++)
    {
        printf("%d\t", array[row][col]);
    }

    printf("\n");
}
```

The program uses another set of nested `for` loops to display the populated array.

- The outer loop processes each row.
- The inner loop accesses and displays each column.
- `printf()` displays the integer stored at each array position.
- `\t` inserts a tab between values.
- `\n` moves the output to the next line after each row.

This produces a formatted 10 × 10 table.

### C. Calculating the Fourth Column

```c
for (row = 0; row < 10; row++)
{
    sumFourthCol += array[row][3];
}
```

The program calculates the sum of the fourth column by iterating through all ten rows.

The expression `array[row][3]` accesses the fourth column because array indexing begins at zero.

The `+=` operator adds each accessed value to the accumulator variable.

The fourth-column values are:

```text
4
14
24
34
44
54
64
74
84
94
```

**Calculation:**

\[
4+14+24+34+44+54+64+74+84+94=490
\]

The resulting total is stored in `sumFourthCol`.

### D. Calculating the Ninth Column

```c
for (row = 0; row < 10; row++)
{
    sumNinethCol += array[row][8];
}
```

The program calculates the sum of the ninth column using another `for` loop.

The expression `array[row][8]` accesses the ninth column because its zero-based index is `8`.

The ninth-column values are:

```text
9
19
29
39
49
59
69
79
89
99
```

**Calculation:**

\[
9+19+29+39+49+59+69+79+89+99=540
\]

The resulting total is stored in `sumNinethCol`.

### E. Displaying the Column Totals

```c
printf("\nThe sum of the 4th column is %d.\n", sumFourthCol);
printf("The sum of the 9th column is %d.\n", sumNinethCol);
printf("\n");
```

The program uses `printf()` to display the calculated column totals.

The `%d` format specifier displays integer values.

The `\n` escape sequence creates line breaks, while the final `printf("\n")` adds an additional blank line.

## 5. Operators Used

| Operator | Name | Purpose |
|---|---|---|
| `=` | Assignment | Assigns values to variables and array elements. |
| `<` | Less Than | Controls loop termination. |
| `++` | Increment | Advances loop counters and the value counter. |
| `+=` | Addition Assignment | Accumulates column totals. |

## 6. Program Execution Sequence

1. The program enters `main()`.
2. A 10 × 10 integer array is declared.
3. Row and column control variables are declared.
4. Both column accumulator variables are initialized to zero.
5. The counter variable is initialized to one.
6. Nested `for` loops populate the array with sequential values from 1 through 100.
7. Another set of nested loops displays the complete array.
8. A `for` loop iterates through all ten rows and accumulates the fourth-column values.
9. A second `for` loop iterates through all ten rows and accumulates the ninth-column values.
10. The program displays the calculated fourth- and ninth-column totals.
11. The program returns `0` and terminates.

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
| Declare 10 x 10 Integer Array        |
| int array[10][10]                    |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Initialize Variables                 |
| sumFourthCol = 0                     |
| sumNinethCol = 0                     |
| count = 1                            |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Initialize Row Counter               |
| row = 0                              |
+--------------------------------------+
                  |
                  v
          +------------------+
          |    row < 10 ?    |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Initialize Column Counter            |
| col = 0                              |
+--------------------------------------+
              |
              v
          +------------------+
          |    col < 10 ?    |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Populate Array Element               |
| array[row][col] = count++            |
+--------------------------------------+
              |
              v
+--------------------------------------+
| Increment Column Counter             |
| col++                                |
+--------------------------------------+
              |
              +------> Return to
                       col < 10?
                            |
                            |
                 NO         v
                 |   +------------------+
                 |   | Increment Row    |
                 |   | row++            |
                 |   +------------------+
                 |           |
                 |           +----> Return to
                 |                  row < 10?
                 |
                 v
+--------------------------------------+
| Display Array Heading                |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Initialize Display Row Counter       |
| row = 0                              |
+--------------------------------------+
                  |
                  v
          +------------------+
          |    row < 10 ?    |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Initialize Display Column Counter    |
| col = 0                              |
+--------------------------------------+
              |
              v
          +------------------+
          |    col < 10 ?    |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Display Array Element                |
| printf("%d\t", array[row][col])      |
+--------------------------------------+
              |
              v
+--------------------------------------+
| Increment Column Counter             |
| col++                                |
+--------------------------------------+
              |
              +------> Return to
                       col < 10?
                            |
                            |
                 NO         v
                 |   +------------------+
                 |   | Print New Line   |
                 |   +------------------+
                 |           |
                 |           v
                 |   +------------------+
                 |   | Increment Row    |
                 |   | row++            |
                 |   +------------------+
                 |           |
                 |           +----> Return to
                 |                  row < 10?
                 |
                 v
+--------------------------------------+
| Calculate Fourth Column Sum          |
| Initialize row = 0                   |
+--------------------------------------+
                  |
                  v
          +------------------+
          |    row < 10 ?    |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Add Fourth Column Value              |
| sumFourthCol += array[row][3]        |
+--------------------------------------+
              |
              v
+--------------------------------------+
| Increment Row Counter                |
| row++                                |
+--------------------------------------+
              |
              +------> Return to
                       row < 10?
                            |
                            |
                 NO         v
                 |   +------------------+
                 |   | Reset Row        |
                 |   | row = 0          |
                 |   +------------------+
                 |           |
                 |           v
                 |   +------------------+
                 |   | Calculate Ninth  |
                 |   | Column Sum       |
                 |   +------------------+
                 |
                 v
          +------------------+
          |    row < 10 ?    |
          +------------------+
              |          |
             YES         NO
              |          |
              v          |
+--------------------------------------+
| Add Ninth Column Value               |
| sumNinethCol += array[row][8]        |
+--------------------------------------+
              |
              v
+--------------------------------------+
| Increment Row Counter                |
| row++                                |
+--------------------------------------+
              |
              +------> Return to
                       row < 10?
                            |
                            |
                 NO         v
                 |
                 v
+--------------------------------------+
| Display Fourth Column Total          |
| sumFourthCol = 490                   |
+--------------------------------------+
                  |
                  v
+--------------------------------------+
| Display Ninth Column Total           |
| sumNinethCol = 540                   |
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
| Two-Dimensional Arrays | Stores 100 integer values in a 10 × 10 structure. |
| Array Indexing | Accesses individual elements using row and column positions. |
| Zero-Based Indexing | Uses index `3` for the fourth column and index `8` for the ninth column. |
| Nested Iteration | Uses nested `for` loops to populate and display the array. |
| Counter Variables | Generates sequential values from 1 through 100. |
| Accumulator Variables | Maintains running totals for selected columns. |
| Compound Assignment | Uses `+=` to accumulate column values. |
| Postfix Increment | Uses `count++` to assign sequential values. |
| Formatted Output | Uses `printf()` to display the array and calculated totals. |
| Function Structure | Uses `main()` as the program entry point. |

## 9. Program Characteristics

| Category | Description |
|---|---|
| Input | None; all values are generated internally. |
| Processing | Populates a 10 × 10 array and calculates two column totals. |
| Output | Displays the complete array and the sums of the fourth and ninth columns. |
| Primary Data Structure | Two-dimensional integer array. |
| Array Dimensions | 10 rows × 10 columns. |
| Data Range | Integers 1 through 100. |
| Iteration | Nested `for` loops and individual `for` loops. |
| Conditional Statements | No `if/else` statements are used. Loop conditions control execution. |
| Functions | `main()` is the program entry point. |
| Accumulation | Uses two integer accumulator variables. |
| Termination | `return 0`. |

## 10. Overall Summary

The 2D Sum of Columns program demonstrates how two-dimensional arrays can be used to organize and manipulate numerical data in C. The program declares a 10 × 10 integer array and uses nested `for` loops to populate it with sequential values ranging from 1 through 100. Additional nested loops display the array in a formatted table. Two separate `for` loops then access the fourth and ninth columns using their respective zero-based indexes and accumulate their values using compound assignment operators. Finally, `printf()` displays the calculated column totals of 490 and 540.

The program demonstrates array declaration, initialization, indexing, nested iteration, counter variables, accumulator variables, postfix increment operations, and formatted console output. It provides a practical example of using two-dimensional arrays to organize data and perform calculations on selected portions of an array.

---

**Educational Disclaimer:** These programs and notes are provided for educational and reference purposes. They are not intended to encourage plagiarism, academic dishonesty, or the unauthorized submission of another person's work. Always maintain academic integrity and follow your institution's academic policies when referencing or adapting programming examples.