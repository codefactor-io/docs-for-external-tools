Pattern: Missing use of `Iterator::flatten()`

Issue: -

## Description

It is verbose and can be simplified
by first calling the `flatten` method on the `Iterator`.

## What it does

Checks for unnecessary `if let` usage in a for loop
where only the `Some` or `Ok` variant of the iterator element is used.

## Examples

Example of **incorrect** code:

```rust
let x = vec![Some(1), Some(2), Some(3)];
for n in x {
    if let Some(n) = n {
        println!("{}", n);
    }
}
```

Example of **correct** code:

```rust
let x = vec![Some(1), Some(2), Some(3)];
for n in x.into_iter().flatten() {
    println!("{}", n);
}
```

## Further Reading

* [Clippy - manual_flatten](https://clippy.rust-lang.org/stable/index.html#manual_flatten)
