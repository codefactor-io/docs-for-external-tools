Pattern: Unnecessary `unwrap()` after check

Issue: -

## Description

Using `if let` or `match` is more idiomatic.

## What it does

Checks for calls of `unwrap[_err]()` that cannot fail.

## Examples

Example of **incorrect** code:

```rust
if option.is_some() {
    do_something_with(option.unwrap())
}
```

Example of **correct** code:

```rust
if let Some(value) = option {
    do_something_with(value)
}
```

## Further Reading

* [Clippy - unnecessary_unwrap](https://clippy.rust-lang.org/stable/index.html#unnecessary_unwrap)
