# Questions

Answer the following questions about your minigrep implementation:

## 1. Pointer Arithmetic in Pattern Matching

In your `str_match()` function, you need to check if the pattern appears anywhere in the line, not just at the beginning. Explain your approach for checking all possible positions in the line. How do you use pointer arithmetic to advance through the line?

> _For checking each part of the line, I had to increment the pointer of the line and keep the position, and whenever starting comparison with the pattern, keep running the loop until two character does not match. For pattern, when starting each comparision, pattern pointer would be copied as the front of the pointer. It works as some sort of loop with pointer, as the character reaches until '\0'._

## 2. Case-Insensitive Comparison

When implementing case-insensitive matching (the `-i` flag), you need to compare characters without worrying about case. Explain how you handle the case where the pattern is "error" but the line contains "ERROR" or "Error". What functions did you use and why?

> _I used tolower() function for lowering all characters from line, character by character. I had to increment pointers to go through all uppercases._

## 3. Memory Management

Your program allocates a line buffer using `malloc()`. Explain what would happen if you forgot to call `free()` before your program exits. Would this cause a problem for:
   - A program that runs once and exits?
   - A program that runs in a loop processing thousands of files?

> _Even after forgetting freeing allocated memory, it might not be a hugh problem for a program that runs a single time because it has only small part of memory leaks. For loop processing programs, however, this memory leak cause a huge problem as lowering the performance, malfunctioning, or breaking in the middle of running the program._

## 4. Buffer Size Choice

The starter code defines `LINE_BUFFER_SZ` as 256 bytes. What happens if a line in the input file is longer than 256 characters? How does `fgets()` handle this situation? (You may need to look up the documentation for `fgets()` to answer this.)

> _If the file is longer than 255 characters (excluding the last one as '\0'), it stops reading, and continues to read the file from the next fgets() call -> that is the reason why while loop is used for reading all the lines from file._

## 5. Return Codes

The program uses different exit codes (0, 1, 2, 3, 4) for different situations. Why is it useful for command-line utilities to return different codes instead of always returning 0 or 1? Give a practical example of how you might use these return codes in a shell script.

> _Building the program in this way instead of pass/fail makes system much more efficient to manage various outputs based on different input options. For shell script, this can be done by detecting code (like $code -eq 0) to echo different result messages._