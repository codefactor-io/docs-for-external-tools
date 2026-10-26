Pattern: Use of `unwrap()` in `Result` function

Issue: -

## Description

These functions promote recoverable errors to non-recoverable errors,
which may be undesirable in code bases which wish to avoid panics,
or be a bug in the specific function.

## What it does

Checks for functions of type `Result` that contain `expect()` or `unwrap()`

## Examples

Before:
```rust
fn divisible_by_3(i_str: String) -> Result<(), String> {
    let i = i_str
        .parse::<i32>()
        .expect("cannot divide the input by three");

    if i % 3 != 0 {
        Err("Number is not divisible by 3")?
    }

    Ok(())
}
```

After:
```rust
fn divisible_by_3(i_str: String) -> Result<(), String> {
    let i = i_str
        .parse::<i32>()
        .map_err(|e| format!("cannot divide the input by three: {}", e))?;

    if i % 3 != 0 {
        Err("Number is not divisible by 3")?
    }

    Ok(())
}
```

## Known problems

This can cause false positives in functions that handle both recoverable and non recoverable errors.

## Further Reading

* [Clippy - unwrap_in_result](https://clippy.rust-lang.org/stable/index.html#unwrap_in_result)
