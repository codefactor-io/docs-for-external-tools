Pattern: Missing use of `while let`

Issue: -

## Description

The `while let` loop is usually shorter and more
readable.

## What it does

Detects `loop + match` combinations that are easier
written as a `while let` loop.

## Examples

Example of **incorrect** code:

```rust
let y = Some(1);
loop {
    let x = match y {
        Some(x) => x,
        None => break,
    };
    // ..
}
```

Example of **correct** code:

```rust
let y = Some(1);
while let Some(x) = y {
    // ..
};
```

## Further Reading

* [Clippy - while_let_loop](https://clippy.rust-lang.org/stable/index.html#while_let_loop)
