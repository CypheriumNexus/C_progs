# MyToUpper – C Programming Project Documentation

**Programmer:** Brian Lorick  
**Program Name:** MyToUpper  
**Programming Language:** C  
**Development Environment:** Microsoft Visual Studio  
**Course Topic:** Chapter 6 – Functions  
**Original Date:** April 4, 2024  
**Source File:** `MyToUpper.c`

---

## 1. Program Overview

The **MyToUpper** program is a C application that accepts a string from the user and converts lowercase alphabetical characters into uppercase characters using a custom user-defined function named `MyToUpper()`.

The program demonstrates how functions, character pointers, arrays, strings, loops, conditional statements, and ASCII character values can be used to manipulate string data.

The program creates two character arrays:

- `original` – Stores the string entered by the user.
- `copy` – Stores a duplicate of the original string.

The program then calls `MyToUpper()` separately for each array, demonstrating how a function can modify string data through a character pointer.

The program follows four primary stages:

1. **Input** – Prompts the user to enter a string and stores it using `fgets()`.
2. **String Preparation** – Removes the newline character and copies the original string into a second character array.
3. **Processing** – Calls `MyToUpper()` to identify lowercase characters and convert them to uppercase.
4. **Output** – Displays the original string and both converted strings.

The primary purpose of this program is to demonstrate function creation, pointer manipulation, string handling, and character conversion without relying on the standard library's `toupper()` function.

## 2. Libraries and Header Files

### 2.1 Preprocessor Directives

| Directive | Purpose |
|---|---|
| `#include <stdio.h>` | Includes the Standard Input/Output library, providing access to `printf()`, `fgets()`, and `stdin`. |
| `#include <string.h>` | Includes the string manipulation library, providing access to `strcspn()` and `strcpy()`. |
| `#define MAX_LENGTH 20` | Defines a symbolic constant representing the maximum character-array size. |

### 2.2 Standard Library Functions

| Function | Purpose |
|---|---|
| `printf()` | Displays prompts, original string contents, and converted strings. |
| `fgets()` | Reads a string from standard input and stores it in a character array. |
| `strcspn()` | Locates the first newline character in the input string. |
| `strcpy()` | Copies the contents of the original string into another character array. |

### 2.3 User-Defined Function

| Function | Return Type | Parameter | Purpose |
|---|---|---|---|
| `MyToUpper()` | `void` | `char* str` | Converts lowercase alphabetical characters within a string to uppercase. |

The program defines its own character-conversion function rather than using a standard library conversion function.

## 3. Variables and Data Structures

### 3.1 Symbolic Constant

| Identifier | Type | Value | Purpose |
|---|---|---:|---|
| `MAX_LENGTH` | Preprocessor constant | `20` | Establishes the maximum size of the character arrays. |

The declaration:

```c
#define MAX_LENGTH 20
```

Defines a symbolic constant that is substituted by the preprocessor wherever `MAX_LENGTH` appears in the source code.

Both character arrays use this constant to establish their storage capacity.

### 3.2 Character Arrays

| Variable | Data Type | Size | Purpose |
|---|---|---:|---|
| `original` | `char[]` | 20 | Stores the string entered by the user. |
| `copy` | `char[]` | 20 | Stores a duplicate of the original string for independent modification. |

The arrays are declared inside `main()`:

```c
char original[MAX_LENGTH];
char copy[MAX_LENGTH];
```

Each array contains 20 character positions.

Because C strings require a null terminator (`'\0'`), the maximum number of input characters stored as part of the string is 19, leaving one position for the terminating character.

### 3.3 Function Parameter

| Parameter | Data Type | Purpose |
|---|---|---|
| `str` | `char*` | Points to the character currently being processed within the supplied string. |

The parameter:

```c
char* str
```

Is a character pointer that provides the function with access to the original character array.

As the function increments the pointer, it moves through the string one character at a time.

### 3.4 Data Structures

The program uses two fixed-size character arrays rather than dynamically allocated memory.

The arrays store null-terminated strings, allowing the program to process individual characters using pointer arithmetic.

No structures, linked lists, or dynamically allocated arrays are used.

## 4. Processing Logic and Statements

### 4.1 User-Defined Function – `MyToUpper()`

```c
void MyToUpper(char* str)
{
    while (*str)
    {
        if (*str >= 'a' && *str <= 'z')
        {
            *str = *str - 32;
        }

        str++;
    }
}
```

The `MyToUpper()` function is responsible for converting lowercase alphabetical characters into uppercase characters.

It accepts a character pointer as its parameter and modifies the string directly in memory.

The function does not return a value because its return type is `void`.

The function contains three primary operations:

1. A `while` loop that processes the string until its null terminator is reached.
2. An `if` statement that determines whether the current character is lowercase.
3. A pointer increment that advances to the next character.

### 4.2 Pointer-Based String Traversal

```c
while (*str)
```

The `while` loop continues as long as the character referenced by `str` is not the null terminator.

The expression:

```c
*str
```

Uses the dereference operator to access the character stored at the memory address currently held by the pointer.

In C, a null character (`'\0'`) evaluates as false.

Therefore, the loop automatically terminates when the end of the string is reached.

This approach allows the function to process a string without needing a separate index variable or an explicitly calculated string length.

### 4.3 Identifying Lowercase Characters

```c
if (*str >= 'a' && *str <= 'z')
```

The `if` statement checks whether the current character falls within the lowercase English alphabet range.

The condition contains two relational expressions combined using the logical AND operator (`&&`).

| Expression | Purpose |
|---|---|
| `*str >= 'a'` | Checks whether the character is greater than or equal to lowercase `a`. |
| `*str <= 'z'` | Checks whether the character is less than or equal to lowercase `z`. |
| `&&` | Requires both comparisons to be true. |

If both conditions are true, the current character is identified as a lowercase alphabetical character.

If either condition is false, the character remains unchanged.

This means uppercase letters, numbers, spaces, punctuation, and other characters are not modified.

### 4.4 ASCII Character Conversion

```c
*str = *str - 32;
```

This statement performs the actual lowercase-to-uppercase conversion.

The program uses the numerical relationship between lowercase and uppercase English letters in the ASCII character encoding.

In ASCII, corresponding uppercase and lowercase alphabetical characters differ by 32.

For example:

| Lowercase | ASCII Value | Uppercase | ASCII Value |
|---|---:|---|---:|
| `a` | 97 | `A` | 65 |
| `b` | 98 | `B` | 66 |
| `c` | 99 | `C` | 67 |
| `d` | 100 | `D` | 68 |
| `e` | 101 | `E` | 69 |
| `z` | 122 | `Z` | 90 |

Subtracting 32 from the lowercase character produces its corresponding uppercase character.

For example:

```c
'a' - 32
```

Produces:

```c
'A'
```

The assignment:

```c
*str = *str - 32;
```

Stores the converted character directly into the original memory location referenced by the pointer.

This means the function modifies the existing string rather than creating a separate converted string.

**Important:** This conversion method assumes an ASCII-compatible character encoding and is designed for the English lowercase alphabet. It is not a general Unicode or locale-aware conversion method.

### 4.5 Pointer Increment

```c
str++;
```

After processing the current character, the pointer is incremented.

The increment operator moves the pointer to the next character in the array.

For example, if `str` initially points to the first character:

```text
H e l l o \0
^
str
```

After executing `str++`:

```text
H e l l o \0
  ^
  str
```

The loop repeats until the pointer reaches the null terminator.

### 4.6 Main Function

```c
int main()
{
    char original[MAX_LENGTH];
    char copy[MAX_LENGTH];

    // Input and string processing

    return 0;
}
```

The `main()` function controls the overall program execution.

It declares the two character arrays, collects the user's input, prepares the strings, calls the conversion function, displays the results, and terminates execution.

### 4.7 Collecting User Input

```c
printf("Enter a string: ");
fgets(original, sizeof(original), stdin);
```

The program prompts the user to enter a string.

It then uses `fgets()` to read the input and store it in the `original` array.

The function receives three arguments:

| Argument | Purpose |
|---|---|
| `original` | Destination character array where the input is stored. |
| `sizeof(original)` | Maximum number of characters that can be read, including the null terminator. |
| `stdin` | Standard input stream, normally associated with the keyboard. |

Using `fgets()` helps prevent writing beyond the allocated array because the function is given the maximum available buffer size.

With a 20-character array, `fgets()` can store up to 19 input characters plus the null terminator.

### 4.8 Removing the Newline Character

```c
original[strcspn(original, "\n")] = '\0';
```

When `fgets()` reads a line of input, it may include the newline character generated when the user presses Enter.

The program uses `strcspn()` to locate the position of the first newline character.

The expression:

```c
strcspn(original, "\n")
```

Returns the index of the first newline character, if one exists.

The program then replaces the character at that position with the null terminator:

```c
= '\0';
```

This removes the newline from the stored string.

If the input does not contain a newline because the buffer became full, `strcspn()` returns the string length, and the assignment writes the null terminator at the existing end of the string.

### 4.9 Displaying the Original String

```c
printf("The string you entered was: %s\n", original);
```

The program displays the string entered by the user.

The `%s` format specifier tells `printf()` to display a null-terminated character string.

At this stage, the original string has not yet been modified by `MyToUpper()`.

### 4.10 Copying the Original String

```c
strcpy(copy, original);
```

The program uses `strcpy()` to duplicate the contents of `original` into `copy`.

This creates two separate character arrays containing the same string.

The purpose of this operation is to allow the program to demonstrate that the conversion function can independently modify each array.

Because both arrays have the same 20-character capacity and the original input is limited by `fgets()`, the copied string fits within the destination array.

### 4.11 Converting the Copy

```c
MyToUpper(copy);

printf("Using MyToUpper() to convert the original string: %s\n", copy);
```

The first function call passes the `copy` array to `MyToUpper()`.

The function converts the lowercase characters in `copy` to uppercase.

The converted copy is then displayed.

The original array remains unchanged during this first conversion because the function receives a pointer to `copy`, not `original`.

### 4.12 Converting the Original String

```c
MyToUpper(original);

printf("Using MyToUpper() to convert the copy of the string: %s\n", original);
```

The second function call passes the original array to `MyToUpper()`.

The function converts the lowercase characters in `original` to uppercase.

The converted original string is then displayed.

**Source-code observation:** The second output message says it is converting the copy of the string, but the actual function call passes `original`. The code therefore converts and displays the original array in this step. The output label is reversed or inaccurate.

### 4.13 Program Termination

```c
return 0;
```

After both strings have been converted and displayed, the program returns `0` from `main()`.

This indicates successful program termination.

## 5. Operators Used

The program uses relational, logical, arithmetic, assignment, dereference, and increment operators.

### 5.1 Relational Operators

| Operator | Name | Purpose |
|---|---|---|
| `>=` | Greater than or equal to | Checks whether the current character is at least lowercase `a`. |
| `<=` | Less than or equal to | Checks whether the current character is no greater than lowercase `z`. |

### 5.2 Logical Operators

| Operator | Name | Purpose |
|---|---|---|
| `&&` | Logical AND | Requires both lowercase-character comparisons to be true. |

### 5.3 Arithmetic Operators

| Operator | Name | Purpose |
|---|---|---|
| `-` | Subtraction | Subtracts 32 from a lowercase character's ASCII value. |

### 5.4 Assignment Operators

| Operator | Name | Purpose |
|---|---|---|
| `=` | Assignment | Stores the converted character and replaces the newline with a null terminator. |

### 5.5 Pointer and Increment Operators

| Operator | Name | Purpose |
|---|---|---|
| `*` | Dereference | Accesses or modifies the character stored at the address referenced by `str`. |
| `++` | Increment | Advances the character pointer to the next position in the string. |

## 6. Program Execution Sequence

The program follows an input-preparation-processing-output structure.

| Step | Operation | Description |
|---:|---|---|
| 1 | Program Start | Execution begins in `main()`. |
| 2 | Array Declaration | Creates the `original` and `copy` character arrays. |
| 3 | Input Prompt | Requests a string from the user. |
| 4 | Input Collection | Reads the string into `original` using `fgets()`. |
| 5 | Newline Removal | Uses `strcspn()` to locate and replace the newline character with `'\0'`. |
| 6 | Original Output | Displays the string entered by the user. |
| 7 | String Duplication | Uses `strcpy()` to copy `original` into `copy`. |
| 8 | First Function Call | Passes `copy` to `MyToUpper()`. |
| 9 | Character Traversal | Uses a `while` loop and pointer dereferencing to process each character. |
| 10 | Character Evaluation | Uses an `if` statement to identify lowercase alphabetical characters. |
| 11 | Character Conversion | Subtracts 32 from lowercase ASCII characters. |
| 12 | Pointer Advancement | Increments `str` to process the next character. |
| 13 | First Converted Output | Displays the uppercase version stored in `copy`. |
| 14 | Second Function Call | Passes `original` to `MyToUpper()`. |
| 15 | Second Character Traversal | Repeats the conversion process on the original array. |
| 16 | Second Converted Output | Displays the uppercase version stored in `original`. |
| 17 | Program Termination | Returns `0` and ends execution. |

## 7. Text-Based Program Flowchart

```text
                 +-------------------------+
                 |      PROGRAM START      |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 |        main()           |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Declare original[20]    |
                 | Declare copy[20]        |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Prompt user for string  |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Read input using fgets()|
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Remove newline using    |
                 | strcspn() and '\0'      |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Display original string |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Copy original to copy   |
                 | using strcpy()          |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Call MyToUpper(copy)    |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 |       MyToUpper()       |
                 | str points to copy     |
                 +-------------------------+
                            |
                            v
                    +----------------+
                    |    *str != 0?  |
                    +----------------+
                       |          |
                      YES         NO
                       |          |
                       v          |
              +----------------+  |
              | Is *str >= 'a' |  |
              | AND *str <= 'z'|  |
              +----------------+  |
                 |          |     |
                YES         NO    |
                 |          |     |
                 v          |     |
        +----------------+  |     |
        | *str = *str-32 |  |     |
        | Convert to     |  |     |
        | uppercase      |  |     |
        +----------------+  |     |
                 |          |     |
                 +----+-----+     |
                      |           |
                      v           |
              +----------------+  |
              | str++          |--+
              | Next character |
              +----------------+
                                  |
                                  v
                 +-------------------------+
                 | Return from function    |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Display uppercase copy  |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Call MyToUpper(original)|
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Repeat character         |
                 | conversion process       |
                 | on original array        |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 | Display uppercase       |
                 | original string         |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 |       return 0;         |
                 +-------------------------+
                            |
                            v
                 +-------------------------+
                 |       PROGRAM END       |
                 +-------------------------+
```

## 8. Important Programming Concepts Demonstrated

### 8.1 User-Defined Functions

The program defines a custom function named `MyToUpper()`.

This function performs a specific operation: converting lowercase characters to uppercase.

Separating the conversion logic from `main()` demonstrates modular programming and function reuse.

### 8.2 Function Parameters

The function receives a character pointer:

```c
void MyToUpper(char* str)
```

This parameter allows the function to access and modify the contents of a character array supplied by the calling function.

### 8.3 Pointers and Dereferencing

The program uses a pointer to navigate through a string.

The dereference operator (`*`) accesses the character stored at the current memory address.

The function modifies characters directly through the pointer rather than creating a separate output string.

### 8.4 Pointer Arithmetic

The statement:

```c
str++;
```

Advances the pointer by one character position.

This demonstrates pointer arithmetic and sequential memory traversal.

### 8.5 Character Arrays and Strings

The program uses fixed-size character arrays to store null-terminated strings.

The `original` and `copy` arrays demonstrate how strings can be stored and manipulated independently.

### 8.6 String Manipulation Functions

The program uses two functions from `<string.h>`:

- `strcspn()` identifies the location of a newline character.
- `strcpy()` duplicates the original string into another array.

These functions demonstrate common string-handling operations in C.

### 8.7 While Loops

The `while` loop processes characters until the null terminator is encountered.

This allows the function to traverse a string without needing to know its length in advance.

### 8.8 Conditional Statements

The `if` statement determines whether the current character falls within the lowercase alphabetical range.

Only characters satisfying both relational comparisons are converted.

### 8.9 ASCII Character Encoding

The program demonstrates how characters are represented by numerical values in ASCII.

Subtracting 32 from lowercase English letters produces their corresponding uppercase characters in ASCII.

### 8.10 In-Place Modification

The function changes the contents of the supplied character array directly.

It does not allocate another array or return a new string.

This demonstrates how pointers can be used to modify data in place.

### 8.11 String Copying and Independent Modification

By copying `original` into `copy`, the program creates two separate arrays containing the same text.

Each array can then be passed to the conversion function independently.

This demonstrates the difference between modifying a copy and modifying the original data.

## 9. Program Characteristics and Limitations

| Characteristic | Description |
|---|---|
| Input Method | Console input using `fgets()`. |
| Input Data Type | Character string. |
| Array Size | 20 characters per array. |
| Maximum Stored Input | 19 characters plus the null terminator. |
| String Preparation | Removes newline using `strcspn()`. |
| String Duplication | Uses `strcpy()`. |
| Conversion Function | User-defined `MyToUpper()`. |
| Conversion Method | Subtracts 32 from lowercase ASCII characters. |
| Traversal Method | Pointer-based `while` loop. |
| Character Evaluation | Relational comparisons using `if` and `&&`. |
| Modification Method | Changes the supplied string in place. |
| Output Method | Console output using `printf()`. |
| Program Structure | One user-defined function and `main()`. |
| Program Termination | Returns `0` from `main()`. |

### 9.1 Fixed Buffer Size

Both character arrays are limited to 20 characters.

The `fgets()` function is supplied with the array size, preventing it from reading more characters than the destination buffer can hold.

The program can therefore store up to 19 input characters plus the terminating null character.

### 9.2 Long Input Handling

If the user enters more than 19 characters, `fgets()` only reads the portion that fits in the array.

The remaining characters stay in the input stream because the program does not perform an additional input operation to consume them.

The program does not display a warning indicating that the input was truncated.

### 9.3 ASCII Dependency

The conversion logic relies on the ASCII numerical difference between lowercase and uppercase English letters.

The function is designed for standard English alphabetical characters and does not provide general Unicode or locale-aware character conversion.

### 9.4 Nonalphabetical Characters

The function only converts characters between lowercase `a` and lowercase `z`.

The following characters remain unchanged:

- Uppercase letters.
- Numbers.
- Spaces.
- Punctuation.
- Special characters outside the lowercase ASCII range.

For example:

```text
Input:  Hello World! 123
Output: HELLO WORLD! 123
```

### 9.5 In-Place Modification

The `MyToUpper()` function modifies the array passed to it.

Once `MyToUpper(original)` executes, the original array no longer contains the original lowercase text.

The program preserves the original text only long enough to create the separate `copy` array.

### 9.6 No Standard `toupper()` Function

The program does not use the standard C `toupper()` function.

Instead, it demonstrates how character conversion can be performed manually using ASCII values, relational operators, pointer dereferencing, and arithmetic.

### 9.7 Output Label Discrepancy

The source code contains two output messages:

```c
printf("Using MyToUpper() to convert the original string: %s\n", copy);

printf("Using MyToUpper() to convert the copy of the string: %s\n", original);
```

The first message displays the converted copy, while the second displays the converted original.

The second message therefore describes the wrong array. The actual function call converts `original`, not `copy`.

## 10. Overall Summary

The **MyToUpper** program demonstrates how user-defined functions, pointers, character arrays, and ASCII character encoding can be used to manipulate strings in C.

The program begins by declaring two fixed-size character arrays and prompting the user to enter a string. It uses `fgets()` to collect the input and `strcspn()` to remove the trailing newline character.

The original string is then duplicated using `strcpy()`, creating two independent arrays.

The program calls `MyToUpper()` first with the copied string and then with the original string. Within the function, a `while` loop traverses the characters using a pointer. An `if` statement checks whether each character is a lowercase English letter. If the character falls within the lowercase ASCII range, the program subtracts 32 from its value to produce the corresponding uppercase character.

The pointer advances through the array until it reaches the null terminator. The converted strings are then displayed using `printf()`.

The primary programming concepts demonstrated include user-defined functions, function parameters, pointers, dereferencing, pointer arithmetic, character arrays, string manipulation, `while` loops, conditional statements, relational operators, logical operators, ASCII encoding, and in-place data modification.

## 11. Educational and Academic Integrity Disclaimer

This program is provided for educational and reference purposes to demonstrate fundamental C programming concepts, including functions, pointers, character arrays, string manipulation, loops, conditional statements, ASCII character encoding, and in-place string modification.

It is not intended to encourage plagiarism, academic dishonesty, unauthorized submission, or misrepresentation of another person's work. Students should use this material responsibly as a learning reference and independently understand the programming concepts demonstrated.

The original author is not responsible for academic misconduct, unauthorized use, or any misuse of this program or its contents. Always follow your institution's academic integrity policies and course requirements.