# Theming
Cart it out by default using Material 3, all of the text styles, widgets, the color schemes, is created to be support Material 3 Color scheme. Before continue for theming we are recommend you to take some basic knowledge from [Material 3 Official](https://m3.material.io/). And also by default Cart it out has `DarkMode` cool isn't it ?
## ColorScheme
You can find the color scheme on the file `lib/common/utils/theme_util.dart` inside the class `ThemeUtil` there is a two color scheme `light` and `dark`. Its very swap-able, to change the color scheme again we will recommend to take a look into [Material 3 color guidelines](https://m3.material.io/styles/color/overview). There is two options for change the color scheme, first generate a color, or add your own color directly to the `ThemeUtil`. Both of them must change the `ColorScheme` inside the `darkColorScheme` or `lightColorScheme`
::: warning
All of the widget inside Cart It Out template is already using (Centralized theme) with Global Theme and Local Theme override, changing the `ColorScheme` may also affect all of them.
:::
```dart
class ThemeUtil {
    ...
    /// ColorScheme
    ColorScheme get lightColorScheme => ColorScheme(
        brightness: Brightness.light,
        primary: Color(0xFF0046FA),
        onPrimary: Color(0xFFFFFFFF),
        primaryContainer: Color(0xFFDDE1FF),
        onPrimaryContainer: Color(0xFF00105A),
        secondary: Color(0xFF750CFF),
        onSecondary: Color(0xFFFFFFFF),
        secondaryContainer: Color(0xFFEBDCFF),
        onSecondaryContainer: Color(0xFF23005B),
        tertiary: Color(0xFFB0008F),
        onTertiary: Color(0xFFFFFFFF),
        tertiaryContainer: Color(0xFFFFD7EE),
        onTertiaryContainer: Color(0xFF3A002F),
        error: Color(0xFFB3261E),
        errorContainer: Color(0xFFF9DEDC),
        onError: Color(0xFFFFFFFF),
        onErrorContainer: Color(0xFF410E0B),
        background: Color(0xFFFFFFFF),
        onBackground: Color(0xFF1C1B1F),
        surface: Color(0xFFFDFBFF),
        onSurface: Color(0xFF1C1B1F),
        surfaceVariant: Color(0xFFEFF0FF),
        onSurfaceVariant: Color(0xFF49454F),
        outline: Color(0xFF79747E),
        onInverseSurface: Color(0xFFF4EFF4),
        inverseSurface: Color(0xFF313033),
        inversePrimary: Color(0xFFB8C4FF),
        shadow: Color(0xFF000000),
    );

    ColorScheme get darkColorScheme => ColorScheme(
        brightness: Brightness.dark,
        primary: Color(0xFFB8C4FF),
        onPrimary: Color(0xFF00208F),
        primaryContainer: Color(0xFF0031C5),
        onPrimaryContainer: Color(0xFFDDE1FF),
        secondary: Color(0xFFD3BBFF),
        onSecondary: Color(0xFF3D0091),
        secondaryContainer: Color(0xFF5800C9),
        onSecondaryContainer: Color(0xFFEBDCFF),
        tertiary: Color(0xFFFFADE2),
        onTertiary: Color(0xFF5F004D),
        tertiaryContainer: Color(0xFF87006D),
        onTertiaryContainer: Color(0xFFFFD7EE),
        error: Color(0xFFF2B8B5),
        errorContainer: Color(0xFF8C1D18),
        onError: Color(0xFF601410),
        onErrorContainer: Color(0xFFF9DEDC),
        background: Color(0xFF1C1B1F),
        onBackground: Color(0xFFE6E1E5),
        surface: Color(0xFF1B1B1F),
        onSurface: Color(0xFFE6E1E5),
        surfaceVariant: Color(0xFF45464F),
        onSurfaceVariant: Color(0xFFCAC4D0),
        outline: Color(0xFF938F99),
        onInverseSurface: Color(0xFF1C1B1F),
        inverseSurface: Color(0xFFE6E1E5),
        inversePrimary: Color(0xFF0046FA),
        shadow: Color(0xFF000000),
    );
}
```
Then to retrieve the color for your widget component you can use vanilla approach using context
```dart
/// Primary color for MaterialButton
MaterialButton(
    color : Theme.of(context).colorScheme.primary,
    ...
),
```

## DarkMode
By default Cart It Out has Dark mode, the default configuration of is stored inside `GlobalProvider`. To flip between light and dark you can use `GlobalProvider` method
```dart
Provider<GlobalProvider>.of(context, false).switchThemeMode();
```