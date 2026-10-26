Pattern: Unnecessary `Option` or `Result` return type

Issue: -

## Description

It is not meaningful to wrap values when no `None` or `Err` is returned.

## What it does

Checks for private functions that only return `Ok` or `Some`.

## Examples

Example of **incorrect** code:

```rust
fn get_cool_number(a: bool, b: bool) -> Option<i32> {
    if a && b {
        return Some(50);
    }
    if a {
        Some(0)
    } else {
        Some(10)
    }
}
```

Example of **correct** code:

```rust
fn get_cool_number(a: bool, b: bool) -> i32 {
    if a && b {
        return 50;
    }
    if a {
        0
    } else {
        10
    }
}
```

## Known problems

There can be false positives if the function signature is designed to
fit some external requirement.

## Further Reading

* [Clippy - unnecessary_wraps](https://clippy.rust-lang.org/stable/index.html#unnecessary_wraps)
