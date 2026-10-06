Pattern: Unresolved `FIXME` comment

Issue: -

## Description

The Dart analyzer reports this diagnostic for comments containing a `FIXME` marker. It is a TODO diagnostic that identifies work still needing a fix, rather than a configurable linter rule.

Address the task described by the comment, then remove the marker once the work is complete.

Example of **incorrect** code:
```dart
main() {
  // FIXME: Implement
}
```

Example of **correct** code:
```dart
main() {
  print('Hello, world!');
}
```

## Further Reading

* [Dart analyzer - Diagnostic definitions](https://github.com/dart-lang/sdk/blob/main/pkg/analyzer/messages.yaml)
* [Dart analyzer - TODO diagnostics tests](https://github.com/dart-lang/sdk/blob/main/pkg/analyzer/test/src/diagnostics/todo_test.dart)
