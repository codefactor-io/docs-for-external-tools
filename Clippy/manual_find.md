Pattern: Missing use of `Iterator::find()`

Issue: -

## Description

It doesn't affect performance, but using `find` is shorter and easier to read.

## What it does

Checks for manual implementations of Iterator::find

## Examples

Example of **incorrect** code:

```rust
fn example(arr: Vec<i32>) -> Option<i32> {
    for el in arr {
        if el == 1 {
            return Some(el);
        }
    }
    None
}
```

Example of **correct** code:

```rust
fn example(arr: Vec<i32>) -> Option<i32> {
    arr.into_iter().find(|&el| el == 1)
}
```

## Further Reading

* [Clippy - manual_find](https://clippy.rust-lang.org/stable/index.html#manual_find)
