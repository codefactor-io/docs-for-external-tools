Pattern: Redundant borrow in format argument

Issue: -

## Description

The extra `&` is redundant and can make the code less clear. Format macros take
references to the arguments internally, so passing `&x` when `x` is already a
reference produces a double reference. The compiler is currently unable to
optimize double references, which results in about 6% degradation per call.

## What it does

Detects format!-style macros (e.g. `format!`, `println!`, `write!`) where an argument
is passed with an explicit `&` but the value is already a reference, resulting in a
double reference (e.g. `&&T`).

## Examples

Example of **incorrect** code:

```rust
let s: &str = "hello";
println!("{}", &s);
```

Example of **correct** code:

```rust
let s: &str = "hello";
println!("{}", s);
```

## Further Reading

* [Clippy - useless_borrows_in_formatting](https://clippy.rust-lang.org/stable/index.html#useless_borrows_in_formatting)
