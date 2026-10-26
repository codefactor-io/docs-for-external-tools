Pattern: Wildcard match for single enum variant

Issue: -

## Description

New enum variants added by library updates can be missed.

## What it does

Checks for wildcard enum matches for a single variant.

## Examples

Example of **incorrect** code:

```rust
match x {
    Foo::A => {},
    Foo::B => {},
    _ => {},
}
```

Example of **correct** code:

```rust
match x {
    Foo::A => {},
    Foo::B => {},
    Foo::C => {},
}
```

## Known problems

Suggested replacements may not use correct path to enum
if it's not present in the current scope.

## Further Reading

* [Clippy - match_wildcard_for_single_variants](https://clippy.rust-lang.org/stable/index.html#match_wildcard_for_single_variants)
