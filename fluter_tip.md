# Flutter Tip

- Read more: [Flutter Tip]('https://dart.dev/guides/language/effective-dart/usage')

### Bỏ dòng bugmode trên cùng thiết bị

- Tại file `main.dart`: Thêm vào dòng

```dart
// ...
return MaterialApp(
  debugShowCheckedModeBanner: false,
);
```

### Chèn Khoảng Trống giữa các Widget

- Sử dụng SizedBox():

```dart
 Column(
   children: <Widget>[
     Widget1(),
     SizedBox(height: 10), // <-- Set height
     Widget2(),
   ],
 )
```

- Sử dụng Spacer:

```dart
Column(
  children: <Widget>[
    Widget1(),
    Spacer(),
    Widget2(),
  ],
)
```

- Sử dụng Expanded

```dart
Column(
  children: <Widget>[
    Widget1(),
    Expanded(child: SizedBox.shrink()),
    Widget2(),
  ],
)
```

- Set mainAxisAlignment

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.spaceAround,
  children: <Widget>[
    Widget1(),
    Widget2(),
  ],
)
```

- Sử dụng Wrap

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

- Style cho Container

```dart
decoration: const BoxDecoration(
  image: DecorationImage(
    image: AssetImage(
      'assets/images/wellcome.gif',
    ),
    fit: BoxFit.cover,
  ),
  borderRadius: BorderRadius.all(Radius.circular(10.0)),
  boxShadow: [
    // BoxShadow(color: Colors.deepOrange, spreadRadius: 3)
  ],
),

decoration: const BoxDecoration(
    color: Colors.grey,
    border: Border(
      top: BorderSide(
        color: Colors.white, // Set border color
        width: 1.0,
      ),
    ),
  ),
```

- padding:

```dart
padding: const EdgeInsets.all(10),
```

- Margin

```dart
margin: const EdgeInsets.all(10),
```

- Không thể vừa đặc color và color trong decoration cùng nhau trong container widget
