Pattern: Unnecessary empty string in `println!`

Issue: -

## Description

You should use `println!()`, which is simpler.

## What it does

This lint warns when you use `println!("")` to
print a newline.

## Examples

Example of **incorrect** code:

```rust
println!("");
```

Example of **correct** code:

```rust
println!();
```

## Further Reading

* [Clippy - println_empty_string](https://clippy.rust-lang.org/stable/index.html#println_empty_string)
