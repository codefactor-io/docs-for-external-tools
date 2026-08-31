Pattern: Explicit type name in constructor declaration

Issue: -

## Description

Don't include the type name in a constructor declaration. It isn't necessary, and the code is shorter and cleaner without it.

Example of **incorrect** code:
```dart
class C {
  C();
  C.name();
}
```

Example of **correct** code:
```dart
class C {
  new ();
  new name();
}
```

## Further Reading

* [Linter for Dart - unnecessary_type_name_in_constructor](https://dart.dev/tools/linter-rules/unnecessary_type_name_in_constructor)
