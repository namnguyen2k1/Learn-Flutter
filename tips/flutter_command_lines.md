# Flutter Command-line

- Xem thêm: [Flutter_Command_Line_Tools](https://docs.flutter.dev/reference/flutter-cli)

### 1. Kiểm tra tương thích sdk, thiết bị, ide

```bash
flutter doctor
```

- Liệt kê chi tiết hơn:

```bash
flutter doctor -v
```

- Nhận danh sách các thiết bị hỗ trợ bởi `flutter sdk`

```bash
flutter devices
```

- Kiểm tra máy ảo `Emulator`

```bash
flutter emulator
```

- Hỗ trợ:

```bash
flutter --help
```

### 2. Tạo mới project:

- Tạo project mặc định: Bao gồm các thư mục `web`, `window`, `linux`, `ios`, `android`

```bash
fluter new [project_name]
```

- Tạo project cho android: Hỗ trợ `Java` và `Kotlin` (mặc định)

```bash
flutter create --org=com.navoki --android-language=java [project_name]
```

- Tạo projectcho ios: Hỗ trợ `Objective C` và `Swift` (mặc định)

```bash
flutter create --org=com.navoki --ios-language=objc [project_name]
```

- Chạy project_name:
  - cd vào thư mục chứa project
  - chọn device, mở terminal và nhập lệnh

```bash
flutter run
```

- Chạy project trên thiết bị cụ thể:

```bash
flutter run -d [device_id]
```

- Chạy project trên thiết bị cụ thể với chế độ xem chi tiết

```bash
flutter run -d [device_id] -v
```

### 2.1 Quản lý thư việc

- Tải các thư viện trong file `pubspec.yaml`

```bash
flutter install
```

- Hoặc:

```bash
flutter pub get
```

- Tải thư viện vào dependencies:

```bash
flutter pub add [package_name]
```

- Tải thư viện vào dev_dependencies:

```bash
flutter pub add --dev [package_name]
```

- Nâng cấp các thư viện:

```bash
flutter upgrade
```

- Hoặc:

```bash
flutter pub upgrade
```

- Kiểm tra các thư viện hết hạn:

```bash
flutter pub outdated
```

- Xoá Cache: Sau khi chạy cần phải các package lại: flutter pub get

```bash
flutter clean
```

### 3. Thêm hỗ trợ nền tảng khác

- Thêm nền tảng `Windows`

```bash
flutter create --platforms=windows .
```

- Thêm nền tảng `MacOS`

```bash
flutter create --platforms=macos .
```

- Thêm nền tảng `Linux`

```bash
flutter create --platforms=linux .
```

- Thêm nền tảng `Web`

```bash
flutter create --platforms=web .
```

### 4. Chuyển kênh

- Flutter có nhiều nhóm để sử dụng riêng. Kiểm tra các kênh:

```bash
flutter channel
```

```bash
-- out-put
Flutter channels:
  master
  beta
* stable
```

- Chuyển kênh cụ thể:

```bash
flutter channel [channel_name]
```

### 5. Cấu hình Flutter

- Bậc cấu hình dành cho web

```bash
flutter config --enable-web
```

- Đặc lại cấu hình:

```bash
flutter config  --clear-features
```

### 6. Định dạng Flutter

- Định dạng tất cả các file trong dự án

```bash
flutter format .
```

### 7. Build App in Production

- Build sang `target_platform_name`

```bash
flutter build [target_platform_name] --release
```
