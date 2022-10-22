## Đường dẫn

- Import đường dẫn dùng Quick Fix => Crash App
- Fix: Sử dụng đường dẫn tuyệt đối: `package:[app_name]/folder/.../[file_name].dart`

## Địa chỉ localhost ở trên thiết bị:

- Địa chỉ `localhost` phải được đổi thành địa chỉ ip trên máy tính đê có thể gửi request
- Mặc khác máy tính và thiết bị phải sử dụng chung 1 mạng (th này dùng điện thoại phát wifi cho máy tính)

```dart
String baseUrl = 'http://localhost:3000/api/';

// Đổi thành địa chỉ ip của máy tính: cmd -> ipconfig  (Windows)
String baseUrl = 'http://192.168.0.26:3000/api/';
```

## Một số vấn đề khác:

- Các bài viết của user đăng trong profile sẽ đặc trong forum mặc định là: `following` (với user khác) và `study` (với teacher)
- Tạo thêm table: `user_forum`: {user_id, forum_id, role_id} để thể hiện quyền trong forum (tương tự trong room: leader, member,..)
  => Trang Home sẽ bao gồm: các bài viết từ người đang theo dõi (student, teacher) và các bài viêt trong forum mà bản thân là thành viên. Bản chất là các bài viết từ các forum: `following`, `study`, `private_forum`

- Đổi api getAllRelationOfUser => getAllBlockingOfUser: lấy danh sách các thành viên đã block
- Trang profile: Thêm tabbar trong body: trong đó có các mục: friends, followings, followers, blocking
  - Mỗi mục có thêm nút delete để xoá khi cần thiết
