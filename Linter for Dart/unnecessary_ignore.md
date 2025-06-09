Pattern: Unnecessary `ignore`

Issue: -

## Description

DON'T specify an ignore for a diagnostic that is not produced.

Example of **correct** code:

```dart
// ignore: [!unused_local_variable!]
void f() {}
```

Example of **incorrect** code:

```dart
void f() {}
```

## Further Reading

* [Linter for Dart - unnecessary_ignore](https://dart.dev/tools/linter-rules/unnecessary_ignore)