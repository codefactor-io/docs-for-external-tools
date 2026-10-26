Pattern: String slice followed by `as_bytes()`

Issue: -

## Description

It involves doing an unnecessary UTF-8 alignment check which is less efficient, and can cause a panic.

## What it does

Checks for string slices immediately followed by `as_bytes`.

## Examples

Example of **incorrect** code:

```rust
let s = "Lorem ipsum";
s[1..5].as_bytes();
```

Example of **correct** code:

```rust
let s = "Lorem ipsum";
&s.as_bytes()[1..5];
```

## Known problems

In some cases, the UTF-8 validation and potential panic from string slicing may be required for
the code's correctness. If you need to ensure the slice boundaries fall on valid UTF-8 character
boundaries, the original form (`s[1..5].as_bytes()`) should be preferred.

## Further Reading

* [Clippy - sliced_string_as_bytes](https://clippy.rust-lang.org/stable/index.html#sliced_string_as_bytes)
