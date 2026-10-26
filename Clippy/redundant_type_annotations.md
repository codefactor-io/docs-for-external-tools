Pattern: Redundant type annotation

Issue: -

## Description

Code without type annotations is shorter and in most cases
more idiomatic and easier to modify.

## What it does

Warns about needless / redundant type annotations.

## Examples

Example of **incorrect** code:

```rust
let foo: String = String::new();
```

Example of **correct** code:

```rust
let foo = String::new();
```

## Limitations

This lint doesn't support:

- Generics
- Refs returned from anything else than a `MethodCall`
- Complex types (tuples, arrays, etc...)
- `Path` to anything else than a primitive type.

## Further Reading

* [Clippy - redundant_type_annotations](https://clippy.rust-lang.org/stable/index.html#redundant_type_annotations)
