Pattern: Use of `print!` with trailing newline

Issue: -

## Description

You should use `println!()` instead, which appends the
newline.

## What it does

This lint warns when you use `print!()` with a format
string that ends in a newline.

## Examples

```rust
print!("Hello {}!\n", name);
```
use println!() instead
```rust
println!("Hello {}!", name);
```

## Further Reading

* [Clippy - print_with_newline](https://clippy.rust-lang.org/stable/index.html#print_with_newline)
