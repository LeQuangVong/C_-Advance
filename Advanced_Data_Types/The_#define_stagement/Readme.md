### #define
The ```#define``` is a preprocessor directive used to define macros. Macros are essentially a way to give a name to a piece of code, a constant, or a set of instructions that you want to reuse throughout your program. When the compiler encounters a macro, it replaces the macro name with the defined value or code before actual compilation begins.

Type of Macros:
- Object-like Macros: These are simple constants or pieces of code.
- Function-like Macros: These resemble functions but are expanded inline wherever they are used.

#### Object-like Macros:
Object-like Macros are used to define constants or pieces of code. The syntax is:
```
#define NAME value
```
Ex:
```
#include <stdio.h>

#define PI 3.14159
#define GREETING "Hello, World!"

int main() {
    printf("Value of PI: %f\n", PI);
    printf("%s\n", GREETING);
    return 0;
}
```
#### Function-like Macros:
Function-like macros are used to define macros that take arguments and can be used like function. The syntax is:
```
#define NAME(parameters) code
```
Ex:
```
#include <stdio.h>

#define SQUARE(x) ((x) * (x))
#define MAX(a, b) ((a) > (b) ? (a) : (b))

int main() {
    int num = 5;
    printf("Square of %d: %d\n", num, SQUARE(num));
    printf("Max of %d and %d: %d\n", 3, 7, MAX(3, 7));
    return 0;
}
```
#### Important point:
- No Semicolon: Unlike regular C statement, ```define``` does not end with a semicolon.
- Global Scope: Macros are replaced throughout the entire program unless they are underfined using ```#undef```
- No Type Checking: Since macros are replaced by text, there is no type checking, which can lead to unexpected results or bugs if not used carefully.
- Preprocessor Derective: The ```define``` directive is handled by the preprocessor, which means it occurs before the compilation stage.
