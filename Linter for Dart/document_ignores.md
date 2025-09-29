Pattern: Undocumented ignore comment

Issue: -

## Description

**DO** document all ignored diagnostic reports.

Example of **incorrect** code:

```dart
// ignore: unused_element
int _x = 1;
```

Example of **correct** code:

```dart
// This private field will be used later.
// ignore: unused_element
int _x = 1;
```

## Further Reading

* [Linter for Dart - document_ignores](https://dart.dev/tools/linter-rules/document_ignores)