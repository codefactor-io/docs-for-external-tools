Pattern: Explicit `const` in generative enum constructor

Issue: -

## Description

Don't use an explicit `const` in a generative enum constructor. Generative enum constructors are implicitly `const`.

Example of **incorrect** code:
```dart
enum const E(final int i) {
  a(1), b(2);
}
```

```dart
enum E {
  a(1), b(2);

  const E(this.i);

  final int i;
}
```

Example of **correct** code:
```dart
enum E(final int i) {
  a(1), b(2);
}
```

```dart
enum E {
  a(1), b(2);

  E(this.i);

  final int i;
}
```

## Further Reading

* [Linter for Dart - unnecessary_const_in_enum_constructor](https://dart.dev/tools/linter-rules/unnecessary_const_in_enum_constructor)
