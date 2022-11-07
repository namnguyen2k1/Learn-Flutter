### Đây là một thư viện dùng để lưu trữ dữ liệu dạng key-value trên hệ điều hành android

- Các hàm cơ bản mà thư viện cung cấp

```dart
import 'package:shared_preferences/shared_preferences.dart';

class SharedKey {
  static const authTokenKey = 'auth_token';
  static const localAccountKey = 'local_account';
  static const appThemeKey = 'app_theme';
  static const appLanguageKey = 'app_language';
  static const appAutoReplayPomodoroKey = 'app_replay_pomodoro';
}

class SharedPreferencesSerivce {
  Future<void> setString(String key, String data) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    await sharedPreferences.setString(key, data);
  }

  Future<void> setStringList(String key, List<String> data) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    await sharedPreferences.setStringList(key, data);
  }

  Future<void> setInt(String key, int data) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    await sharedPreferences.setInt(key, data);
  }

  Future<void> setBool(String key, bool data) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    await sharedPreferences.setBool(key, data);
  }

  // Get data by key
  Future<String> getString(String key) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    return sharedPreferences.getString(key) ?? 'empty';
  }

  Future<List<String>> getStringList(String key) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    return sharedPreferences.getStringList(key) ?? <String>[];
  }

  Future<int> getInt(String key) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    return sharedPreferences.getInt(key) ?? -1;
  }

  Future<bool> getBool(String key) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    return sharedPreferences.getBool(key) ?? false;
  }

  // Delete data with key
  Future<bool> removeStorage(String key) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    return sharedPreferences.remove(key);
  }

  // Check exist Key
  Future<bool> isExisted(String key) async {
    SharedPreferences sharedPreferences = await SharedPreferences.getInstance();
    return sharedPreferences.containsKey(key);
  }
}
```
