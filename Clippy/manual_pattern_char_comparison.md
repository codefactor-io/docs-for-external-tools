Pattern: Closure comparing chars in string pattern

Issue: -

## Description

This can be written more concisely using a `char` or an array of `char`.
This is more readable and more optimized when comparing to only one `char`.

## What it does

Checks for manual `char` comparison in string patterns

## Examples

Example of **incorrect** code:

```rust
"Hello World!".trim_end_matches(|c| c == '.' || c == ',' || c == '!' || c == '?');
```

Example of **correct** code:

```rust
"Hello World!".trim_end_matches(['.', ',', '!', '?']);
```

## Further Reading

* [Clippy - manual_pattern_char_comparison](https://clippy.rust-lang.org/stable/index.html#manual_pattern_char_comparison)
