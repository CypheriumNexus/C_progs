# Shapes with Asterisks – C Program Documentation

| **Program Information** | **Details** |
|---|---|
| Program Name | Shapes with Asterisks |
| Programmer | Brian Lorick |
| Programming Language | C |
| Development Environment | Microsoft Visual Studio |
| Course Topic | Chapter 1 – Introduction |
| Original Date | January 25, 2024 |
| Source File | `Shapes with Asterisks.c` |

---

## 1. Program Overview

**Shapes with Asterisks** is a basic C program that demonstrates console output using formatted text and repeated character patterns.

The program uses a series of `printf()` statements to display four different geometric shapes constructed from asterisk (`*`) characters. Each shape is separated visually by vertical pipe (`|`) characters.

After displaying the first group of shapes, the program prints the word **LOVE** using asterisk characters.

The program demonstrates fundamental C programming concepts, including:

- Standard input/output library usage.
- The `main()` function.
- Function calls.
- String literals.
- Escape sequences.
- Console formatting.
- Sequential program execution.
- Program termination using `return 0`.

Unlike programs that calculate values or accept user input, this program primarily focuses on displaying predefined character patterns.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directive

```c
#define _CRT_SECURE_NO_WARNINGS
```

This Microsoft Visual C-specific preprocessor directive suppresses warnings associated with certain standard C library functions, including `printf()` and `scanf()`.

The directive is included in the source code, although this particular program does not use `scanf()` or other input functions.

### 2.2 Standard Input/Output Library

```c
#include <stdio.h>
```

The `stdio.h` header file provides standard input/output functionality.

The program uses the following function:

| Function | Purpose |
|---|---|
| `printf()` | Displays text and asterisk patterns in the console. |

No additional libraries are required because the program does not perform mathematical calculations, accept user input, or manipulate external files.

## 3. Variables and Data Structures

The original source code does not declare any variables, arrays, structures, or constants.

The following section appears inside `main()`:

```c
// Constant and Variable Declarations

// *** Your program goes here ***
```

These are comments left in the source file as part of the original programming template. They do not execute and do not create variables or constants.

The program relies entirely on predefined string literals passed directly to `printf()`.

### 3.1 String Literals

A string literal is a sequence of characters enclosed in double quotation marks.

For example:

```c
printf("*********  |     ***     |      *      \n");
```

The text between the quotation marks is passed to `printf()` for display.

The program uses string literals to define every row of the geometric shapes and the word LOVE.

## 4. Processing Logic and Statements

### 4.1 Main Function

```c
int main(void)
```

The `main()` function serves as the entry point of the program.

Execution begins at the opening brace of `main()` and continues sequentially through each statement until the function reaches:

```c
return 0;
```

The function returns an integer value to the operating system to indicate the program's termination status.

### 4.2 Displaying the Four Shapes

The first group of `printf()` statements displays four separate geometric patterns.

```c
printf("*********  |     ***     |      *      |      *      \n");
printf("*       *  |   *     *   |     ***     |     * *     \n");
printf("*       *  |  *       *  |    *****    |    *   *    \n");
printf("*       *  |  *       *  |      *      |   *     *   \n");
printf("*       *  |  *       *  |      *      |  *       *  \n");
printf("*       *  |  *       *  |      *      |   *     *   \n");
printf("*       *  |  *       *  |      *      |    *   *    \n");
printf("*       *  |   *     *   |      *      |     * *     \n");
printf("*********  |     ***     |      *      |      *      \n");
```

Each statement displays one horizontal row of the combined design.

The vertical pipe characters separate the four patterns visually.

The shapes represented are:

1. **Rectangle** – A hollow rectangular outline constructed using asterisks.
2. **Diamond** – A diamond-shaped pattern using progressively increasing and decreasing asterisk positions.
3. **Triangle** – A vertically oriented triangular pattern.
4. **Hourglass** – A pattern that expands and contracts around its center.

The nine output rows are carefully arranged using spaces to preserve the alignment of each shape.

### 4.3 Newline Escape Sequence

Each row ends with:

```c
\n
```

The newline escape sequence moves the console output cursor to the beginning of the next line.

This allows the program to build larger visual patterns from multiple individual `printf()` statements.

Without the newline characters, the output would appear as one continuous line.

### 4.4 Separating the Two Pattern Groups

```c
printf("\n");
```

After displaying the four shapes, the program executes an additional `printf()` statement containing only a newline escape sequence.

This creates a blank line between the geometric patterns and the word LOVE.

The blank line improves the readability and visual separation of the output.

### 4.5 Displaying the Word LOVE

The second group of `printf()` statements constructs the word LOVE using asterisk characters.

```c
printf("*              ***       *       *    *********  \n");
printf("*            *     *     *       *    *          \n");
printf("*           *       *    *       *    *          \n");
printf("*           *       *    *       *    *          \n");
printf("*           *       *    *       *    *********  \n");
printf("*           *       *     *     *     *          \n");
printf("*           *       *      *   *      *          \n");
printf("*            *     *        * *       *          \n");
printf("*********      ***           *        *********  \n");
```

Each statement displays one row of the lettering.

The asterisks and spaces are positioned to form four letters:

- **L** – A vertical line with a horizontal base.
- **O** – A hollow, rounded rectangular character.
- **V** – Two diagonal lines converging toward the bottom.
- **E** – A vertical line with horizontal sections.

The nine rows combine to create the complete word.

### 4.6 Program Termination

```c
return 0;
```

The `return 0` statement ends the `main()` function and indicates successful program execution.

The comment:

```c
// end main()
```

is included for source-code readability and does not affect program behavior.

## 5. Operators and Escape Sequences Used

The program uses very few operators because its primary purpose is displaying predefined text.

| Symbol | Category | Purpose |
|---|---|---|
| `#` | Preprocessor directive | Introduces the `#define` and `#include` directives. |
| `()` | Function syntax | Encloses function parameters and function arguments. |
| `{}` | Block delimiters | Define the beginning and end of the `main()` function body. |
| `;` | Statement terminator | Marks the end of executable C statements. |
| `//` | Comment syntax | Introduces single-line comments. |
| `"` | String delimiter | Identifies the beginning and end of string literals. |

### 5.1 Escape Sequences

The program uses the newline escape sequence:

```c
\n
```

Its purpose is to move output to the next line.

The program also uses spaces directly within its string literals to control horizontal alignment.

### 5.2 Function Call Syntax

Each `printf()` statement follows this general structure:

```c
printf("text to display");
```

The string literal is passed as an argument to the function.

The function processes the string and sends the characters to the standard output stream, which is normally the console.

## 6. Program Execution Sequence

The program follows a straightforward sequential execution process:

1. The program begins execution in `main()`.
2. The preprocessor directive and header file are processed during compilation.
3. The program reaches the first `printf()` statement.
4. The first group of nine statements displays the four geometric shapes.
5. A newline statement creates a blank line.
6. The second group of nine statements displays the word LOVE.
7. Another newline statement separates the output from the console prompt.
8. The program executes `return 0`.
9. The operating system receives the successful termination status.

There are no loops, conditional statements, calculations, or user-input operations in the original source code.

## 7. Text-Based Program Flowchart

### 7.1 Main Program Flow

```text
              +------------------------+
              |         START          |
              +-----------+------------+
                          |
                          v
              +------------------------+
              | Enter main() Function  |
              +-----------+------------+
                          |
                          v
              +------------------------+
              | Display Four Shapes    |
              | Using printf()         |
              +-----------+------------+
                          |
                          v
              +------------------------+
              | Print Blank Line       |
              +-----------+------------+
                          |
                          v
              +------------------------+
              | Display Word LOVE      |
              | Using printf()         |
              +-----------+------------+
                          |
                          v
              +------------------------+
              | Execute return 0       |
              +-----------+------------+
                          |
                          v
              +------------------------+
              |          END           |
              +------------------------+
```

### 7.2 Output Construction Flow

```text
       +----------------------------+
       | Begin Console Output       |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Print Shape Row 1          |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Print Shape Rows 2–9       |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Print Blank Line           |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Print LOVE Row 1           |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Print LOVE Rows 2–9        |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | Return 0                   |
       +-------------+--------------+
                     |
                     v
       +----------------------------+
       | End Program                |
       +----------------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 Standard Output

The program demonstrates how `printf()` sends character data to the console.

Each function call outputs a predefined string.

### 8.2 String Literals

The geometric shapes and lettering are constructed using string literals.

The program demonstrates how characters, spaces, and escape sequences can be combined to create formatted output.

### 8.3 Sequential Execution

The statements execute in the order they appear in the source code.

There are no branching structures or repetition structures controlling execution.

### 8.4 Console Formatting

The program uses spaces and newline escape sequences to control the placement of characters.

The horizontal spacing within each string is essential to maintaining the appearance of the shapes and lettering.

### 8.5 Preprocessor Directives

The source code includes `#define` and `#include` directives.

These are processed before the compiler translates the C source code into executable instructions.

### 8.6 Comments

The program contains single-line comments introduced by `//`.

Comments provide descriptions and organizational information for programmers but are ignored during compilation.

### 8.7 Function Structure

The program demonstrates the basic structure of a C application through the `main()` function and calls to the standard library's `printf()` function.

## 9. Program Characteristics and Limitations

### 9.1 Static Output

All displayed patterns are predefined in the source code.

The program does not generate shapes dynamically or allow the user to choose different designs.

### 9.2 No User Input

The program does not request or accept information from the user.

All output is produced automatically when the program executes.

### 9.3 No Variables or Calculations

The source code does not declare variables or perform mathematical operations.

Every displayed character is contained directly within a string literal.

### 9.4 Alignment Depends on Text Formatting

The shapes depend on carefully positioned spaces and asterisks.

Changes to spacing, character placement, or line formatting can alter the appearance of the output.

### 9.5 No Repetition Structures

The program uses individual `printf()` statements for each output row.

A more advanced implementation could use loops and stored character patterns to generate the shapes, but that functionality is not present in the original source.

## 10. Overall Summary

Shapes with Asterisks demonstrates fundamental C programming concepts through the use of formatted console output.

The program uses the `stdio.h` library and repeated calls to `printf()` to display four geometric patterns and the word LOVE using asterisk characters.

It demonstrates string literals, escape sequences, function calls, preprocessor directives, comments, sequential execution, and basic program structure.

Although the program does not include variables, arrays, loops, or conditional statements, it provides an introductory example of how C programs communicate with users through standard output and how carefully formatted strings can be used to construct visual patterns in a console environment.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational, instructional, and programming-reference purposes. It is intended to demonstrate introductory C programming concepts, including standard output, function calls, string literals, escape sequences, preprocessor directives, comments, and sequential program execution.

This source code is not intended to be submitted as another student's original work, used to circumvent coursework requirements, or used for plagiarism or academic dishonesty.

Students should maintain academic integrity by understanding the source code, independently completing assigned coursework, and following their institution's academic policies.

The author is not responsible for unauthorized use, academic misconduct, plagiarism, cheating, or any other misuse of this program or its contents.