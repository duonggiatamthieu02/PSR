PSR-3: [Logger Interface](https://github.com/php-fig/log)
=========================================================
Tài liệu này mô tả một khuôn mẫu chung cho các thư viện ghi log.

Mục đích chính là cho phép thư viện nhận một đối tượng `Psr\Log\LoggerInterface` và ghi log vào nó một cách dễ dàng và bao quát.

### 1. Specification
#### 1.1 Basics
* `LoggerInterface` trình bày 8 phương thức để ghi log, ứng với 8 level: debug, info, notice, warning, error, critical, alert, emergency.
* Một phương thức thứ 9 - `log` - chấp nhận `log level` với đối số thứ đầu tiên.
Gọi phương thức này với một hằng số `log level` phải tương ứng với một trong 8 level trên kia.
Nếu một `log level` không được định nghĩa thì phải bung ra lỗi `Psr\Log\InvalidArgumentException` nếu không biết level nào cả.

#### 1.2 Message
* Mỗi phương thức chấp nhận một string ứng với message, hoặc object với phương thức `__toString()`.
`Implementors` có thể có những xử lý đặc biệt cho những object. Trường hợp khác, `implementors` phải chuyển sang một string.
* Message có thể chứa `placeholder` (giống [sprintf](http://php.net/manual/en/function.sprintf.php)) mà `implementors` phải thay thế bằng `value` từ mảng `context`.

Tên của `placeholder` phải tương ứng với tên key trong mảng `context`.

Được phân cách bởi mở và đóng ngoặc nhọn, không có whitespace nào liền kề bên trong ngoặc nhọn.

Và phải chỉ dùng các ký tự `A-Z`, `a-z`, `0-9`, gạch chân `_`, và dấu chấm `.`.

`Implementors` có thể dùng `placeholders` để phiên dịch khi ghi log.

Sau đây là ví dụ của việc sử dụng `Placeholder`:
```php
/**
 * Interpolates context values into the message placeholders.
 */
function interpolate($message, array $context = array())
{
    // build a replacement array with braces around the context keys
    $replace = array();
    foreach ($context as $key => $val) {
        $replace['{' . $key . '}'] = $val;
    }
    // interpolate replacement values into the message and return
    return strtr($message, $replace);
}

// a message with brace-delimited placeholder names
$message = "User {username} created";

// a context array of placeholder names => replacement values
$context = array('username' => 'bolivar');

// echoes "User bolivar created"
echo interpolate($message, $context);
```
