Pattern: Unnecessary `return` with `?`

Issue: -

## Description

The `return` is unnecessary.

Returns may be used to add attributes to the return expression. Return
statements with attributes are therefore be accepted by this lint.

## What it does

Checks for return statements on `Err` paired with the `?` operator.

## Examples

```rust
fn foo(x: usize) -> Result<(), Box<dyn Error>> {
    if x == 0 {
        return Err(...)?;
    }
    Ok(())
}
```
simplify to
```rust
fn foo(x: usize) -> Result<(), Box<dyn Error>> {
    if x == 0 {
        Err(...)?;
    }
    Ok(())
}
```
if paired with `try_err`, use instead:
```rust
fn foo(x: usize) -> Result<(), Box<dyn Error>> {
    if x == 0 {
        return Err(...);
    }
    Ok(())
}
```

## Further Reading

* [Clippy - needless_return_with_question_mark](https://clippy.rust-lang.org/stable/index.html#needless_return_with_question_mark)
