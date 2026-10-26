Pattern: Useless conversion to same type

Issue: -

## Description

Redundant code.

## What it does

Checks for `Into`, `TryInto`, `From`, `TryFrom`, or `IntoIterator` calls
which uselessly convert to the same type.

## Examples

Example of **incorrect** code:

```rust
// format!() returns a `String`
let s: String = format!("hello").into();
```

Example of **correct** code:

```rust
let s: String = format!("hello");
```

## Further Reading

* [Clippy - useless_conversion](https://clippy.rust-lang.org/stable/index.html#useless_conversion)
