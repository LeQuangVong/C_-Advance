### Static variable
Static variable can have different meanings depending on whether it is declared within a function or outside of all functions.
#### Static variable in Functions
When declared inside a function, a static variable retains its value between functions calls. Its scope is limited to the function in which it is declared, but is lifetime is the entire program execution.
```
#include <stdio.h>

void countCalls()
{
    static int count = 0;// Static variable declaration
    count++;
    printf("Function called %d times\n", count);
}

int main()
{
    countCalls();
    countCalls();
    countCalls();
    return 0;
}
```
Output:
```
Function called 1 times
Function called 2 times
Function called 3 times
```
#### Static Global Variables
When declared outside of any function, a static variable's scope is limited to the file in which it is declared, making it a "file-scope" variable. This is useful for encapsulating the variable and preventing it from being accessed from other files.
```
#include <stdio.h>

static int globalVar = 0; // Static global variable

void incrementGlobalVar() {
    globalVar++;
    printf("Global variable is now %d\n", globalVar);
}

int main() {
    incrementGlobalVar();
    incrementGlobalVar();
    return 0;
}
```
Output:
```
Global variable is now 1
Global variable is now 2
```