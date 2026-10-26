Pattern: Possible missing `else`

Issue: -

## Description

This is probably some refactoring remnant, even if the code is correct, it
might look confusing.

## What it does

Checks for an `if` expression followed by either a block or another `if` that
looks like it should have an `else` between them.

## Examples

Example of **incorrect** code:

```rust
if foo {
} { // looks like an `else` is missing here
}

if foo {
} if bar { // looks like an `else` is missing here
}
```

## Further Reading

* [Clippy - possible_missing_else](https://clippy.rust-lang.org/stable/index.html#possible_missing_else)
