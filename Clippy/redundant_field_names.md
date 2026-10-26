Pattern: Redundant field name in struct literal

Issue: -

## Description

If the field and variable names are the same,
the field name is redundant.

## What it does

Checks for fields in struct literals where shorthands
could be used.

## Examples

```rust
let bar: u8 = 123;

struct Foo {
    bar: u8,
}

let foo = Foo { bar: bar };
```
the last line can be simplified to
```rust
let foo = Foo { bar };
```

## Further Reading

* [Clippy - redundant_field_names](https://clippy.rust-lang.org/stable/index.html#redundant_field_names)
