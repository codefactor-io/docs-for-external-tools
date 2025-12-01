Pattern: Unspecified non-obvious type

Issue: -

## Description

Do type annotate initialized local variables when the type is non-obvious.

Type annotations on local variables can serve as a request for type inference, documenting the expected outcome of the type inference step, and declaratively allowing the compiler and analyzer to solve the possibly complex task of finding type arguments and annotations in the initializing expression that yield the desired result.

Type annotations on local variables can also inform readers about the type of the initializing expression, which will allow them to proceed reading the subsequent lines of code with known good information about the type of the given variable (which may not be immediately evident by looking at the initializing expression).

An expression is considered to have a non-obvious type when it does not have an obvious type.

An expression e has an obvious type in the following cases:

    e is a non-collection literal. For instance, 1, `true`, `'Hello, $name!'`.
    e is a collection literal with actual type arguments. For instance, `<int, bool>{}`.
    e is a list literal or a set literal where at least one element has an obvious type, and all elements have the same type. For instance, `[1, 2]` and `{ [true, false], [] }`, but not `[1, 1.5]`.
    e is a map literal where all key-value pair have a key with an obvious type and a value with an obvious type, and all keys have the same type, and all values have the same type. For instance, `{ #a: [] }`, but not `{1: 1, 2: true}`.
    e is an instance creation expression whose class part is not raw. For instance `C(14)` if C is a non-generic class, or `C(14)` if C accepts one type argument, but not `C(14)` if C accepts one or more type arguments.
    e is a cascade whose target has an obvious type. For instance, `1..isEven..isEven` has an obvious type because 1 has an obvious type.
    e is a type cast. For instance, `myComplexExpression as int`.


Example of **incorrect** code:

```dart
List<List<Ingredient>> possibleDesserts(Set<Ingredient> pantry) {
  var desserts = genericFunctionDeclaredFarAway(<num>[42], 'Something');
  for (final recipe in cookbook) {
    if (pantry.containsAll(recipe)) {
      desserts.add(recipe);
    }
  }

  return desserts;
}

const List<List<Ingredient>> cookbook = ...;
```

Example of **correct** code:

```dart
List<List<Ingredient>> possibleDesserts(Set<Ingredient> pantry) {
  List<List<Ingredient>> desserts = genericFunctionDeclaredFarAway(
    <num>[42],
    'Something',
  );
  for (final List<Ingredient> recipe in cookbook) {
    if (pantry.containsAll(recipe)) {
      desserts.add(recipe);
    }
  }

  return desserts;
}

const List<List<Ingredient>> cookbook = ...;
```

## Further Reading

* [Linter for Dart - specify_nonobvious_local_variable_types](https://dart.dev/tools/linter-rules/specify_nonobvious_local_variable_types)