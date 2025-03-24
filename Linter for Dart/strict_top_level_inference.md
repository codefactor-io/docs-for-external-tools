Pattern: Missing type annotation

Issue: -

## Description

Do type annotate top-level and class-like member declarations, where types are not inferred from super-interfaces or initializers.

The lint warns about every omitted return type, parameter type, and variable type of a top-level declaration or class-like-namespace-level declaration (static or instance member or constructor declaration), which is not given a type by inference, and which therefore defaults to dynamic.

The only omitted types that can be given a type by top-level inference, are those of variable declarations with initializer expressions, and return and parameter types of instance members that override a consistent combined super-interface signature.

Setters do not need a return type, as it is always assumed to be `void`.

Example of **incorrect** code:

```dart
var _zeroPointCache;
class Point {
  get zero => ...;
  final x, y;
  Point(x, y) {}
  closest(b, c) => distance(b) <= distance(c) ? b : c;
  distance(other) => ...;
}
_sq(v) => v * v;
```

Example of **correct** code:

```dart
Point? _zeroPointCache;
class Point {
  Point get zero => ...;
  final int x, y;
  Point(int x, int y) {}
  closest(Point b, Point c) =>
      distance(b) <= distance(c) ? b : c;
  distance(Point other) => ...;
}
int _sq(int v) => v * v;
```

## Further Reading

* [Linter for Dart - strict_top_level_inference](https://dart.dev/tools/linter-rules/strict_top_level_inference)