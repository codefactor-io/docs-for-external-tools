Pattern: Missing semicolon after unit expression

Issue: -

## Description

The semicolon might be optional but when extending the block with new
code, it doesn't require a change in previous last line.

## What it does

Looks for blocks of expressions and fires if the last expression returns
`()` but is not followed by a semicolon.

## Examples

Example of **incorrect** code:

```rust
fn main() {
    println!("Hello world")
}
```

Example of **correct** code:

```rust
fn main() {
    println!("Hello world");
}
```

## Further Reading

* [Clippy - semicolon_if_nothing_returned](https://clippy.rust-lang.org/stable/index.html#semicolon_if_nothing_returned)
