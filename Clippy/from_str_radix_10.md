Pattern: Use of `from_str_radix()` with radix 10

Issue: -

## Description

This specific common use case can be rewritten as `s.parse::<primitive>()`
(and in most cases, the turbofish can be removed), which reduces code length
and complexity.

## What it does

Checks for function invocations of the form `primitive::from_str_radix(s, 10)`

## Examples

Example of **incorrect** code:

```rust
let input: &str = get_input();
let num = u16::from_str_radix(input, 10)?;
```

Example of **correct** code:

```rust
let input: &str = get_input();
let num: u16 = input.parse()?;
```

## Known problems

This lint may suggest using `(&<expression>).parse()` instead of `<expression>.parse()`
directly in some cases, which is correct but adds unnecessary complexity to the code.

## Further Reading

* [Clippy - from_str_radix_10](https://clippy.rust-lang.org/stable/index.html#from_str_radix_10)
