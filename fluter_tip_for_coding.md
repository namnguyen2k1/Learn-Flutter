# Flutter Tip

- Read more: [Flutter Tip]('https://dart.dev/guides/language/effective-dart/usage')

## Một số nguồn lấy API free

- [Reqres](https://reqres.in/)
- [Json Placeholder](https://jsonplaceholder.typicode.com/)

## Một số mẹo giúp code dễ dàng hơn

- Bỏ dòng Debug trên góc phải của thiết bị: Tại `main.dart`, thêm vào dòng:

```dart
return MaterialApp(
  debugShowCheckedModeBanner: false,
);
```

- Bỏ qua cảnh báo wraning khi dùng hàm print(): Tại file `analysis_options.yaml` bỏ commment tại dòng:

```yaml
rules:
  avoid_print: false # Uncomment to disable the `avoid_print` rule
  # prefer_single_quotes: true  # Uncomment to enable the `prefer_single_quotes` rule
```

- Truy cập localhost ở trên thiết bị thật:

  - Địa chỉ `localhost` phải được đổi thành địa chỉ ip trên máy tính đê có thể gửi request
  - Mặt khác máy tính và thiết bị phải sử dụng chung 1 mạng (trường hợp này dùng điện thoại phát wifi cho máy tính)

```dart
// Trên máy ảo
String baseUrl = 'http://localhost:3000/api/';

// Trên máy thật: đổi `localhost` thành địa chỉ ip của máy tính:
// Xem ip: cmd -> ipconfig  (Windows)
String baseUrl = 'http://192.168.0.26:3000/api/';
```

- Prefer_collection_literals

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

- Chèn khoảng cách giữa các phần tử:

  - `SizeBox()`: Dùng để chèn một khoảng cách cố định vào giữa các phần tử, ngoài ra có thể chứa thêm phần tử con

  ```dart
  Column(
    children: <Widget>[
      Widget1(),
      SizedBox(height: 10), // <-- Set height
      Widget2(),
    ],
  )
  ```

  - `Spacer()`: Thường được dùng trong widget Colum`n` và `Row`, đặc thuộc tính flex để có thể điều chỉnh khoảng cách giữa các phần tử
  - [Spacer_Youtube]('https://youtu.be/7FJgd7QN1zI')

  ```dart
  Column(
    children: <Widget>[
      Widget1(),
      Spacer(),
      Widget2(),
    ],
  )
  ```

  - `Wrap()`: dùng để gói các phần tử, ngăn cách việc tràn dòng

  ```dart
  Wrap(
    direction: Axis.vertical,
    spacing: 20,
    children: <Widget>[
      Widget1(),
      Widget2(),
    ],
  )
  ```

- Style cho widget `Container()`: padding, margin, backgroundColor, border, boxShadow, borderRadius,..

```dart
margin: const EdgeInsets.all(10),
padding: const EdgeInsets.all(10),
decoration: const BoxDecoration(
  color: Colors.grey,
  border: Border(
    top: BorderSide(
      color: Colors.white, // Set border color
      width: 1.0,
    ),
  ),
  image: DecorationImage(
    image: AssetImage(
      'assets/images/wellcome.gif',
    ),
    fit: BoxFit.cover,
  ),
  borderRadius: BorderRadius.all(Radius.circular(10.0)),
  boxShadow: [
    BoxShadow(color: Colors.deepOrange, spreadRadius: 3)
  ],
),
```
