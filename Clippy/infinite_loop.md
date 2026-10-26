Pattern: Infinite loop in function not returning `!`

Issue: -

## Description

Making the return type `!` serves as documentation that the function does not return.
If the function is not intended to loop infinitely, then this lint may detect a bug.

## What it does

Checks for infinite loops in a function where the return type is not `!`
and lint accordingly.

## Examples

```rust
fn run_forever() {
    loop {
        // do something
    }
}
```
If infinite loops are as intended:
```rust
fn run_forever() -> ! {
    loop {
        // do something
    }
}
```
Otherwise add a `break` or `return` condition:
```rust
fn run_forever() {
    loop {
        // do something
        if condition {
            break;
        }
    }
}
```

## Further Reading

* [Clippy - infinite_loop](https://clippy.rust-lang.org/stable/index.html#infinite_loop)
