Dynamic memory in C refers to the process of allocating and freeing memory during the execution of a program. Dynamic memory allows a program to manage memory more flexibly, adapting to changing memory requirements at runtime.
#### Functions for Dynamic Memory Management
##### Malloc:
- Allocates a block of uninitialized memory.
```
void* malloc(size_t size);
```
##### Calloc:
- Allocates memory for an array and initializes all elements to zero.
```
void* calloc(size_t num, size_t size);
```
##### Realloc:
- Changes the size of a previously allocated memory block.
```
void* realloc(void* ptr, size_t size);
```
##### Free:
- Frees allocated memory.
```
void free(void* ptr);
```
#### Examples:
- Malloc:
```
#include <stdlib.h>

int main() {
    int *arr;
    arr = (int*) malloc(10 * sizeof(int));  // Allocate memory for 10 int elements

    if (arr == NULL) {
        // Check if allocation failed
        return 1;
    }

    // Use the memory
    for (int i = 0; i < 10; i++) {
        arr[i] = i;
    }

    // Free the memory
    free(arr);

    return 0;
}
```
- Calloc:
```
#include <stdlib.h>

int main() {
    int *arr;
    arr = (int*) calloc(10, sizeof(int));  // Allocate memory for 10 elements and initialize to zero

    if (arr == NULL) {
        // Check if allocation failed
        return 1;
    }

    // Use the memory
    for (int i = 0; i < 10; i++) {
        arr[i] = i;
    }

    // Free the memory
    free(arr);

    return 0;
}
```
- Realloc:
```
#include <stdlib.h>

int main() {
    int *arr;
    arr = (int*) malloc(5 * sizeof(int));  // Allocate memory for 5 elements

    if (arr == NULL) {
        // Check if allocation failed
        return 1;
    }

    // Use the memory
    for (int i = 0; i < 5; i++) {
        arr[i] = i;
    }

    // Resize the memory block
    arr = (int*) realloc(arr, 10 * sizeof(int));  // Resize to 10 elements

    if (arr == NULL) {
        // Check if reallocation failed
        return 1;
    }

    // Use the new memory
    for (int i = 5; i < 10; i++) {
        arr[i] = i;
    }

    // Free the memory
    free(arr);

    return 0;
}
```
#### Note:
- Check Allocation Results: Always check the results of malloc, calloc, and realloc to ensure that memory has been successfully allocated.
- Free Memory: After using dynamically allocated memory, always free it using free to avoid memory leaks.
- Initialize Memory: malloc does not initialize memory, while calloc initializes memory to zero.