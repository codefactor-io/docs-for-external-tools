Pattern: Missing type annotation for top-level/static variable

Issue: -

## Description

Type annotations on top-level or static variables can serve as a request for type inference, documenting the expected outcome of the type inference step, and declaratively allowing the compiler and analyzer to solve the possibly complex task of finding type arguments and annotations in the initializing expression that yield the desired result.

Type annotations on top-level or static variables can also inform readers about the type of the initializing expression, which will allow them to proceed reading the locations in code where this variable is used with known good information about the type of the given variable (which may not be immediately evident by looking at the initializing expression).

An expression is considered to have a non-obvious type when it does not have an obvious type.

Example of **incorrect** code:

```dart
final myTopLevelVariable =
    genericFunctionWrittenByOtherFolks(with, args);

class A {
  static var myStaticVariable =
      myTopLevelVariable.update('foo', null);
}
```

Example of **correct** code:

```dart
final Map<String, Widget?> myTopLevelVariable =
    genericFunctionWrittenByOtherFolks(with, args);

class A {
  static Map<String, Widget?> myStaticVariable =
      myTopLevelVariable.update('foo', null);
}
```

## Further Reading

* [Linter for Dart - specify_nonobvious_property_types](https://dart.dev/tools/linter-rules/specify_nonobvious_property_types)