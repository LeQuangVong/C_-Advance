### Auto Variable
- Scope: The scope of an auto variables is limited to the block in which it is declared. This mean it can only be accessed within the function or block where it is defined.
- Lifetime: The lifetime of an auto variables is the duration of the block in which it is declared. When the block is exited, the variable is automatically destroyed.
- Storage: Auto variables are stored on the stack.
- Initialization: Auto variables are not automatically initialized to zero. If not explicitly initialized, they contain garbage values.

Ex:
```
#include <stdio.h>

void Function() {
    auto int a = 5;   // 'auto' keyword is redundant (dư thừa) here
    int b = 10;       // Equivalent (tương đương) to 'auto int b = 10;'
    
    printf("a = %d, b = %d\n", a, b);
}

int main() {
    Function();
    return 0;
}
```