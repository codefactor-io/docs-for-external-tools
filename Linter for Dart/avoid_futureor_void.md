Pattern: Use of `FutureOr<void>`

Issue: -

## Description

This type is problematic because it may appear to encode that a result is either a `Future<void>`, or the result should be discarded (when it is void). However, there is no safe way to detect whether we have one or the other case (because an expression of type void can evaluate to any object whatsoever, including a future of any type).

It is also conceptually unsound to have a type whose meaning is something like "ignore this object; also, take a look because it might be a future".


Example of **incorrect** code:

```dart
FutureOr<void> m() {...}
```

Example of **incorrect** code:

```dart
Future<void>? m() {...}
```

## Further Reading

* [Linter for Dart - avoid_futureor_void](https://dart.dev/tools/linter-rules/avoid_futureor_void)