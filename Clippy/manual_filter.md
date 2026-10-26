Pattern: Missing use of `Option::filter()`

Issue: -

## Description

Using the `filter` method is clearer and more concise.

## What it does

Checks for usage of `match` which could be implemented using `filter`

## Examples

Example of **incorrect** code:

```rust
match Some(0) {
    Some(x) => if x % 2 == 0 {
                    Some(x)
               } else {
                    None
                },
    None => None,
};
```

Example of **correct** code:

```rust
Some(0).filter(|&x| x % 2 == 0);
```

## Further Reading

* [Clippy - manual_filter](https://clippy.rust-lang.org/stable/index.html#manual_filter)
