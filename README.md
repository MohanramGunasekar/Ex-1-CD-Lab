# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
# AIM :
## To write a C program to implement a symbol table.
# ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol is inserted into symbol table along with its memory address.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8.	Stop the program. 
# PROGRAM
```
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

// Main function
int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *p, *add[5];
    char ch, srch, b[15], d[15], c;

    // Input expression from user
    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$') {
        b[i] = c;
        i++;
    }
    b[i] = '\0';  // Null-terminate the string
    n = i - 1;

    // Display the given expression
    printf("Given Expression: ");
    for (i = 0; i <= n; i++) {
        printf("%c", b[i]);
    }
    printf("\n");

    // Display Symbol Table header
    printf("\nSymbol Table\n");
    printf("Symbol\tAddr\tType\n");

    // Analyze the expression to create the symbol table
    for (j = 0; j <= n; j++) {
        c = b[j];
        if (isalpha(c)) { // Check if the symbol is an identifier
            if (j == n || (b[j+1] == '+' || b[j+1] == '-' || b[j+1] == '*' || b[j+1] == '=')) {
                p = malloc(sizeof(char)); // Allocate memory
                if (p == NULL) {
                    printf("Memory allocation failed\n");
                    return 1;
                }
                add[x] = p; // Store address
                d[x] = c;   // Store symbol
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }

    // Search for a symbol in the table
    printf("\nEnter the symbol to be searched: ");
    scanf(" %c", &srch);

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c @address %p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (flag == 0)
        printf("Symbol Not Found\n");

    // Free allocated memory
    for (i = 0; i < x; i++) {
        free(add[i]);
    }

    return 0;
}
```
# OUTPUT

![Screenshot 2024-09-26 141439](https://github.com/user-attachments/assets/4e5850d4-12be-4a16-aace-bbf7ea766ee3)

# RESULT
### The program to implement a symbol table is executed and the output is verified.
