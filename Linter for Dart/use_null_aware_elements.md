Pattern: Missing use of null-aware element

Issue: -

## Description

Where possible, use null-aware elements in collection literals.

Example of **incorrect** code:

```dart
f(String? key) => {if (key != null) key: "value"};
```

Example of **correct** code:

```dart
f(String? key) => {?key: "value"};
```

## Further Reading

* [Linter for Dart - use_null_aware_elements](https://dart.dev/tools/linter-rules/use_null_aware_elements)