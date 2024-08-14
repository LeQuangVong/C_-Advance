#### Khái niệm về Void Pointer
Một con trỏ void được khai báo bằng cách sử dụng từ khóa void*.
Ví dụ:
```
void *ptr;
```
- Kích thước: Con trỏ ```void``` có kích thước giống như bất kỳ con trỏ nào khác, vì nó chỉ lưu trữ địa chỉ bộ nhớ, không phải kiểu dữ liệu cụ thể.
- Ép kiểu: Để truy cập dữ liệu mà con trỏ ```void``` trỏ tới, bạn phải ép kiểu con trỏ đó sang kiểu dữ liệu cụ thể trước khi thao tác.
#### Ví dụ về Void Pointer
Sử dụng Void Pointer để trỏ đến các kiểu dữ liệu khác nhau
```
#include <stdio.h>

int main() {
    int a = 10;
    float b = 5.5;
    char c = 'A';

    void *ptr;

    // Trỏ đến một biến kiểu int
    ptr = &a;
    printf("Giá trị của a = %d\n", *(int *)ptr);

    // Trỏ đến một biến kiểu float
    ptr = &b;
    printf("Giá trị của b = %.2f\n", *(float *)ptr);

    // Trỏ đến một biến kiểu char
    ptr = &c;
    printf("Giá trị của c = %c\n", *(char *)ptr);

    return 0;
}
```
#### Void Pointer trong hàm tổng quát
Sử dụng con trỏ void trong một hàm tổng quát để in ra giá trị của bất kỳ kiểu dữ liệu nào:

```
#include <stdio.h>

void printValue(void *ptr, char type) {
    switch (type) {
        case 'i': // Nếu kiểu int
            printf("Giá trị kiểu int: %d\n", *(int *)ptr);
            break;
        case 'f': // Nếu kiểu float
            printf("Giá trị kiểu float: %.2f\n", *(float *)ptr);
            break;
        case 'c': // Nếu kiểu char
            printf("Giá trị kiểu char: %c\n", *(char *)ptr);
            break;
        default:
            printf("Kiểu không được hỗ trợ\n");
    }
}

int main() {
    int a = 10;
    float b = 3.14;
    char c = 'Z';

    printValue(&a, 'i');
    printValue(&b, 'f');
    printValue(&c, 'c');

    return 0;
}
```
#### Ưu điểm và Nhược điểm của Void Pointer
- Ưu điểm:
    - Tính linh hoạt: Một con trỏ void có thể trỏ đến bất kỳ kiểu dữ liệu nào, cho phép bạn viết các hàm và cấu trúc dữ liệu tổng quát.
    - Tiết kiệm bộ nhớ: Trong một số trường hợp, việc sử dụng con trỏ void có thể giúp giảm kích thước mã nguồn và sử dụng tài nguyên hiệu quả hơn.
- Nhược điểm:
    - Không thể thực hiện phép toán con trỏ trực tiếp: Do không có kiểu dữ liệu cụ thể, bạn không thể thực hiện các phép toán con trỏ như cộng, trừ trực tiếp trên con trỏ void mà không ép kiểu trước.
    - Thiếu kiểm tra kiểu dữ liệu: Vì void không có kiểu, trình biên dịch không thể kiểm tra lỗi về kiểu dữ liệu trong quá trình biên dịch, dẫn đến việc dễ xảy ra lỗi thời gian chạy nếu không ép kiểu chính xác.
    