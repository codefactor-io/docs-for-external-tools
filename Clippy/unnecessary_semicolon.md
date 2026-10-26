Pattern: Unnecessary semicolon after `if` or `match`

Issue: -

## Description

The semicolon is not needed, and may be removed to
avoid confusion and visual clutter.

## What it does

Checks for the presence of a semicolon at the end of
a `match` or `if` statement evaluating to `()`.

## Examples

Example of **incorrect** code:

```rust
if a > 10 {
    println!("a is greater than 10");
};
```

Example of **correct** code:

```rust
if a > 10 {
    println!("a is greater than 10");
}
```

## Further Reading

* [Clippy - unnecessary_semicolon](https://clippy.rust-lang.org/stable/index.html#unnecessary_semicolon)
