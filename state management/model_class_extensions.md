### Tự động tạo Model với VS Code Extension

- Tải `Dart Data Class Generator` trong vs code
- Mở file settings.json: thêm vào 2 dòng

```json

  "dart_data_class_generator.hashCode.enabled": false,
  "dart_data_class_generator.equality.enabled": false
```

##### Tạo model từ class:

- Khai báo tên class, các thuộc tính cần thiết

```dart
class UserModel {
  final int id;
  final String name;
  final List<String> array;
  final String email;
}

```

- Gõ Ctrl + Shift + P: Gõ 'Dart Data Class Generator: Generate from class properties'

```dart
import 'dart:convert';

class UserModel {
  final int id;
  final String name;
  final List<String> array;
  final String email;
  UserModel({
    required this.id,
    required this.name,
    required this.array,
    required this.email,
  });

  UserModel copyWith({
    int? id,
    String? name,
    List<String>? array,
    String? email,
  }) {
    return UserModel(
      id: id ?? this.id,
      name: name ?? this.name,
      array: array ?? this.array,
      email: email ?? this.email,
    );
  }

  Map<String, dynamic> toMap() {
    return <String, dynamic>{
      'id': id,
      'name': name,
      'array': array,
      'email': email,
    };
  }

  factory UserModel.fromMap(Map<String, dynamic> map) {
    return UserModel(
      id: map['id'] as int,
      name: map['name'] as String,
      array: List<String>.from((map['array'] as List<String>)), // thiếu ")"
      email: map['email'] as String,
    );
  }

  String toJson() => json.encode(toMap());

  factory UserModel.fromJson(String source) =>
      UserModel.fromMap(json.decode(source) as Map<String, dynamic>);

  @override
  String toString() {
    return 'UserModel(id: $id, name: $name, array: $array, email: $email)';
  }
}

```

##### Tạo model từ JSON:

- Tạo file.dart, thêm vào nội dung là json cần parse

```json
{
  "id": 1,
  "name": "Nguyen Nam",
  "array": ["c", "a", "name"],
  "gender": true
}
```

- Gõ Ctrl + Shift + P: Gõ 'Dart Data Class Generator: Generate from JSON'
- Gõ tên model và nhấn enter

```dart
import 'dart:convert';

class UsesModel {
  final int id;
  final String name;
  final List<String> array;
  final bool gender;
  UsesModel({
    required this.id,
    required this.name,
    required this.array,
    required this.gender,
  });

  UsesModel copyWith({
    int? id,
    String? name,
    List<String>? array,
    bool? gender,
  }) {
    return UsesModel(
      id: id ?? this.id,
      name: name ?? this.name,
      array: array ?? this.array,
      gender: gender ?? this.gender,
    );
  }

  Map<String, dynamic> toMap() {
    return <String, dynamic>{
      'id': id,
      'name': name,
      'array': array,
      'gender': gender,
    };
  }

  factory UsesModel.fromMap(Map<String, dynamic> map) {
    return UsesModel(
      id: map['id'].toInt() as int,
      name: map['name'] as String,
      array: List<String>.from((map['array'] as List<String>), // thiếu `)`
      gender: map['gender'] as bool,
    );
  }

  String toJson() => json.encode(toMap());

  factory UsesModel.fromJson(String source) => UsesModel.fromMap(json.decode(source) as Map<String, dynamic>);

  @override
  String toString() {
    return 'UsesModel(id: $id, name: $name, array: $array, gender: $gender)';
  }
}
```

- Lưu ý: nếu json là mảng thì có khả năng bị lỗi, cần thêm dấu `)`
