Pattern: `match` with single non-trivial arm

Issue: -

## Description

Just readability – `if let` nests less than a `match`.

## What it does

Checks for matches with a single arm where an `if let`
will usually suffice.

This intentionally does not lint if there are comments
inside of the other arm, so as to allow the user to document
why having another explicit pattern with an empty body is necessary,
or because the comments need to be preserved for other reasons.

## Examples

Example of **incorrect** code:

```rust
match x {
    Some(ref foo) => bar(foo),
    _ => (),
}
```

Example of **correct** code:

```rust
if let Some(ref foo) = x {
    bar(foo);
}
```

## Further Reading

* [Clippy - single_match](https://clippy.rust-lang.org/stable/index.html#single_match)
