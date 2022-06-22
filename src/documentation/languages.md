# Languages
Cart it out has it's own translation, we didn't use any package for the localization. It's serve same purpose with any other localization out there, but perhaps different approach.

## Adding New Text
To add new string into internalization dictionary, you can follow these steps.
1. First add key into `CoreLocalization` class inside `lib/common/core/core_localization.dart`
```dart
static const yourNewKeyHere = 'yourNewKeyHere';
```
2. Add translation into your key by adding text into each language files (current `string_id.dart` and `string_en.dart`), that  you can find inside `lib/common/consts/locale`. Then add text into `translations` variable inside each locale.
```dart
/// Indonesian translation
class StringId {
    ...
    static const translations = {
        ...
        CoreLocalization.yourNewKeyHere: 'Terjemahan baru kamu',
    };
}
```
```dart
/// English translation
class StringEn {
    ...
    static const translations = {
        ...
        CoreLocalization.yourNewKeyHere: 'Your new translation',
    };
}
```
And this is how to use the translation
```dart
/// Call static key then use .tr method
Text(CoreLocalization.yourNewKeyHere.tr),
/// The result is
/// Widget Text with 'Your new translation'
```
## Adding New Language
Sometimes we need more language for application, Cart it out already capable to load new language into the app. Just folow these step
1. Create new locale file inside `lib/common/consts/locale` example `string_es.dart` (spanish). With following format
```dart
class StringEs {
    /// Language code es
    static const languageCode = 'id';
    /// Country code (mexican)
    static const countryCode = 'MX';
    /// Add the const into `Locale`
    static const locale = Locale(
        languageCode,
        countryCode,
    );
    /// Spanish text translation for each key here, you can refer the key from
    /// `CoreTranslation` earlier
    static const translations = {
        ...
        /// Dont forget to adding translation text
    };
}
```
2. Add supported locale into `CoreLocalization` class inside `lib/common/core/core_localization.dart` on the `supportedLocales` variable
```dart
class CoreLocalization {
    ...
    static Iterable<Locale> get supportedLocales => [
        ...
        /// New locale
        StringEs.locale,
    ];
}
```
3. Add new flag asset for new language (Mexico) `mx.png` into `assets/images/flags`, then add the following file into `ImageAsset` class inside the `lib/common/consts/image_assets.dart`
```dart
class ImageAsset {
  ...
  /// Flag assets
  static String idFlag = '$baseFlagPath/id.png';
  static String ukFlag = '$baseFlagPath/uk.png';
  static String mxFlag = '$baseFlagPath/mx.png';
}
``` 
4. For proper language selector appearence, also add new label inside the `LocaleExtension` class on the file `lib/common/extensions/locale_extension.dart`
```dart
extension LocaleExtension on Locale {
    String get label {
        switch (countryCode) {
            ...
            /// Add new case for MX
            case 'MX':
                return 'Mexico';
            default:
                return 'United States';
        }
    }

    String get languageLabel {
        switch (countryCode) {
            ...
            /// Add new language label
            case 'ES':
                return 'Spanish';
            default:
                return 'English';
        }
    }

    String get image {
        switch (countryCode) {
            ...
            /// Add new flag
            case 'ES':
                return ImageAsset.esFlag;
            default:
                return ImageAsset.ukFlag;
        }
    }
}
```