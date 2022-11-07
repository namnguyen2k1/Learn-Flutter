## Sử dụng thư viện để parse json sang model và ngược lại

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
