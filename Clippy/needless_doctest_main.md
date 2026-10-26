Pattern: Unnecessary `fn main()` in doctest

Issue: -

## Description

The test can be shorter (and likely more readable)
if the `fn main()` is left implicit.

## What it does

Checks for `fn main() { .. }` in doctests

## Examples

Example of **incorrect** code:

```rust
/// An example of a doctest with a `main()` function
///
/// # Examples
///
/// ```
/// fn main() {
///     // this needs not be in an `fn`
/// }
/// ```
fn needless_main() {
    unimplemented!();
}
```

## Further Reading

* [Clippy - needless_doctest_main](https://clippy.rust-lang.org/stable/index.html#needless_doctest_main)
