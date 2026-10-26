Pattern: `#[should_panic]` without expected message

Issue: -

## Description

The expected panic message should be specified to ensure that the test is actually
panicking with the expected message, and not another unrelated panic.

## What it does

Checks for `#[should_panic]` attributes without specifying the expected panic message.

## Examples

Example of **incorrect** code:

```rust
fn random() -> i32 { 0 }

#[should_panic]
#[test]
fn my_test() {
    let _ = 1 / random();
}
```

Example of **correct** code:

```rust
fn random() -> i32 { 0 }

#[should_panic = "attempt to divide by zero"]
#[test]
fn my_test() {
    let _ = 1 / random();
}
```

## Further Reading

* [Clippy - should_panic_without_expect](https://clippy.rust-lang.org/stable/index.html#should_panic_without_expect)
