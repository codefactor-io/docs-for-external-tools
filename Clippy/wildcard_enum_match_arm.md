Pattern: Wildcard arm in enum `match`

Issue: -

## Description

New enum variants added by library updates can be missed.

## What it does

Checks for wildcard enum matches using `_`.

## Examples

Example of **incorrect** code:

```rust
match x {
    Foo::A(_) => {},
    _ => {},
}
```

Example of **correct** code:

```rust
match x {
    Foo::A(_) => {},
    Foo::B(_) => {},
}
```

## Known problems

Suggested replacements may be incorrect if guards exhaustively cover some
variants, and also may not use correct path to enum if it's not present in the current scope.

## Further Reading

* [Clippy - wildcard_enum_match_arm](https://clippy.rust-lang.org/stable/index.html#wildcard_enum_match_arm)
