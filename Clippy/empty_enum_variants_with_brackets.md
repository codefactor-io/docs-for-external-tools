Pattern: Enum variant with empty brackets

Issue: -

## Description

Empty brackets after a enum variant declaration are redundant and can be omitted,
and it may be desirable to do so consistently for style.

However, removing the brackets also introduces a public constant named after the variant,
so this is not just a syntactic simplification but an API change, and adding them back
is a *breaking* API change.

## What it does

Finds enum variants without fields that are declared with empty brackets.

## Examples

Example of **incorrect** code:

```rust
enum MyEnum {
    HasData(u8),
    HasNoData(),       // redundant parentheses
    NoneHereEither {}, // redundant braces
}
```

Example of **correct** code:

```rust
enum MyEnum {
    HasData(u8),
    HasNoData,
    NoneHereEither,
}
```

## Further Reading

* [Clippy - empty_enum_variants_with_brackets](https://clippy.rust-lang.org/stable/index.html#empty_enum_variants_with_brackets)
