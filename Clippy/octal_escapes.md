Pattern: Octal-looking escape sequence

Issue: -

## Description

C and other languages support octal character escapes in strings, where
a backslash is followed by up to three octal digits. For example, `\033`
stands for the ASCII character 27 (ESC). Rust does not support this
notation, but has the escape code `\0` which stands for a null
byte/character, and any following digits do not form part of the escape
sequence. Therefore, `\033` is not a compiler error but the result may
be surprising.

## What it does

Checks for `\0` escapes in string and byte literals that look like octal
character escapes in C.

## Examples

Example of **incorrect** code:

```rust
let one = "\033[1m Bold? \033[0m";  // \033 intended as escape
let two = "\033\0";                 // \033 intended as null-3-3
```

Example of **correct** code:

```rust
let one = "\x1b[1mWill this be bold?\x1b[0m";
let two = "\x0033\x00";
```

## Known problems

The actual meaning can be the intended one. `\x00` can be used in these
cases to be unambiguous.

The lint does not trigger for format strings in `print!()`, `write!()`
and friends since the string is already preprocessed when Clippy lints
can see it.

## Further Reading

* [Clippy - octal_escapes](https://clippy.rust-lang.org/stable/index.html#octal_escapes)
