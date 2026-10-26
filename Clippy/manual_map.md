Pattern: Missing use of `Option::map()`

Issue: -

## Description

Using the `map` method is clearer and more concise.

## What it does

Checks for usage of `match` which could be implemented using `map`

## Examples

Example of **incorrect** code:

```rust
match Some(0) {
    Some(x) => Some(x + 1),
    None => None,
};
```

Example of **correct** code:

```rust
Some(0).map(|x| x + 1);
```

## Further Reading

* [Clippy - manual_map](https://clippy.rust-lang.org/stable/index.html#manual_map)
