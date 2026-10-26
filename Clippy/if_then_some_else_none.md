Pattern: Missing use of `bool::then()`

Issue: -

## Description

Looks a little redundant. Using `bool::then` is more concise and incurs no loss of clarity.
For simple calculations and known values, use `bool::then_some`, which is eagerly evaluated
in comparison to `bool::then`.

## What it does

Checks for if-else that could be written using either `bool::then` or `bool::then_some`.

## Examples

Example of **incorrect** code:

```rust
let a = if v.is_empty() {
    println!("true!");
    Some(42)
} else {
    None
};
```

Example of **correct** code:

```rust
let a = v.is_empty().then(|| {
    println!("true!");
    42
});
```

## Further Reading

* [Clippy - if_then_some_else_none](https://clippy.rust-lang.org/stable/index.html#if_then_some_else_none)
