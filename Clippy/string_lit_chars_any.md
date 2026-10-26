Pattern: Use of `chars().any()` on string literal

Issue: -

## Description

It's significantly slower than using a pattern instead, like
`matches!(c, '\\' | '.' | '+')`.

Despite this being faster, this is not `perf` as this is pretty common, and is a rather nice
way to check if a `char` is any in a set. In any case, this `restriction` lint is available
for situations where that additional performance is absolutely necessary.

## What it does

Checks for `<string_lit>.chars().any(|i| i == c)`.

## Examples

Example of **incorrect** code:

```rust
"\\.+*?()|[]{}^$#&-~".chars().any(|x| x == c);
```

Example of **correct** code:

```rust
matches!(c, '\\' | '.' | '+' | '*' | '(' | ')' | '|' | '[' | ']' | '{' | '}' | '^' | '$' | '#' | '&' | '-' | '~');
```

## Further Reading

* [Clippy - string_lit_chars_any](https://clippy.rust-lang.org/stable/index.html#string_lit_chars_any)
