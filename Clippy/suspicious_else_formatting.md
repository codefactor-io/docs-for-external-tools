Pattern: Suspicious `else` formatting

Issue: -

## Description

This is probably some refactoring remnant, even if the
code is correct, it might look confusing.

## What it does

Checks for formatting of `else`. It lints if the `else`
is followed immediately by a newline or the `else` seems to be missing.

## Examples

Example of **incorrect** code:

```rust
if foo {
} { // looks like an `else` is missing here
}

if foo {
} if bar { // looks like an `else` is missing here
}

if foo {
} else

{ // this is the `else` block of the previous `if`, but should it be?
}

if foo {
} else

if bar { // this is the `else` block of the previous `if`, but should it be?
}
```

## Further Reading

* [Clippy - suspicious_else_formatting](https://clippy.rust-lang.org/stable/index.html#suspicious_else_formatting)
