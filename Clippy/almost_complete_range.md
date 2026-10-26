Pattern: Almost complete character range

Issue: -

## Description

This (`'a'..'z'`) is almost certainly a typo meant to include all letters.

## What it does

Checks for ranges which almost include the entire range of letters from 'a' to 'z'
or digits from '0' to '9', but don't because they're a half open range.

## Examples

Example of **incorrect** code:

```rust
let _ = 'a'..'z';
```

Example of **correct** code:

```rust
let _ = 'a'..='z';
```

## Further Reading

* [Clippy - almost_complete_range](https://clippy.rust-lang.org/stable/index.html#almost_complete_range)
