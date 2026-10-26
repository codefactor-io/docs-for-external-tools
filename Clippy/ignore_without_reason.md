Pattern: Ignored test without reason

Issue: -

## Description

The reason for ignoring the test may not be obvious.

## What it does

Checks for ignored tests without messages.

## Examples

Example of **incorrect** code:

```rust
#[test]
#[ignore]
fn test() {}
```

Example of **correct** code:

```rust
#[test]
#[ignore = "Some good reason"]
fn test() {}
```

## Note

Clippy can only lint compiled code. For this lint to trigger, you must configure `cargo clippy`
to include test compilation, for instance, by using flags such as `--tests` or `--all-targets`.

## Further Reading

* [Clippy - ignore_without_reason](https://clippy.rust-lang.org/stable/index.html#ignore_without_reason)
