#### Khái niệm Double Pointer
Một con trỏ thông thường là một biến lưu trữ địa chỉ của một giá trị hoặc một biến khác. ```Double pointer``` là một con trỏ lưu trữ địa chỉ của một con trỏ, tức là con trỏ cấp 2.

Nếu ```int* p``` là con trỏ trỏ đến một biến kiểu ```int```, thì ```int** pp``` là một con trỏ trỏ đến ```p```.

#### Cách khai báo Double Pointer
Khai báo double pointer giống như khai báo một con trỏ thông thường, nhưng có thêm một dấu *:
```
int** pp;
```
Ở đây, ```pp``` là một ```double pointer``` trỏ đến một con trỏ kiểu ```int```.

#### Ví dụ về Double Pointer
```
#include <stdio.h>

int main() {
    int a = 10;     // Khai báo một biến kiểu int
    int *p;         // Khai báo một con trỏ trỏ đến biến kiểu int
    int **pp;       // Khai báo một con trỏ trỏ đến một con trỏ trỏ đến int

    p = &a;         // p trỏ đến a (lưu địa chỉ của a)
    pp = &p;        // pp trỏ đến p (lưu địa chỉ của p)

    // Hiển thị giá trị của a thông qua pp
    printf("Giá trị của a: %d\n", a);          // Trực tiếp
    printf("Giá trị của a thông qua p: %d\n", *p);  // Thông qua p
    printf("Giá trị của a thông qua pp: %d\n", **pp); // Thông qua pp

    return 0;
}
```
Trong ví dụ trên:

- ```a``` là một biến kiểu ```int``` với giá trị 10.
- ```p``` là một ```con trỏ``` trỏ đến ```a```.
- ```pp``` là một ```double pointer``` trỏ đến ```p```.
#### Thay đổi giá trị của con trỏ trong hàm
Khi muốn thay đổi giá trị của một con trỏ (để nó trỏ đến một địa chỉ khác) bên trong một hàm, bạn cần sử dụng double pointer.
```
#include <stdio.h>
#include <stdlib.h>

void allocateMemory(int **ptr) {
    *ptr = (int *)malloc(sizeof(int));  // Cấp phát bộ nhớ cho con trỏ trỏ đến
    **ptr = 100;  // Gán giá trị cho vùng nhớ đã cấp phát
}

int main() {
    int *p = NULL;

    allocateMemory(&p);  // Truyền địa chỉ của con trỏ p vào hàm

    printf("Giá trị được lưu trữ trong vùng nhớ p trỏ đến: %d\n", *p);

    // Giải phóng bộ nhớ sau khi sử dụng
    free(p);

    return 0;
}
```
Trong ví dụ này:

- ```allocateMemory()``` là hàm sử dụng ```double pointer``` ```int **ptr``` để cấp phát bộ nhớ cho con trỏ được truyền vào.
- Bên trong hàm, con trỏ ```p``` được cập nhật để trỏ đến vùng nhớ mới được cấp phát.
#### Làm việc với mảng động nhiều chiều
Double pointer thường được sử dụng để xử lý mảng động hai chiều trong C.
```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int rows = 3, cols = 4;
    int **matrix;

    // Cấp phát bộ nhớ cho các hàng của ma trận
    matrix = (int **)malloc(rows * sizeof(int *));
    
    // Cấp phát bộ nhớ cho các cột của mỗi hàng
    for (int i = 0; i < rows; i++) {
        matrix[i] = (int *)malloc(cols * sizeof(int));
    }

    // Gán giá trị cho ma trận
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            matrix[i][j] = i * cols + j;
        }
    }

    // Hiển thị giá trị ma trận
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }

    // Giải phóng bộ nhớ
    for (int i = 0; i < rows; i++) {
        free(matrix[i]);
    }
    free(matrix);

    return 0;
}
```
Trong ví dụ này:

- ```matrix``` là một ```double pointer```, được sử dụng để tạo ra một mảng động hai chiều.
- Bộ nhớ cho các hàng và cột của ma trận được cấp phát động, và sau đó được giải phóng sau khi sử dụng.