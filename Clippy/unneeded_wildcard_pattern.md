Pattern: Unnecessary wildcard next to rest pattern

Issue: -

## Description

The wildcard pattern is unneeded as the rest pattern
can match that element as well.

## What it does

Checks for tuple and struct patterns with a wildcard
pattern (`_`) is next to a rest pattern (`..`).

_NOTE_: While `_, ..` means there is at least one element left, `..`
means there are 0 or more elements left. This can make a difference
when refactoring, but shouldn't result in errors in the refactored code,
since the wildcard pattern isn't used anyway.

## Examples

Example of **incorrect** code:

```rust
match t {
    TupleStruct(0, .., _) => (),
    _ => (),
}
```

Example of **correct** code:

```rust
match t {
    TupleStruct(0, ..) => (),
    _ => (),
}
```

## Further Reading

* [Clippy - unneeded_wildcard_pattern](https://clippy.rust-lang.org/stable/index.html#unneeded_wildcard_pattern)
