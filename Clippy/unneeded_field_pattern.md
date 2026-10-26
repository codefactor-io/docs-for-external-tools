Pattern: Unnecessary wildcard field pattern

Issue: -

## Description

Using `..` instead is shorter and leaves the focus on
the fields that are actually bound.

## What it does

Checks for structure field patterns bound to wildcards.

## Examples

Example of **incorrect** code:

```rust
let f = Foo { a: 0, b: 0, c: 0 };

match f {
    Foo { a: _, b: 0, .. } => {},
    Foo { a: _, b: _, c: _ } => {},
}
```

Example of **correct** code:

```rust
let f = Foo { a: 0, b: 0, c: 0 };

match f {
    Foo { b: 0, .. } => {},
    Foo { .. } => {},
}
```

## Further Reading

* [Clippy - unneeded_field_pattern](https://clippy.rust-lang.org/stable/index.html#unneeded_field_pattern)
