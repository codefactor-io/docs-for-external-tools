Pattern: Regular expression compiled in loop

Issue: -

## Description

Compiling a regex is a much more expensive operation than using one, and a compiled regex can be used multiple times.
This is documented as an antipattern [on the regex documentation](https://docs.rs/regex/latest/regex/#avoid-re-compiling-regexes-especially-in-a-loop)

## What it does

Checks for [regex](https://crates.io/crates/regex) compilation inside a loop with a literal.

## Examples

```rust
for haystack in haystacks {
    let regex = regex::Regex::new(MY_REGEX).unwrap();
    if regex.is_match(haystack) {
        // Perform operation
    }
}
```
can be replaced with
```rust
let regex = regex::Regex::new(MY_REGEX).unwrap();
for haystack in haystacks {
    if regex.is_match(haystack) {
        // Perform operation
    }
}
```

## Further Reading

* [Clippy - regex_creation_in_loops](https://clippy.rust-lang.org/stable/index.html#regex_creation_in_loops)
