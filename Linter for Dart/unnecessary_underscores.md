Pattern: Unnecessary underscore

Issue: -

## Description

Avoid using multiple underscores when a single underscore will do.

Example of **incorrect** code:

```dart
void function(int __) { }
```

Example of **correct** code:

```dart
void function(int _) { }
```

## Further Reading

* [Linter for Dart - unnecessary_underscores](https://dart.dev/tools/linter-rules/unnecessary_underscores)