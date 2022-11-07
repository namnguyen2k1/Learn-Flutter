## Một số cách để chèn khoảng cách giữa các phần tử

- Chèn khoảng cách giữa các phần tử:

  - `Divider()`: Dùng để vạch 1 đường kẻ ngăn cách các phần tử

  ```dart
  Column(
    children: <Widget>[
      Divider(),
      Text('Hello'),
      Divider(),
      Text('Hello'),
      Divider(),
    ],
  )
  ```

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

  - `Spacer()`: Được dùng trong widget `Colum` và `Row`, đặc thuộc tính flex sẽ chia khoảng cách giữa các phần tử dựa trên tỉ lệ hiện có giữa các Spacer()
  - [Spacer_Youtube]('https://youtu.be/7FJgd7QN1zI')

  ```dart
  Column(
    children: <Widget>[
      Spacer(flex: 2),
      Widget1(),
      Spacer(flex: 1),
      Widget2(),
      Spacer(flex: 2),
    ],
  )
  ```
