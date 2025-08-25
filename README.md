# Ex. No : 1

# IMPLEMENTATION OF SYMBOL TABLE

# Register Number : 212223110058

# Date :25/08/2025

# AIM:

To write a C program to implement a symbol table.

# ALGORITHM:

1. Start the program.
2. Get the input from the user with the terminating symbol ‘$’.
3. Allocate memory for the variable by dynamic memory allocation function.
4. If the next character of the symbol is an operator then only the memory is allocated.
5. While reading, the input symbol is inserted into symbol table along with its memory address.
6. The steps are repeated till ‘$’ is reached.
7. To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8. Stop the program.

# PROGRAM:

#include <iostream>
#include <cctype>
#include <cstring>
using namespace std;

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void* add[50];   // store addresses
    char b[MAX_EXPRESSION_SIZE], d[50], c, srch;

    cout << "Enter the Expression terminated by $: ";
    while ((c = cin.get()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; 
    n = i - 1;

    cout << "Given Expression: " << b << "\n";

    cout << "\nSymbol Table\n";
    cout << "Symbol\taddr\t\ttype\n";

    for (j = 0; j <= n; j++) {
        c = b[j];
        if (isalpha(static_cast<unsigned char>(c))) {
            if (j == n) {
                void* p = new char;
                add[x] = p;
                d[x] = c;
                cout << c << "\t" << p << "\tidentifier\n";
                x++;
            } else {
                char ch = b[j + 1];
                if (ch == '+' || ch == '-' || ch == '*' || ch == '=') {
                    void* p = new char;
                    add[x] = p;
                    d[x] = c;
                    cout << c << "\t" << p << "\tidentifier\n";
                    x++;
                }
            }
        }
    }

    cout << "\nThe symbol to be searched: ";
    cin >> srch;

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            cout << "Symbol Found\n";
            cout << srch << "@address " << add[i] << "\n";
            flag = 1;
        }
    }

    if (flag == 0)
        cout << "Symbol Not Found\n";

    for (i = 0; i < x; i++) {
        delete static_cast<char*>(add[i]);
    }

    return 0;
}

# OUTPUT:

<img width="1153" height="490" alt="Screenshot 2025-08-25 112229" src="https://github.com/user-attachments/assets/0803b626-4f59-4a6b-9504-7d219e89280f" />

<img width="984" height="421" alt="image" src="https://github.com/user-attachments/assets/cbb1f5ff-d5b3-4d7e-a4b9-4c2f40ba7d06" />



# RESULT:

The program to implement a symbol table is executed and the output is verified.
