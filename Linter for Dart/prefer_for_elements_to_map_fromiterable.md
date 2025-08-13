Pattern: Missing use of `for` when building map from iterable

Issue: -

## Description

When building maps from iterables, it is preferable to use for elements.

Example of **incorrect** code:
```dart
Map<String, WidgetBuilder>.fromIterable(
 kAllGalleryDemos,
 key: (demo) => '${demo.routeName}',
 value: (demo) => demo.buildRoute,
);

```

Example of **correct** code:
```dart
return {
 for (var demo in kAllGalleryDemos)
  '${demo.routeName}': demo.buildRoute,
};
```

## Further Reading

* [Linter for Dart - prefer_for_elements_to_map_fromIterable](https://dart.dev/tools/linter-rules/prefer_for_elements_to_map_fromIterable)
