## Prefer_collection_literals

- Bad:

```dart
var points = List();
var addresses = Map();
var uniqueNames = Set();
var ids = LinkedHashSet();
var coordinates = LinkedHashMap();
```

- GOOD:

```dart
var points = [];
var addresses = <String,String>{};
var uniqueNames = <String>{};
var ids = <int>{};
var coordinates = <int,int>{};
```

## Một số nguồn lấy API free

- [Reqres](https://reqres.in/)
- [Json Placeholder](https://jsonplaceholder.typicode.com/)

## Tự động paste Json sang Model và ngược lại

- Thư viện sử dụng:

```bash
flutter pub add --dev json_annotation
```

```bash
flutter pub add --dev json_serializable
```

```bash
flutter pub add --dev build_runner
```

- Sử dụng tại file \*.model.dart:

```dart
import 'package:json_annotation/json_annotation.dart';
part 'course.model.g.dart'; // nơi code của hàm `_$CourseFromJson` được generage được render.

@JsonSerializable()
class Course {
  int id;
  @JsonKey(name: 'user_id') // Kiểu data response trả về
  int userId;
  @JsonKey(name: 'file_url')
  String fileUrl;

  Course({
    required this.id,
    required this.userId,
    required this.fileUrl
  });

// Đổi tên tương ứng với model: `_$CourseFromJson`
  factory Course.fromJson(Map<String, dynamic> json) => _$CourseFromJson(json);
  Map<String, dynamic> toJson() => _$CourseToJson(this);
}
```

- Gender Code: Chạy lại dòng này mỗi khi thay đổi code

```bash
flutter pub run build_runner watch
```

## Paste Json to Model online

- Convert here: [Json to Dart]('https://jsontodart.com/')
- Điểm cộng:
  - Thường thì khi xây dựng frontend đã có backend: nên chỉ cần lấy mẫu json chung nhất (getById,..) để copy
  - Đặc tên model và chọn convert
- Chỉnh sửa một số điểm:
  - Thêm giá trị default trong hàm `fromJson(...)`
  - Đổi `Map<String, dynamic>()` thành `<String, dynamic>{}`

## Template Model

- `Rule`:
  - Gía trị mặc định: String => 'default', int => 0, [link, null] => 'null'
  - Tên thuộc tính: createdAt
  - Tên trường json: created_at
  - Các hàm cơ bản: `fromJson()` , `toJson()`

```dart

class ___Model {
  int id;
  // add more property
  String createdAt;
  String updatedAt;
  String deletedAt;

  ___Model({
    required this.id,
    required this.createdAt,
    required this.updatedAt,
    required this.deletedAt,
  });

  factory ___Model.fromJson(Map<String, dynamic> json) {
    return ___Model(
      id: json['id'] ?? 0,
      // add more property
      createdAt: json['created_at'] ?? 'default',
      updatedAt: json['updated_at'] ?? 'null',
      deletedAt: json['deleted_at'] ?? 'null',
    );
  }

  Map<String, dynamic> toJson() {
    final json = <String, dynamic>{
      'id': id,
      // add more property
      'created_at': createdAt,
      'updated_at': updatedAt,
      'deleted_at': deletedAt,
    };
    return json;
  }
}

```
