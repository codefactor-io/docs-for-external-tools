Pattern: `panic!` or assertion in `Result` function

Issue: -

## Description

For some codebases, it is desirable for functions of type result to return an error instead of crashing. Hence panicking macros should be avoided.

## What it does

Checks for usage of `panic!` or assertions in a function whose return type is `Result`.

## Examples

Example of **incorrect** code:

```rust
fn result_with_panic() -> Result<bool, String>
{
    panic!("error");
}
```

Example of **correct** code:

```rust
fn result_without_panic() -> Result<bool, String> {
    Err(String::from("error"))
}
```

## Known problems

Functions called from a function returning a `Result` may invoke a panicking macro. This is not checked.

## Further Reading

* [Clippy - panic_in_result_fn](https://clippy.rust-lang.org/stable/index.html#panic_in_result_fn)
