#### Toán tử # (Stringification)
Toán tử ```#``` được sử dụng để biến một macro argument thành một chuỗi ký tự (string literal). Khi bạn áp dụng ```#``` trước một tham số của macro, tham số đó sẽ được chuyển đổi thành một chuỗi.
- Ví dụ:
```
#include <stdio.h>

#define STRINGIFY(x) #x

int main() {
    printf("%s\n", STRINGIFY(Hello World!));
    return 0;
}
```
- Kết quả: Hello World!

Trong ví dụ này, macro ```STRINGIFY(x)``` biến tham số ```x``` thành chuỗi ký tự. Khi gọi ```STRINGIFY(Hello World!)```, kết quả sẽ là ```"Hello World!"```.

#### Toán tử ## (Token-Pasting)
Toán tử ```##``` được sử dụng để kết hợp hai token lại với nhau thành một token duy nhất. Điều này hữu ích khi bạn muốn tạo tên biến hoặc hàm một cách động trong macro.

- Ví dụ:
```
#include <stdio.h>

#define CONCATENATE(x, y) x##y

int main() {
    int xy = 100;
    printf("%d\n", CONCATENATE(x, y)); // sẽ in ra giá trị của biến xy
    return 0;
}
```
- Kết quả: 100

Trong ví dụ này, macro ```CONCATENATE(x, y)``` kết hợp hai token ```x``` và ```y``` thành ```xy```. Khi gọi ```CONCATENATE(x, y)```, kết quả sẽ là token ```xy```, dẫn đến việc sử dụng biến ```xy``` trong hàm printf.

#### Toán tử defined
Toán tử defined được sử dụng trong các điều kiện của bộ tiền xử lý để kiểm tra xem một macro có được định nghĩa hay không. Nó thường được sử dụng cùng với các chỉ thị ```#if, #elif, #else, và #endif```.

- Ví dụ:
```
#include <stdio.h>

#define FEATURE_ENABLED

int main() {
    #if defined(FEATURE_ENABLED)
        printf("Feature is enabled.\n");
    #else
        printf("Feature is not enabled.\n");
    #endif
    return 0;
}
```
- Kết quả: Feature is enabled.

Trong ví dụ này, ```defined(FEATURE_ENABLED)``` kiểm tra xem macro ```FEATURE_ENABLED``` có được định nghĩa hay không. Nếu có, đoạn mã bên trong ```#if``` sẽ được biên dịch, ngược lại thì đoạn mã trong ```#else``` sẽ được biên dịch.

#### Toán tử #error và #warning
- #error: Toán tử này được sử dụng để tạo ra một thông báo lỗi trong quá trình tiền xử lý. Khi trình biên dịch gặp #error, nó sẽ dừng lại và thông báo lỗi được chỉ định.
- #warning: Một số trình biên dịch (không phải tất cả) hỗ trợ toán tử này để tạo ra một cảnh báo trong quá trình tiền xử lý, nhưng chương trình vẫn tiếp tục biên dịch.
- Ví dụ với ```#error```:
```
#include <stdio.h>

#define VERSION 3

#if VERSION < 4
    #error "Version is too old. Update required!"
#endif

int main() {
    printf("Version is up-to-date.\n");
    return 0;
}
```
- Kết quả: Trình biên dịch sẽ dừng lại và đưa ra thông báo lỗi: ```Version is too old. Update required!```

#### Toán tử #pragma
```#pragma``` được sử dụng để đưa ra các chỉ thị cụ thể cho trình biên dịch. Các chỉ thị này có thể khác nhau tùy thuộc vào trình biên dịch đang sử dụng.

- Ví dụ:
```
#pragma message("Compiling this file...")

int main() {
    return 0;
}
```
- Kết quả: Trình biên dịch sẽ hiển thị thông báo ```"Compiling this file..."``` trong quá trình biên dịch, nhưng chương trình vẫn sẽ biên dịch và chạy bình thường.
