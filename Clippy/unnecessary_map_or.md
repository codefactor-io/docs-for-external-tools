Pattern: Unnecessary `map_or()` with `bool` default

Issue: -

## Description

Calls such as `opt.map_or(false, |val| val == 5)` are needlessly long and cumbersome,
and can be reduced to, for example, `opt == Some(5)` assuming `opt` implements `PartialEq`.
Also, calls such as `opt.map_or(true, |val| val == 5)` can be reduced to
`opt.is_none_or(|val| val == 5)`.
Calls that map the two variants of a `Result` to opposite boolean constants can be
reduced to `is_ok()` or `is_err()`.
This lint offers readability and conciseness improvements.

## What it does

Converts some constructs mapping an enum value for equality or variant checks.

## Examples

Example of **incorrect** code:

```rust
pub fn a(x: Option<i32>, result: Result<i32, i32>) -> (bool, bool, bool) {
    (
        x.map_or(false, |n| n == 5),
        x.map_or(true, |n| n > 5),
        result.map_or_else(|_| false, |_| true),
    )
}
```

Example of **correct** code:

```rust
pub fn a(x: Option<i32>, result: Result<i32, i32>) -> (bool, bool, bool) {
    (
        x == Some(5),
        x.is_none_or(|n| n > 5),
        result.is_ok(),
    )
}
```

## Further Reading

* [Clippy - unnecessary_map_or](https://clippy.rust-lang.org/stable/index.html#unnecessary_map_or)
