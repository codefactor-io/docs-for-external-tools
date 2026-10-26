Pattern: Case-mismatched arm in case-altering `match`

Issue: -

## Description

The arm is unreachable, which is likely a mistake

## What it does

Checks for `match` expressions modifying the case of a string with non-compliant arms

## Examples

Example of **incorrect** code:

```rust
match &*text.to_ascii_lowercase() {
    "foo" => {},
    "Bar" => {},
    _ => {},
}
```

Example of **correct** code:

```rust
match &*text.to_ascii_lowercase() {
    "foo" => {},
    "bar" => {},
    _ => {},
}
```

## Further Reading

* [Clippy - match_str_case_mismatch](https://clippy.rust-lang.org/stable/index.html#match_str_case_mismatch)
