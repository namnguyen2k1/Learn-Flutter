# Hướng dẫn cài đặc môi trường lập trình Flutter

## 1. Tải các ứng dụng

- `Git`: [git_download](https://git-scm.com/downloads)
- `Flutter SDK`: [flutter_download](https://docs.flutter.dev/get-started/install/windows#get-the-flutter-sdk)
- `Visual Studio Code`: [vscode_download](https://code.visualstudio.com/download)
- `Android Studio`: [android_download](https://developer.android.com/studio)

#### 1.1 Git - Setup

- Kiểm tra phiên bản:

  ```bash
  git --version
  ```

  > git version 2.37.2.windows.2

- Cấu hình username và email: [git_link](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
  ```bash
  git config --global user.name "[your username]"
  git config --global user.email [your email]
  ```
- Kiểm tra cấu hình đã thiết lập:

  ```bash
  git config --list
  ```

- Sử dụng chi tiết: [git_github_beginners](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)
- Ngoài ra khi thao tác lần đầu trên thiết bị mới git sẽ yêu cầu làm theo một số yêu cầu bảo mật.

#### 1.2 Flutter SDK - Setup

- Cài đặc biến môi trường:
  - Giải nén lấy thư mục `flutter`, lấy đường dẫn trỏ đến thư mục `bin`
  - This PC -> Properties -> Advanced Setting -> Environment Setup -> ... Tạo mới biến và paste đường dẫn vừa copy vào.
- Kiêm tra phiên bản:
  ```bash
  flutter --version
  ```
- Kiểm tra thiết bị đã có:
  ```bash
  flutter doctor
  ```
- Vì flutter có thể build app đa nền tảng, nên tuỳ nền tảng mà tải thêm các ứng dụng tương ứng:

  - `Web App`: Chrom, Edge,..
  - `Desktop App`: Visual Studio.
  - `Android`: Android Studio (Dùng Emulator) hoặc Điện thoại thật.

    - Riêng Android, cần chấp nhận bản quyền của họ: chạy câu lệnh

    ```bash
    flutter doctor --android-licenses
    ```

#### 1.3 Visual Studio Code - Setup

- Kiểm tra cài đặc:

  ```bash
  code --version
  ```

- Tải thêm các extension hỗ trợ code Flutter: [extension_link](https://docs.flutter.dev/get-started/editor?tab=vscode)

  - `Dart`: Dart Code extends VS Code with support for the Dart programming language, and provides tools for effectively editing, refactoring, running, and reloading Flutter mobile apps. [dart_install](https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code)
  - `Flutter`: This VS Code extension adds support for effectively editing, refactoring, running, and reloading Flutter mobile apps. It depends on (and will automatically install) the Dart extension for support for the Dart programming language. [flutter_install](https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter)

- Các tiện ích sẽ được hiển thị sau khi mở file `.dart`
- Xem các tiện ích: **Ctrl Shift P** - Gõ **fluter** ...
- Chạy ứng dụng flutter:
  - Chọn thiết bị: Web, Emulator, Mobile,..
  - Chọn `Run Without Debugging`
  - Mở `Terminal`, xem tab `Debug Console`

#### 1.4 Android Studio - Setup

- Sau khi cài đặc xong, mở app lên, chọn `more option` -> `SDK manager`
- Tải thêm về máy các thư viện và tool:

  - `Android SDK Command-line Tools (lastest)`
  - `Android 12.0 (S)`
  - `Android Emulator`
  - `Google Play Intel x86 Atom_64 System Image`

- Debug: Tạo máy ảo với Emulator:

  - Chọn các loại thiết bị có biểu tượng CH Play vì dễ đưa lên chợ ứng dụng
  - Ram phải đủ, ít nhất là 8GB, ổ đĩa cài đặc dư hơn 20GB
  - Không nên bậc thêm các app khác trong khi chờ quá trình tạo máy ảo
  - `Tip`: Đặt máy ảo luôn ở trên cùng màn hình: `Settings` -> Tick chọn `Emulator always on top`

- Debug: Kết nối trên điện thoại thật: [read_link](https://docs.flutter.dev/get-started/install/windows#set-up-your-android-device)
  - Ở điện thoại thật: Click 5-7 lần vào `Số hiệu bản tạo`. Kích hoạt chế độ nhà phát triển,
  - Kết nối với máy tính qua USB. Vào `Cài đặc dành cho nhà phát triển`, chọn chế độ `Debug qua USB`
  - Điện thoại sẽ tạo ra mã `RSA`. Chấp nhận.
  - Mở Visual Studio Code lên và chọn thiết bị, lúc này thiết bị điện thoại đã được tạo.
  - Lần đầu chạy project có thể lâu (5-10p) do tải thêm cái thư viện.
