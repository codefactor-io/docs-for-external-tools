Pattern: `Iterator` implemented on `Copy` type

Issue: -

## Description

Implicit copies can be confusing when working with
iterator combinators.

## What it does

Checks for types that implement `Copy` as well as
`Iterator`.

## Examples

Example of **incorrect** code:

```rust
#[derive(Copy, Clone)]
struct Countdown(u8);

impl Iterator for Countdown {
    // ...
}

let a: Vec<_> = my_iterator.take(1).collect();
let b: Vec<_> = my_iterator.collect();
```

## Further Reading

* [Clippy - copy_iterator](https://clippy.rust-lang.org/stable/index.html#copy_iterator)
