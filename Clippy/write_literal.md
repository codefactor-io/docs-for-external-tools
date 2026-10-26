Pattern: Literal argument in `write!`

Issue: -

## Description

Using literals as `writeln!` args is inefficient
(c.f., https://github.com/matthiaskrgr/rust-str-bench) and unnecessary
(i.e., just put the literal in the format string)

## What it does

This lint warns about the use of literals as `write!`/`writeln!` args.

## Examples

Example of **incorrect** code:

```rust
writeln!(buf, "{}", "foo");
```

Example of **correct** code:

```rust
writeln!(buf, "foo");
```

## Further Reading

* [Clippy - write_literal](https://clippy.rust-lang.org/stable/index.html#write_literal)
