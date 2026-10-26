Pattern: `replace()` with no effect

Issue: -

## Description

It's either a mistake or confusing.

## What it does

Checks for `replace` statements which have no effect.

## Examples

Example of **incorrect** code:

```rust
"1234".replace("12", "12");
"1234".replacen("12", "12", 1);
```

## Further Reading

* [Clippy - no_effect_replace](https://clippy.rust-lang.org/stable/index.html#no_effect_replace)
