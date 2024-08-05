### Extern Variable
- Scope: Extern variables have global scope, meaning they can be accessed from any file in the program after being declared.
- Definition and Declaration: An extern variable must be defined in one location, and it can be declared in multiple locations. The definiton allocates memory for the variable, while the declaration informs the compiler about the variable's existance without allocating memory.
- Storage Duration: Extern variable have static duration, which means their memory is allocated when the program starts and deallocated when the program ends.

Ex:
```file1.c```:
```
#include <stdio.h>

int globalVariable = 10;  // Definition of the global variable

void printGlobalVariable() {
    printf("Global Variable: %d\n", globalVariable);
}
```
```file2.c```:
```
#include <stdio.h>

extern int globalVariable;  // Declaration of the global variable

void modifyGlobalVariable() {
    globalVariable = 20;
}
```
```main.c```:
```
#include <stdio.h>

void printGlobalVariable();
void modifyGlobalVariable();

int main() {
    printGlobalVariable();  // Print the initial value of the global variable
    modifyGlobalVariable(); // Modify the value of the global variable
    printGlobalVariable();  // Print the new value of the global variable
    return 0;
}
```
- ```file1.c```: Defines the ```globalVariable``` and allocate memory for it. The function ```printGlobalVariable``` prints its value.
- ```file2.c```: Declare the ```globalVariable``` using the ```extern``` keyword, indicating that it is defined elsewhere. The function ```modifyGlobalVariable``` modifies its value.
- ```main.c```: Call the functions ```printGlobalVariable``` and ```modifyGlobalVariable``` to demonstrate accessing and modifying the global variable from different files.
