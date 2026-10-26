Pattern: `#[test]` in doc example

Issue: -

## Description

Code in examples marked as `#[test]` will somewhat
surprisingly not be run by `cargo test`. If you really want
to show how to test stuff in an example, mark it `no_run` to
make the intent clear.

## What it does

Checks for `#[test]` in doctests unless they are marked with
either `ignore`, `no_run` or `compile_fail`.

## Examples

Example of **incorrect** code:

```rust
/// An example of a doctest with a `main()` function
///
/// # Examples
///
/// ```
/// #[test]
/// fn equality_works() {
///     assert_eq!(1_u8, 1);
/// }
/// ```
fn test_attr_in_doctest() {
    unimplemented!();
}
```

## Further Reading

* [Clippy - test_attr_in_doctest](https://clippy.rust-lang.org/stable/index.html#test_attr_in_doctest)
