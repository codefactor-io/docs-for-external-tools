Pattern: Enum variants with shared prefix or suffix

Issue: -

## Description

Enumeration variant names should specify their variant,
not repeat the enumeration name.

## What it does

Detects enumeration variants that are prefixed or suffixed
by the same characters.

## Examples

Example of **incorrect** code:

```rust
enum Cake {
    BlackForestCake,
    HummingbirdCake,
    BattenbergCake,
}
```

Example of **correct** code:

```rust
enum Cake {
    BlackForest,
    Hummingbird,
    Battenberg,
}
```

## Limitations

Characters with no casing will be considered when comparing prefixes/suffixes
This applies to numbers and non-ascii characters without casing
e.g. `Foo1` and `Foo2` is considered to have different prefixes
(the prefixes are `Foo1` and `Foo2` respectively), as also `Bar螃`, `Bar蟹`

## Further Reading

* [Clippy - enum_variant_names](https://clippy.rust-lang.org/stable/index.html#enum_variant_names)
