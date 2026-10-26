Pattern: Repetitive struct field names

Issue: -

## Description

Information common to all struct fields is better represented in the struct name.

## What it does

Detects struct fields that are prefixed or suffixed
by the same characters or the name of the struct itself.

## Examples

Example of **incorrect** code:

```rust
struct Cake {
    cake_sugar: u8,
    cake_flour: u8,
    cake_eggs: u8
}
```

Example of **correct** code:

```rust
struct Cake {
    sugar: u8,
    flour: u8,
    eggs: u8
}
```

## Limitations

Characters with no casing will be considered when comparing prefixes/suffixes
This applies to numbers and non-ascii characters without casing
e.g. `foo1` and `foo2` is considered to have different prefixes
(the prefixes are `foo1` and `foo2` respectively), as also `bar螃`, `bar蟹`

## Further Reading

* [Clippy - struct_field_names](https://clippy.rust-lang.org/stable/index.html#struct_field_names)
