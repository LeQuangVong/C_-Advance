### STACK 
- Description: The stack is region of memory that operates in a LIFO (Last In, First Out) manner (cơ chế). It is a used to store local variables, function parameters, and return addresses (các thông tin liên quan đến lời gọi hàm).
- Management: Stack memory is automatically managed by the compiler and the operating system. When a function is called, its local variables are pushed onto the stack. When the function returns, its local variables are automatically popped off.
- Speed: Access to the stack is fast due to its simple and well-defined management.
- Size: the size of stack is typically limited by the operating system and can lead to stack overflow if too much memory is used.
Ex:
    ```
    void Function() {
        int localVariable = 10;  // Local variable stored on the stack
        // Other operations
    }
    ```

### HEAP
- Desciption: The heap is region of memory used for dynamic memory allocation during runtime of the program.
- Management: Heap memory is not automatically managed. Programmers must manually allocate and free memory using functions like ```malloc```, ```calloc```, ```realloc``` (for allocation), and ```free``` (for deallocation).
- Speed: Accress to the heap is slower than the stack due to the complexily of managing memory.
- Size: The head is more flexible in size and can be larger than the stack, but it is still limited by the operatign system and system resources.

Ex:
```
#include <stdlib.h>

void exampleFunction() {
    int *dynamicArray = (int *)malloc(10 * sizeof(int));  // Dynamic memory allocation on the heap
    if (dynamicArray != NULL) {
        // Use the array
        free(dynamicArray);  // Free the allocated memory
    }
}
```

### Specific Comparison

| Characteristic    | Stack                                | Heap                                       |
|-------------------|--------------------------------------|--------------------------------------------|
| Memory Management | Automatic                            | Manual                                     |
| Speed             | Fast                                 | Slower                                     |
| Usage Scope       | Local variables, function parameters | Dynamic memory allocation                  |
| Scalability       | Limited (Prone to stack overflow)    | Flexible, can be larger (but defend on OS) |
| Management Method | LIFO (Last In, First Out)            | Free-form                                  |

