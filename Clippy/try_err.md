Pattern: Use of `Err(x)?`

Issue: -

## Description

The `?` operator is designed to allow calls that
can fail to be easily chained. For example, `foo()?.bar()` or
`foo(bar()?)`. Because `Err(x)?` can't be used that way (it will
always return), it is more clear to write `return Err(x)`.

## What it does

Checks for usage of `Err(x)?`.

## Examples

Example of **incorrect** code:

```rust
fn foo(fail: bool) -> Result<i32, String> {
    if fail {
      Err("failed")?;
    }
    Ok(0)
}
```

Example of **correct** code:

```rust
fn foo(fail: bool) -> Result<i32, String> {
    if fail {
      return Err("failed".into());
    }
    Ok(0)
}
```

## Further Reading

* [Clippy - try_err](https://clippy.rust-lang.org/stable/index.html#try_err)
