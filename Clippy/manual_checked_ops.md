Pattern: Missing use of `checked_div()`

Issue: -

## Description

`checked_div` already handles the zero case and makes the intent clearer while avoiding a
panic from a manual division.

## What it does

Detects manual zero checks before dividing integers, such as `if x != 0 { y / x }`.

## Examples

Example of **incorrect** code:

```rust
if b != 0 {
    let result = a / b;
    println!("{result}");
}
```

Example of **correct** code:

```rust
if let Some(result) = a.checked_div(b) {
    println!("{result}");
}
```

## Further Reading

* [Clippy - manual_checked_ops](https://clippy.rust-lang.org/stable/index.html#manual_checked_ops)
