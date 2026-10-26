Pattern: Use of `ok()` to ignore `Result`

Issue: -

## Description

Using `Result::ok()` may look like the result is checked like `unwrap` or `expect` would do
but it only silences the warning caused by `#[must_use]` on the `Result`.

## What it does

Checks for calls to `Result::ok()` without using the returned `Option`.

## Examples

Example of **incorrect** code:

```rust
some_function().ok();
```

Example of **correct** code:

```rust
let _ = some_function();
```

## Further Reading

* [Clippy - unused_result_ok](https://clippy.rust-lang.org/stable/index.html#unused_result_ok)
