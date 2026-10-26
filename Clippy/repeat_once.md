Pattern: Use of `repeat(1)`

Issue: -

## Description

For example, `String.repeat(1)` is equivalent to `.clone()`. If cloning
the string is the intention behind this, `clone()` should be used.

## What it does

Checks for usage of `.repeat(1)` and suggest the following method for each types.
- `.to_string()` for `str`
- `.clone()` for `String`
- `.to_vec()` for `slice`

The lint will evaluate constant expressions and values as arguments of `.repeat(..)` and emit a message if
they are equivalent to `1`. (Related discussion in [rust-clippy#7306](https://github.com/rust-lang/rust-clippy/issues/7306))

## Examples

Example of **incorrect** code:

```rust
fn main() {
    let x = String::from("hello world").repeat(1);
}
```

Example of **correct** code:

```rust
fn main() {
    let x = String::from("hello world").clone();
}
```

## Further Reading

* [Clippy - repeat_once](https://clippy.rust-lang.org/stable/index.html#repeat_once)
