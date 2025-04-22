Pattern: Unnecessary `async`

Issue: -

## Description

Functions that don't do `await` don't have to be `async`.

Usually such functions also don't have to return a `Future`, which allows an invoker to avoid `await` in its code, etc. Synchronous code in general runs faster, and is easier to reason about.

Example of **incorrect** code:

```dart
void f() async {
  // await Future.delayed(const Duration(seconds: 2));
  print(0);
}
```

Example of **correct** code:

```dart
void f() {
  // await Future.delayed(const Duration(seconds: 2));
  print(0);
}
```

## Further Reading

* [Linter for Dart - unnecessary_async](https://dart.dev/tools/linter-rules/unnecessary_async)