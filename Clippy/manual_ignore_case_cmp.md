Pattern: Missing use of `eq_ignore_ascii_case()`

Issue: -

## Description

The `eq_ignore_ascii_case` method is faster because it does not allocate
memory for the new strings, and it is more readable.

## What it does

Checks for manual case-insensitive ASCII comparison.

## Examples

Example of **incorrect** code:

```rust
fn compare(a: &str, b: &str) -> bool {
    a.to_ascii_lowercase() == b.to_ascii_lowercase() || a.to_ascii_lowercase() == "abc"
}
```

Example of **correct** code:

```rust
fn compare(a: &str, b: &str) -> bool {
    a.eq_ignore_ascii_case(b) || a.eq_ignore_ascii_case("abc")
}
```

## Further Reading

* [Clippy - manual_ignore_case_cmp](https://clippy.rust-lang.org/stable/index.html#manual_ignore_case_cmp)
