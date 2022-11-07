### CustomeTheme Flutter

- Mặc định các màu sắc có sẵn được cung cấp bởi flutter không đáp ứng như cầu thực tế, cần phải tuỳ chỉnh lại => Kế thừa và tuỳ biến các thành phần giao diện

- Tạo file lightTheme.dart

```dart
import 'package:flutter/material.dart';

class LightTheme {
  static final value = ThemeData.light().copyWith(
    primaryColor: Colors.white70,
    backgroundColor: Colors.teal[900],
    splashColor: Colors.transparent,
    highlightColor: Colors.transparent,
    hoverColor: Colors.transparent,
    appBarTheme: AppBarTheme(
      backgroundColor: Colors.teal[900],
    ),
    tabBarTheme: TabBarTheme(
      indicator: BoxDecoration(
          borderRadius: BorderRadius.circular(
            15.0,
          ),
          color: Colors.teal,
          border: Border.all(
            color: Colors.green,
            width: 2.0,
          )),
      labelColor: Colors.black,
      unselectedLabelColor: Colors.grey,
    ),
    bottomAppBarColor: Colors.black54,
    focusColor: Colors.green,
    floatingActionButtonTheme: const FloatingActionButtonThemeData(
      foregroundColor: Colors.black,
      backgroundColor: Colors.teal,
    ),
    elevatedButtonTheme: ElevatedButtonThemeData(
      style: ElevatedButton.styleFrom(
        backgroundColor: Colors.teal,
      ),
    ),
    textSelectionTheme: const TextSelectionThemeData(
      cursorColor: Colors.teal,
    ),
    inputDecorationTheme: InputDecorationTheme(
      prefixIconColor: Colors.teal[700],
      suffixIconColor: Colors.teal[700],
      floatingLabelStyle: TextStyle(color: Colors.teal[700], fontSize: 20),
      counterStyle: TextStyle(color: Colors.teal[700], fontSize: 20),
      enabledBorder: const OutlineInputBorder(
        borderSide: BorderSide(
          width: 1,
          color: Colors.grey,
        ),
      ),
      focusedBorder: OutlineInputBorder(
        borderSide: BorderSide(
          width: 1,
          color: Colors.teal[700]!,
        ),
      ),
    ),
  );
}
```

- Tạo file darkTheme.dart

```dart
import 'package:flutter/material.dart';

class DarkTheme {
  static final value = ThemeData.dark().copyWith(
    primaryColor: Colors.black54,
    backgroundColor: Colors.black54,
    appBarTheme: const AppBarTheme(
      backgroundColor: Colors.black54,
    ),
    splashColor: Colors.transparent,
    highlightColor: Colors.transparent,
    hoverColor: Colors.transparent,
    tabBarTheme: TabBarTheme(
      labelStyle: const TextStyle(fontSize: 20.0, fontWeight: FontWeight.bold),
      indicator: BoxDecoration(
          borderRadius: BorderRadius.circular(
            15.0,
          ),
          color: Colors.orange,
          border: Border.all(
            color: Colors.deepOrange,
            width: 2.0,
          )),
      labelColor: Colors.black,
      unselectedLabelColor: Colors.white60,
    ),
    bottomAppBarColor: Colors.grey,
    focusColor: Colors.deepOrange,
    floatingActionButtonTheme: const FloatingActionButtonThemeData(
      foregroundColor: Colors.black,
      backgroundColor: Colors.orange,
    ),
    elevatedButtonTheme: ElevatedButtonThemeData(
      style: ElevatedButton.styleFrom(
        backgroundColor: Colors.orange,
      ),
    ),
    textSelectionTheme: const TextSelectionThemeData(
      cursorColor: Colors.deepOrange,
    ),
    inputDecorationTheme: const InputDecorationTheme(
      prefixIconColor: Colors.deepOrange,
      suffixIconColor: Colors.deepOrange,
      floatingLabelStyle: TextStyle(color: Colors.deepOrange, fontSize: 20),
      counterStyle: TextStyle(color: Colors.deepOrange, fontSize: 20),
      enabledBorder: OutlineInputBorder(
        borderSide: BorderSide(
          width: 1,
          color: Colors.grey,
        ),
      ),
      focusedBorder: OutlineInputBorder(
        borderSide: BorderSide(
          width: 1,
          color: Colors.deepOrange,
        ),
      ),
    ),
  );
}
```

- Tạo file theme.dart sử dụng các tuỳ chỉnh được khai báo

```dart
import './light_theme.dart';
import './dark_theme.dart';

class AppTheme {
  static final light = LightTheme.value;
  static final dark = DarkTheme.value;
}
```

- Theme là biến được sử dụng cho toàn bộ ứng dụng, nên cần đưa lên trên cùng (Material App). trường hợp sử dụng theme với provider để theo dõi trạng thái theme của ứng dụng:

```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';
import './state/controllers/app_settings_controller.dart';
import './ui/themes/theme.dart';

Future<void> main() async {
  WidgetsFlutterBinding.ensureInitialized();

  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MultiProvider(
      providers: [
        ChangeNotifierProvider(
          create: (ctx) => AppSettingsController(),
        ),
      ],
      child: Consumer<AppSettingsController>(
        builder: (ctx, appSettingsController, child) {
          return MaterialApp(
            // ...
            theme: appSettingsController.isDarkTheme
                ? AppTheme.dark
                : AppTheme.light,
            // ...
          );
        },
      ),
    );
  }
}
```
