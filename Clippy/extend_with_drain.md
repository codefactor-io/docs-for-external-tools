Pattern: Missing use of `Vec::append()`

Issue: -

## Description

Using `append` instead of `extend` is more concise and faster

## What it does

Checks for occurrences where one vector gets extended instead of append

## Examples

Example of **incorrect** code:

```rust
let mut a = vec![1, 2, 3];
let mut b = vec![4, 5, 6];

a.extend(b.drain(..));
```

Example of **correct** code:

```rust
let mut a = vec![1, 2, 3];
let mut b = vec![4, 5, 6];

a.append(&mut b);
```

## Further Reading

* [Clippy - extend_with_drain](https://clippy.rust-lang.org/stable/index.html#extend_with_drain)
