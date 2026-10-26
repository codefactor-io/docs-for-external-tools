Pattern: Missing use of `is_ascii_*()` method

Issue: -

## Description

Using the built-in functions is more readable and makes it
clear that it's not a specific subset of characters, but all
ASCII (lowercase|uppercase|digit|hexdigit) characters.

## What it does

Suggests to use dedicated built-in methods,
`is_ascii_(lowercase|uppercase|digit|hexdigit)` for checking on corresponding
ascii range

## Examples

Example of **incorrect** code:

```rust
fn main() {
    assert!(matches!('x', 'a'..='z'));
    assert!(matches!(b'X', b'A'..=b'Z'));
    assert!(matches!('2', '0'..='9'));
    assert!(matches!('x', 'A'..='Z' | 'a'..='z'));
    assert!(matches!('C', '0'..='9' | 'a'..='f' | 'A'..='F'));

    ('0'..='9').contains(&'0');
    ('a'..='z').contains(&'a');
    ('A'..='Z').contains(&'A');
}
```

Example of **correct** code:

```rust
fn main() {
    assert!('x'.is_ascii_lowercase());
    assert!(b'X'.is_ascii_uppercase());
    assert!('2'.is_ascii_digit());
    assert!('x'.is_ascii_alphabetic());
    assert!('C'.is_ascii_hexdigit());

    '0'.is_ascii_digit();
    'a'.is_ascii_lowercase();
    'A'.is_ascii_uppercase();
}
```

## Further Reading

* [Clippy - manual_is_ascii_check](https://clippy.rust-lang.org/stable/index.html#manual_is_ascii_check)
