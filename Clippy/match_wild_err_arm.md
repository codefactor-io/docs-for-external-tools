Pattern: `Err(_)` match arm that panics

Issue: -

## Description

It is generally a bad practice, similar to
catching all exceptions in java with `catch(Exception)`

## What it does

Checks for arm which matches all errors with `Err(_)`
and take drastic actions like `panic!`.

## Examples

Example of **incorrect** code:

```rust
let x: Result<i32, &str> = Ok(3);
match x {
    Ok(_) => println!("ok"),
    Err(_) => panic!("err"),
}
```

## Further Reading

* [Clippy - match_wild_err_arm](https://clippy.rust-lang.org/stable/index.html#match_wild_err_arm)
