### Register Variable
- Faster Access: A ```register``` variable may be stored in a CPU register, making access faster compared to a variable stored in RAM.
- No Address Access: You cannot use the ```&``` operator to get the address of a ```register``` variable because registers do not have memory address.
- Scope: ```register``` variables are typically used for local variables within a function, especially those that are frequently accessed within loops.
- Litmited Number: The number of CPU registers is limited, so only a few variables can be stored as ```register```. The compiler decides which variables will actually be stored in registers based on various factors.
```
#include <stdio.h>

void sumOfArrayElement()
{
    int arr[5] = {1,2,3,4,5};
    register int sum = 0;
    register int i;
    
    for(i = 0; i < 5; i++)
    {
        sum += arr[i];
    }

    printf("Sum of array elements: %d\n", sum);
}

int main()
{
    sumOfArrayElement();
    return 0;
}
```