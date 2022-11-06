## Một số nguồn lấy API free

- [Reqres](https://reqres.in/)
- [Json Placeholder](https://jsonplaceholder.typicode.com/)

### **Avoid Print**:

- Tại file `analysis_options.yaml` bỏ commment tại dòng:

```yaml
rules:
  avoid_print: false # Uncomment to disable the `avoid_print` rule
  # prefer_single_quotes: true  # Uncomment to enable the `prefer_single_quotes` rule
```

### **Access Localhost**

- Địa chỉ `localhost` phải được đổi thành địa chỉ ip trên máy tính đê có thể gửi request
- Mặt khác máy tính và thiết bị phải sử dụng chung 1 mạng (trường hợp này dùng điện thoại phát wifi cho máy tính)

```dart
// Trên máy ảo
String baseUrl = 'http://localhost:3000/api/';

// Trên máy thật: đổi `localhost` thành địa chỉ ip của máy tính:
// Xem ip: cmd -> ipconfig  (Windows)
String baseUrl = 'http://192.168.0.26:3000/api/';
```

### **Prefer Collection Literals**

```dart
// Bad
var points = List();
var addresses = Map();
var uniqueNames = Set();
var ids = LinkedHashSet();
var coordinates = LinkedHashMap();

// Good
var points = [];
var addresses = <String,String>{};
var uniqueNames = <String>{};
var ids = <int>{};
var coordinates = <int,int>{};
```

# Refactor Source Code

- Do cấu trúc code của flutter phải lồng các widget vào nhau, nên nhìn chung rất khó bảo trì. Chúng ta có thể convert sang dạng local varriable hoặc sang dạng method hoặc là class widget
  - `Refactor into method`:
    Text buildHello() => Text('Hello');
  - `Refactor into widget`:
    Tận dụng được các benifits của widget lifecycle, ngăn chặn lại việc render không cần thiết

# State Management

- Quản lý trạng thái trong cùng 1 widget: Có thể dùng StatefullWidget
- Quản lý trạng thái toàn bộ ứng dụng: State Management:
  - **Provider**: Đưa tất cả trạng thái lên đầu cây thư mục flutter, mỗi khi thay đổi data, flutter sẽ tự động render lại widgets bị changed
  - **GetIt**: Tạo một đối tượng để tất cả các widget có thể truy xuất đến nó (Một biến cục bộ)
  - **Bloc**: Xu hướng hiện nay: https://somniosoftware.com/post/fundamentals-of-the-the-bloc-pattern

## Để lưu trữ dữ liệu cục bộ:

- `shared_preferences`: Lưu trữ dữ liệu trong Ram của ứng dụng Android.
- `sqflite`: Lưu trữ thông tin trong file

## Lưu trữ từ xa:

- `Rest API`: Get, Put, Post, Delete,.. => Backend -> Frontend | Mobile,...
- `SDK`: Firebase Google,...

## Shortcut Key

- Wrap Widget: Ctrl + Shift + R: Build sang local varriable, method or widget (ful, less)

### **Flutter Tip**

- Kỹ thuật sử dụng Constructor để truyền data từ widget cha xuống widget con người ta gọi là `Passing state down`

- Dùng const ngay khi có thể

  - Giá trị được gán vào thời điểm khởi tạo. Trong khi final thì có thể gán giá trị vào thời điểm runtime
  - Widget cha đã dùng const thì ở widget con không cần dùng. Sử dụng const sẽ hiệu quả khi hot reload lại ứng dụng khi coding
  - Không sử dụng const khi không cần thiết

- Read more: [Flutter Tip]('https://dart.dev/guides/language/effective-dart/usage')
