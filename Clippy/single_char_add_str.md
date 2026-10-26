Pattern: `push_str()` with single-character string

Issue: -

## Description

It's less clear that we are pushing a single character.

## What it does

Warns when using `push_str`/`insert_str` with a single-character string literal
where `push`/`insert` with a `char` would work fine.

## Examples

Example of **incorrect** code:

```rust
string.insert_str(0, "R");
string.push_str("R");
```

Example of **correct** code:

```rust
string.insert(0, 'R');
string.push('R');
```

## Further Reading

* [Clippy - single_char_add_str](https://clippy.rust-lang.org/stable/index.html#single_char_add_str)
