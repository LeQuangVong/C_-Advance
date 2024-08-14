#### Khái niệm Function Pointer
Một function pointer là một biến lưu trữ địa chỉ của một hàm. Không giống như con trỏ thông thường, con trỏ hàm không trỏ đến dữ liệu mà trỏ đến mã thực thi.
Kiểu của function pointer phụ thuộc vào kiểu trả về và danh sách tham số của hàm mà nó trỏ đến.
#### Cách khai báo Function Pointer
Cú pháp khai báo function pointer trong C:
```
return_type (*pointer_name)(parameter_types);
```
Trong đó:

- ```return_type``` là kiểu trả về của hàm mà con trỏ trỏ đến.
- ```pointer_name``` là tên của con trỏ hàm.
- ```parameter_types``` là danh sách các kiểu tham số mà hàm nhận.
#### Ví dụ về Function Pointer
Khai báo và sử dụng function pointer
```
#include <stdio.h>

// Hàm cộng hai số nguyên
int add(int a, int b) {
    return a + b;
}

// Hàm trừ hai số nguyên
int subtract(int a, int b) {
    return a - b;
}

int main() {
    // Khai báo một con trỏ hàm trỏ đến hàm nhận hai tham số int và trả về int
    int (*operation)(int, int);

    // Gán địa chỉ của hàm add cho con trỏ hàm
    operation = &add;

    // Gọi hàm add thông qua con trỏ hàm
    int result = operation(5, 3);
    printf("Kết quả của phép cộng: %d\n", result);

    // Gán địa chỉ của hàm subtract cho con trỏ hàm
    operation = &subtract;

    // Gọi hàm subtract thông qua con trỏ hàm
    result = operation(5, 3);
    printf("Kết quả của phép trừ: %d\n", result);

    return 0;
}
```
#### Sử dụng function pointer trong mảng hàm
Sử dụng một mảng các function pointer để chọn hàm thực thi động:
```
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int multiply(int a, int b) {
    return a * b;
}

int main() {
    // Khai báo một mảng các con trỏ hàm
    int (*operations[3])(int, int) = {add, subtract, multiply};

    int choice, a = 10, b = 5;
    printf("Chọn phép tính: 0=Add, 1=Subtract, 2=Multiply\n");
    scanf("%d", &choice);

    if (choice >= 0 && choice < 3) {
        int result = operations[choice](a, b);
        printf("Kết quả: %d\n", result);
    } else {
        printf("Lựa chọn không hợp lệ.\n");
    }

    return 0;
}
```
#### Ưu điểm của Function Pointer
- Tính linh hoạt: Function pointer cho phép bạn thay đổi hàm được gọi một cách linh động tại runtime, điều này rất hữu ích trong các chương trình phức tạp hoặc có yêu cầu động.
- Gọn gàng và rõ ràng: Bạn có thể quản lý và tổ chức mã nguồn tốt hơn, đặc biệt trong các trường hợp cần thực hiện nhiều chức năng khác nhau dựa trên các điều kiện hoặc tham số đầu vào.