Pattern: Unnecessary hashes around raw string

Issue: -

## Description

It's just unnecessary, and makes it look like there's more escaping needed than is actually
necessary.

## What it does

Checks for raw string literals with an unnecessary amount of hashes around them.

## Examples

Example of **incorrect** code:

```rust
let r = r###"Hello, "world"!"###;
```

Example of **correct** code:

```rust
let r = r#"Hello, "world"!"#;
```

## Further Reading

* [Clippy - needless_raw_string_hashes](https://clippy.rust-lang.org/stable/index.html#needless_raw_string_hashes)
