## Một số vấn đề khi sử dụng sqflite trong flutter

### Một file sql có thể khai báo nhiều table

- Chỉ nên khai báo tối đa 10 table để đảm bảo hiệu suất đọc ghi csdl

```dart
Future<void> _createDefaultTables(Database db, int version) async {
    // Create category table
    await db.execute(
      '''CREATE TABLE $_categoryTableName (
      id $idType,
      name $textType,
      code $textType,
      description $textType,
      imageUrl $textType,
      color $textType,
      createdAt $textType
    )''',
    );

    // Create task table
    await db.execute(
      '''CREATE TABLE $_taskTableName (
      id $idType,
      categoryId $foreignType,
      name $textType,
      star $integerType,
      color $textType,
      description $textType,
      imageUrl $textType,
      workingTime $textType,
      createdAt $textType,
      isCompleted $integerType,
      FOREIGN KEY (categoryId) REFERENCES $_categoryTableName(id)
    )''',
    );

    // Create more table here ..
  }
```

### Kiểu bool không hỗ trợ trên sqflite

- sqflite chỉ hỗ trợ kiểu TEXT, INTEGER

### Load dữ liệu từ file cục bộ

- Thêm controller tại hàm main()

```dart
Future<void> main() async {
  WidgetsFlutterBinding.ensureInitialized();

  // Load data from sqflite
  await CategoryController().getAll();
  await TaskController().getAll();

  runApp(const MyApp());
}
```

### Tạo singleton

- Ngăn class tạo nhiều instance: SharedPrefrences, ReadFile
- Mỗi tác vụ vớI controller chỉ thực thi qua duy nhất một dịch vụ

```dart
static final SqfliteService instance = SqfliteService._sharedInstance();
SqfliteService._sharedInstance();
```

### Kết quả trả về của của các hàm

- `insert`: Trả về id của item mới thêm vào
- `update`: Trả về số phần tử được cập nhập
- `delete`: Trả về số phần từ đã bị xoá
