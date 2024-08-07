#### Restrict
the restrict keyword is used to indicate that a pointer is the only reference to a particular memory location within a certain scope. This allows the compiler to perform optimizations based on the assumption that no other pointers will access the same memory, which can improve performance.

Syntax
```
type *restrict pointer_name;
```
Ex:
```
void updateArray(int *restrict arr, int size) {
    for (int i = 0; i < size; i++) {
        arr[i] = i;
    }
}
```
In this example, arr is a restrict pointer. This tells the compiler that within the scope of updateArray, arr is the only pointer accessing the memory it points to. This can enable optimizations such as eliminating redundant memory accesses.
#### Benefits of ```restrict```
- Performance Optimization: The primary benefit of restrict is that it allows the compiler to perform optimizations based on the assumption that the memory pointed to by restrict pointers is not accessed by other pointers.
- Avoiding Redundant Memory Accesses: By ensuring that memory accesses through restrict pointers are exclusive, the compiler can avoid unnecessary memory load/store operations.
#### When to Use ```restrict```
- Performance-Critical Code: Use restrict in performance-critical sections of code where pointer aliasing could prevent optimizations.
- When You Are Certain: Only use restrict when you are certain that the pointers do not alias, as incorrect use can lead to undefined behavior.