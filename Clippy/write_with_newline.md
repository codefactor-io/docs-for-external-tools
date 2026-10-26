Pattern: Use of `write!` with trailing newline

Issue: -

## Description

You should use `writeln!()` instead, which appends the
newline.

## What it does

This lint warns when you use `write!()` with a format
string that
ends in a newline.

## Examples

Example of **incorrect** code:

```rust
write!(buf, "Hello {}!\n", name);
```

Example of **correct** code:

```rust
writeln!(buf, "Hello {}!", name);
```

## Further Reading

* [Clippy - write_with_newline](https://clippy.rust-lang.org/stable/index.html#write_with_newline)
