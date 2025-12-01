Pattern: Specified obvious type

Issue: -

## Description

Omit obvious type annotations for local variables.

Local variables, especially in modern code where functions tend to be small, have very little scope. Omitting the type focuses the reader's attention on the more important name of the variable and its initialized value. Hence, local variable type annotations that are obvious should be omitted. 

Example of **incorrect** code:

```dart
List<List<Ingredient>> possibleDesserts(Set<Ingredient> pantry) {
  List<List<Ingredient>> desserts = <List<Ingredient>>[];
  for (final List<Ingredient> recipe in cookbook) {
    if (pantry.containsAll(recipe)) {
      desserts.add(recipe);
    }
  }

  return desserts;
}

const cookbook = <List<Ingredient>>[....];
```

Example of **correct** code:

```dart
List<List<Ingredient>> possibleDesserts(Set<Ingredient> pantry) {
  var desserts = <List<Ingredient>>[];
  for (final List<Ingredient> recipe in cookbook) {
    if (pantry.containsAll(recipe)) {
      desserts.add(recipe);
    }
  }

  return desserts;
}

const cookbook = <List<Ingredient>>[....];
```

## Further Reading

* [Linter for Dart - omit_obvious_local_variable_types](https://dart.dev/tools/linter-rules/omit_obvious_local_variable_types)