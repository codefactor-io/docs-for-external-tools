Pattern: Empty string in `writeln!`

Issue: -

## Description

You should use `writeln!(buf)`, which is simpler.

## What it does

This lint warns when you use `writeln!(buf, "")` to
print a newline.

## Examples

Example of **incorrect** code:

```rust
writeln!(buf, "");
```

Example of **correct** code:

```rust
writeln!(buf);
```

## Further Reading

* [Clippy - writeln_empty_string](https://clippy.rust-lang.org/stable/index.html#writeln_empty_string)
