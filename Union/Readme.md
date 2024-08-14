Union là một kiểu dữ liệu trong C và C++ cho phép bạn lưu trữ các kiểu dữ liệu khác nhau trong cùng một vùng nhớ. Điểm đặc biệt của union so với struct là tất cả các thành viên của union đều dùng chung một vùng nhớ, nghĩa là tại một thời điểm, chỉ có một trong các thành viên của union có thể chứa giá trị có ý nghĩa.

#### Cú pháp của union
```
union union_name {
    data_type1 member1;
    data_type2 member2;
    ...
};
```
- `union_name`: Tên của union.
- `data_type`: Kiểu dữ liệu của thành viên (ví dụ: int, float, char, v.v.).
- `member`: Tên của thành viên union.
#### Ví dụ về union
```
#include <stdio.h>

union Data {
    int i;
    float f;
    char str[20];
};

int main() {
    union Data data;

    data.i = 10;
    printf("data.i : %d\n", data.i);

    data.f = 220.5;
    printf("data.f : %.1f\n", data.f);

    snprintf(data.str, sizeof(data.str), "Hello");
    printf("data.str : %s\n", data.str);

    return 0;
}
```
- Giải thích:
    - data.i: Thành viên i của union data được gán giá trị 10.
    - data.f: Khi gán data.f là 220.5, giá trị của data.i không còn hợp lệ nữa, vì f và i dùng chung một vùng nhớ.
    - data.str: Khi gán data.str là "Hello", giá trị của data.f cũng không còn hợp lệ.
- Kết quả:
```
data.i : 10
data.f : 220.5
data.str : Hello
```
- Lưu ý: Vì các thành viên chia sẻ cùng một vùng nhớ, nên khi một thành viên mới được gán giá trị, giá trị của các thành viên khác có thể bị thay đổi hoặc không còn hợp lệ.

#### Kích thước của union
Kích thước của một union được xác định bởi kích thước của thành viên lớn nhất của nó. Ví dụ, nếu một union có một int (4 bytes) và một double (8 bytes), thì kích thước của union đó sẽ là 8 bytes.

- Ví dụ:
```
#include <stdio.h>

union Example {
    int i;
    double d;
    char c;
};

int main() {
    printf("Kích thước của union: %lu bytes\n", sizeof(union Example));
    return 0;
}
```
- Kết quả:
Kích thước của union: 8 bytes
#### Union vs Struct
- Memory Usage: Với `struct`, mỗi thành viên chiếm một vùng nhớ riêng, vì vậy kích thước của `struct` là tổng kích thước của tất cả các thành viên. Với `union`, tất cả các thành viên dùng chung một vùng nhớ, vì vậy kích thước của `union` bằng với kích thước của thành viên lớn nhất.

- Use Case: `Union` thường được sử dụng khi bạn muốn tiết kiệm bộ nhớ và bạn biết chắc rằng chỉ cần một trong các thành viên của `union` tại bất kỳ thời điểm nào. `Struct` thường được dùng khi bạn cần lưu trữ và truy cập nhiều thành viên cùng một lúc.

#### Một số ứng dụng của union
- Type Punning: Union có thể được sử dụng để thực hiện type punning, tức là xem một vùng nhớ dưới nhiều kiểu dữ liệu khác nhau. Ví dụ, bạn có thể lưu một giá trị int trong một union và sau đó đọc nó như một float để thấy cách máy tính lưu trữ các số.

- Variant Data Types: Union thường được sử dụng trong việc xử lý dữ liệu biến thể, nơi một biến có thể lưu trữ nhiều kiểu dữ liệu khác nhau tùy thuộc vào ngữ cảnh.

- Efficient Memory Use: Union giúp tiết kiệm bộ nhớ khi bạn chỉ cần một giá trị tại một thời điểm, điều này rất hữu ích trong các hệ thống nhúng hoặc khi xử lý các gói dữ liệu.
