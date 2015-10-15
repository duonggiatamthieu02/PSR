PSR-1 Basic Coding Standard
===========================
Những tiêu chuẩn của phần này bao gồm những gì được coi là chuẩn code.
Việc này đảm bảo một mức độ cao về khả năng tương tác của code PHP được chia sẻ.

### Tổng quan
* Files phải sử dụng thẻ `<?php` và `<?=`
* Files phải dùng *UTF-8 without BOM* cho code PHP
* Files chỉ nên khai báo các biểu tượng (như Class, Function, Constant, ...), hoặc để làm các việc phụ (như xuất ra màn hình, cấu hình, ...). Nhưng không được làm một lúc cả 2 việc.
* Namespaces và các class phải tuân theo `autoloading` PSR: [[PSR-0](https://github.com/runsystem-hiennt2/PSR/blob/master/PSR-0.md),[PSR-4](https://github.com/runsystem-hiennt2/PSR/blob/master/PSR-4.md)]
* Tên class phải khai báo theo `StudlyCaps`
* Tên constant phải khai báo tất cả viết hoa và ngăn cách bằng dấu gạch chân
* Tên method (function) phải khai báo theo `camelCase`

### Files
#### PHP tags
Code PHP phải dùng tag dài `<?php ?>` hoặc tag echo ngắn `<?= ?>`, không được dùng những tag với từ khóa khác.

#### Character Encoding
Code PHP phải chỉ dùng `UTF-8 without BOM`.

#### Side effects
Một file chỉ nên khai báo các biểu tượng (như Class, Function, Constant, ...) và không có những `side effects` khác, hoặc chỉ nên thực thi các logic với `side effects`, nhưng không được làm cả 2 việc.

Cụm từ `side effects` nghĩa là thực thi các logic không liên quan trực tiếp đến việc xây dựng Class, Function, Constant, ...

`Side effects` bao gồm: xuất ra màn hình, sử dụng `require` hoặc `include`, kết nối với services ngoài, chỉnh sửa file ini, bung ra các lỗi hoặc ngoại lệ, chỉnh sửa các biến toàn cục hoặc tĩnh, đọc hoặc viết ra file, và hơn nữa.
