Pattern: Recursive call to `main()`

Issue: -

## Description

Apart from special setups (which we could detect following attributes like #![no_std]),
recursing into main() seems like an unintuitive anti-pattern we should be able to detect.

## What it does

Checks for recursion using the entrypoint.

## Examples

Example of **incorrect** code:

```rust
fn main() {
    main();
}
```

## Further Reading

* [Clippy - main_recursion](https://clippy.rust-lang.org/stable/index.html#main_recursion)
