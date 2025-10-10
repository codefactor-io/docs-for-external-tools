Pattern: Use of switch on `Type`

Issue: -

## Description

Switching on `Type` is not type-safe and can lead to bugs if the class hierarchy changes. Prefer to use pattern matching on the variable instead.
 
Example of **incorrect** code:

```dart
void f(Object o) {
  switch (o.runtimeType) {
    case int:
      print('int');
    case String:
      print('String');
  }
}
```

Example of **correct** code:

```dart
void f(Object o) {
  switch(o) {
    case int():
      print('int');
    case String _:
      print('String');
    default:
      print('other');
  }
}
```

## Further Reading

* [Linter for Dart - switch_on_type](https://dart.dev/tools/linter-rules/switch_on_type)