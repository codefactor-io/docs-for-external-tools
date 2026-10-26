Pattern: Unnecessary `inspect()` before `for_each()`

Issue: -

## Description

It is the same as performing the computation
inside `inspect` at the beginning of the closure in `for_each`.

## What it does

Checks for usage of `inspect().for_each()`.

## Examples

Example of **incorrect** code:

```rust
[1,2,3,4,5].iter()
.inspect(|&x| println!("inspect the number: {}", x))
.for_each(|&x| {
    assert!(x >= 0);
});
```

Example of **correct** code:

```rust
[1,2,3,4,5].iter()
.for_each(|&x| {
    println!("inspect the number: {}", x);
    assert!(x >= 0);
});
```

## Further Reading

* [Clippy - inspect_for_each](https://clippy.rust-lang.org/stable/index.html#inspect_for_each)
