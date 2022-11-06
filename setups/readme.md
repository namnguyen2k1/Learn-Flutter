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

### Đặc tên File, biến, class, function

- **File name**: snake case (home_screen.dart, cart_services.dart, cart_controller.dart,..)
- **Biến**: clamse

### Các bước cài đặc để code dự án tốt hơn

- Tạo model class:
  - Chuyển đổi dữ liệu json sang map và ngược lại. Đồng thời giúp flutter quản lý kiểu dữ liệu dễ dàng hơn.
  - Chuyển flutter khuyến khích dùng clameCase để đặc tên các thuộc tính
  - Một class thì có 2 hàm mặc định nên có là: `fromJson()` và `toJson()`

```dart

class ModelName {
  int id;
  // add more property
  String createdAt;
  String updatedAt;
  String deletedAt;

  ModelName({
    required this.id,
    required this.createdAt,
    required this.updatedAt,
    required this.deletedAt,
  });

  factory ModelName.fromJson(Map<String, dynamic> json) {
    return ModelName(
      id: json['id'] as int,
      // add more property
      createdAt: json['createdAt'] as String,
      updatedAt: json['updatedAt'] as String,
      deletedAt: json['deletedAt'] as String,
    );
  }

  Map<String, dynamic> toJson() {
    final json = <String, dynamic>{
      'id': id,
      // add more property
      'createdAt': createdAt,
      'updatedAt': updatedAt,
      'deletedAt': deletedAt,
    };
    return json;
  }
}
```

- Tạo các service:

  - Thao tác trực tiếp với dữ liệu cục bộ hoặc từ xa nhằm truy xuất, lưu trữ cập nhập dữ liệu.
  - Fetch api từ server (get, post, put, delete)
  - Đọc ghi file, chỉnh sửa nội dung file.

- Tạo controller (hoặc là manager, provider đều được)

  - Các class controller có nhiệm vụ giao tiếp giữa yêu cầu ui và service tương ứng.
  - controller thường kế thừa các gói quản lý dữ liệu (provider: changeNotifier) để cập nhập trạng thái dữ liệu của toàn bộ ứng dụng.
  - Business code được đặt trong các hàm của controller

- Tạo các lớp dữ liệu giả: (FakeData)

  - Cung cấp dữ liệu giả đến cho controller

- Tạo cấu hình navigator: go_router,..

  - Cấu hình điều hướng cho ứng dụng: bottomnavigationBar,...

- Tạo sẵn các trang màn hình (screen) định cài đặc
  - Mỗi màn hình screen đều phải được bao bọc bởi widget `Scaffold`()
