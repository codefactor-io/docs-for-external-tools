Pattern: Invalid runtime check with JS interop type

Issue: -

## Description

DON'T use `is` checks where the type is a JS interop type.

DON'T use `is` checks where the type is a generic Dart type that has JS interop type arguments.

DON'T use `is` checks with a JS interop value.

`dart:js_interop` types have runtime types that are different based on whether you are compiling to JS or to Wasm. Therefore, runtime type checks may result in different behavior. Runtime checks also do not necessarily check that a JS interop value is a particular JavaScript type.

Example of **incorrect** code:

```dart
extension type HTMLElement(JSObject o) {}
extension type HTMLDivElement(JSObject o) implements HTMLElement {}

void compute(JSAny a, bool b, List<JSObject> lo, List<String> ls, JSObject o,
    HTMLElement e) {
  a is String; // LINT, checking that a JS value is a Dart type
  b is JSBoolean; // LINT, checking that a Dart value is a JS type
  a is JSString; // LINT, checking that a JS value is a different JS interop
                 // type
  o is JSNumber; // LINT, checking that a JS value is a different JS interop
                 // type
  lo is List<String>; // LINT, JS interop type argument and Dart type argument
                      // are incompatible
  ls is List<JSString>; // LINT, Dart type argument and JS interop type argument
                        // are incompatible
  lo is List<JSArray>; // LINT, comparing JS interop type argument with
                       // different JS interop type argument
  lo is List<JSNumber>; // LINT, comparing JS interop type argument with
                        // different JS interop type argument
  o is HTMLElement; // LINT, true because both are JSObjects but doesn't check
                    // that it's a JS HTMLElement
  e is HTMLDivElement; // LINT, true because both are JSObjects but doesn't
                       // check that it's a JS HTMLDivElement
}
```

Example of **incorrect** code:

```dart
extension type HTMLElement(JSObject o) implements JSObject {}
extension type HTMLDivElement(JSObject o) implements HTMLElement {}

void compute(JSAny a, List<JSAny> l, JSObject o, HTMLElement e) {
  a.isA<JSString>; // OK, uses JS interop to check it is a JS string
  l[0].isA<JSString>; // OK, uses JS interop to check it is a JS string
  o.isA<HTMLElement>(); // OK, uses JS interop to check `o` is an HTMLElement
  e.isA<HTMLDivElement>(); // OK, uses JS interop to check `e` is an
                           // HTMLDivElement
}
```

## Further Reading

* [Linter for Dart - invalid_runtime_check_with_js_interop_types](https://dart.dev/tools/linter-rules/invalid_runtime_check_with_js_interop_types#details)