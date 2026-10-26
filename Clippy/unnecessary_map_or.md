Pattern: Unnecessary `map_or()` with `bool` default

Issue: -

## Description

Calls such as `opt.map_or(false, |val| val == 5)` are needlessly long and cumbersome,
and can be reduced to, for example, `opt == Some(5)` assuming `opt` implements `PartialEq`.
Also, calls such as `opt.map_or(true, |val| val == 5)` can be reduced to
`opt.is_none_or(|val| val == 5)`.
This lint offers readability and conciseness improvements.

## What it does

Converts some constructs mapping an Enum value for equality comparison.

## Examples

Example of **incorrect** code:

```rust
pub fn a(x: Option<i32>) -> (bool, bool) {
    (
        x.map_or(false, |n| n == 5),
        x.map_or(true, |n| n > 5),
    )
}
```

Example of **correct** code:

```rust
pub fn a(x: Option<i32>) -> (bool, bool) {
    (
        x == Some(5),
        x.is_none_or(|n| n > 5),
    )
}
```

## Further Reading

* [Clippy - unnecessary_map_or](https://clippy.rust-lang.org/stable/index.html#unnecessary_map_or)
