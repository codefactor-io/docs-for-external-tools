Pattern: Use of `and_then()` in return expression

Issue: -

## Description

The `and_then` method is used to chain a computation that returns an `Option` or a `Result`.
This can be replaced with the `?` operator, which is more concise and idiomatic.

## What it does

Detect functions that end with `Option::and_then` or `Result::and_then`, and suggest using
the `?` operator instead.

## Examples

Example of **incorrect** code:

```rust
fn test(opt: Option<i32>) -> Option<i32> {
    opt.and_then(|n| {
        if n > 1 {
            Some(n + 1)
        } else {
            None
       }
    })
}
```

Example of **correct** code:

```rust
fn test(opt: Option<i32>) -> Option<i32> {
    let n = opt?;
    if n > 1 {
        Some(n + 1)
    } else {
        None
    }
}
```

## Further Reading

* [Clippy - return_and_then](https://clippy.rust-lang.org/stable/index.html#return_and_then)
