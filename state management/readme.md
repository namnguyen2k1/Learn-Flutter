## Paste Json to Model online

- Convert here: [Json to Dart](https://jsontodart.com/)
- Điểm cộng:
  - Thường thì khi xây dựng frontend đã có backend: nên chỉ cần lấy mẫu json chung nhất (getById,..) để copy
  - Đặc tên model và chọn convert
- Chỉnh sửa một số điểm:
  - Thêm giá trị default trong hàm `fromJson(...)`
  - Đổi `Map<String, dynamic>()` thành `<String, dynamic>{}`

## Template Model

- `Rule`:

  - Gía trị mặc định: Một số trường có thể không tồn tại hoặc null, cần gắn giá trị mặc định cho nó

    - link: 'empty',
    - `updatedAt`, `deletedAt`: 'null',

  - Tên thuộc tính: createdAt
  - Tên trường json: createdAt (Không nên dùng kiểu snake case như created_at)
  - Các hàm cơ bản: `fromJson()` , `toJson()`

```dart

class ModelName {
  final int id;
  // add more property
  final String createdAt;
  final String updatedAt;
  final String deletedAt;

  ModelName({
    required this.id,
    required this.text,
    required this.createdAt,
    required this.updatedAt,
    required this.deletedAt,
  });

  factory ModelName.fromJson(Map<String, dynamic> json) {
    return ModelName(
      id: json['id'] as int,
      // add more property
      createdAt: json['createdAt'] as String,
      updatedAt: json['updatedAt'] as String ?? 'null',
      deletedAt: json['deletedAt'] as String ?? 'null',
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
