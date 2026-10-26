Pattern: Use of `cloned().collect()` on slice

Issue: -

## Description

`.to_vec()` is clearer

## What it does

Checks for the use of `.cloned().collect()` on slice to
create a `Vec`.

## Examples

Example of **incorrect** code:

```rust
let s = [1, 2, 3, 4, 5];
let s2: Vec<isize> = s[..].iter().cloned().collect();
```

Example of **correct** code:

```rust
let s = [1, 2, 3, 4, 5];
let s2: Vec<isize> = s.to_vec();
```

## Further Reading

* [Clippy - iter_cloned_collect](https://clippy.rust-lang.org/stable/index.html#iter_cloned_collect)
