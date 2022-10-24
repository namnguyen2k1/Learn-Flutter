# Cấu trúc thư mục dự án Flutter

### Các Nguồn Tham Khảo:

- [medium](https://medium.com/flutter-community/flutter-scalable-folder-files-structure-8f860faafebd)
- [geeksforgeek](https://www.geeksforgeeks.org/flutter-file-structure/)

### Goal

- Dựa trên kinh nghiệm code Web và một thời gian tìm hiểu về flutter, tôi nảy ra ý tưởng về cấu trúc thư mục cho riêng mình. **Áp dụng cho các dự án vừa và nhỏ**
- Mỗi thư mục mang ý nghĩa như sau:
  - `assets`: Chứa các tài nguyên (hình ảnh, font,..) dùng trong ứng dụng
  - `configs`: Cấu hình chung cho ứng dụng (lấy biến môi trường,...)
  - `states`:
    - `models`: Nhận data từ services trả về, paste sang object để sử dụng trong ứng dụng
    - `controllers`: Chức các xử lý khi user tương tác với ui (cập nhập trạng thái, sử dụng data lấy từ api,...)
    - `services`: Sử lý fetch Api từ Network giữa Client và Server qua Http Protocol.
  - `ui`: Render giao diện người dùng
    - `shared`: Kho widget dùng chung, sử dụng mọi nơi khi cần.
    - `routes`: Cấu hình tuyến đường trong ứng dụng.
    - `themes`: Cấu hình các theme dùng trong ứng dụng: `Dark Theme`, `Light Theme`
    - `screens`: Các trang tương ứng trong ứng dụng, trong đó mỗi trong là một thư mục
- Chi tiết hơn hãy đọc file `readme.md` trong từng thư mục

## Flutter Widget Template

- Blog
  - [started_with_flutter](https://www.raywenderlich.com/24499516-getting-started-with-flutter#toc-anchor-001)
  - [Started_quickly_with_Flutter](https://github.com/Temidtech/Flutter-Cheat-Sheet)
