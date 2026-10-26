Pattern: Unnecessary `match`

Issue: -

## Description

This `match` block does nothing and might not be what the coder intended.

## What it does

Checks for unnecessary `match` or match-like `if let` returns for `Option` and `Result`
when function signatures are the same.

## Examples

```rust
fn foo() -> Result<(), i32> {
    match result {
        Ok(val) => Ok(val),
        Err(err) => Err(err),
    }
}

fn bar() -> Option<i32> {
    if let Some(val) = option {
        Some(val)
    } else {
        None
    }
}
```

Could be replaced as

```rust
fn foo() -> Result<(), i32> {
    result
}

fn bar() -> Option<i32> {
    option
}
```

## Further Reading

* [Clippy - needless_match](https://clippy.rust-lang.org/stable/index.html#needless_match)
