Pattern: Unnecessary `match` with single binding

Issue: -

## Description

Readability and needless complexity.

## What it does

Checks for useless match that binds to only one value.

## Examples

Example of **incorrect** code:

```rust
match (a, b) {
    (c, d) => {
        // useless match
    }
}
```

Example of **correct** code:

```rust
let (c, d) = (a, b);
```

## Known problems

Suggested replacements may be incorrect when `match`
is actually binding temporary value, bringing a 'dropped while borrowed' error.

## Further Reading

* [Clippy - match_single_binding](https://clippy.rust-lang.org/stable/index.html#match_single_binding)
