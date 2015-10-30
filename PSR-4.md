PSR-4: Autoloader
=================

### 1. Overview
PSR này mô tả đặc điểm kỹ thuật cho những class `autoloading` từ những đường dẫn file.
Nó hoàn toàn tương thích và có thể dùng bổ sung cho bất kỳ những `autoloading` khác, bao gồm cả [PSR-0](https://github.com/runsystem-hiennt2/PSR/blob/master/PSR-0.md).
PSR này cũng mô tả nơi đặt những file mà có thể tự động load.

### 2. Specification
1. Định nghĩa `class` đề cập đến các Class, Interface, Trait và các cấu trúc tương tự khác.
2. Một tên class đầy đủ phải theo dạng sau:

  ```
  \<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>
  ```
  a. Một tên class đầy đủ phải có tên namespace cấp cao nhất, cũng có thể hiểu như một **vendor namespace**.
  b. abc
3. Khi load một file mà nó tương ứng với tên class đầy đủ...
