Pattern: Literal argument to print macro

Issue: -

## Description

Using literals as `println!` args is inefficient
(c.f., https://github.com/matthiaskrgr/rust-str-bench) and unnecessary
(i.e., just put the literal in the format string)

## What it does

This lint warns about the use of literals as `print!`/`println!` args.

## Examples

```rust
println!("{}", "foo");
```
use the literal without formatting:
```rust
println!("foo");
```

## Further Reading

* [Clippy - print_literal](https://clippy.rust-lang.org/stable/index.html#print_literal)
