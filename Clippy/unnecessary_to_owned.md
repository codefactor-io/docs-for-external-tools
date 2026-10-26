Pattern: Unnecessary `to_owned()`-like call

Issue: -

## Description

The unnecessary calls result in useless allocations.

## What it does

Checks for unnecessary calls to [`ToOwned::to_owned`](https://doc.rust-lang.org/std/borrow/trait.ToOwned.html#tymethod.to_owned)
and other `to_owned`-like functions.

## Examples

Example of **incorrect** code:

```rust
let path = std::path::Path::new("x");
foo(&path.to_string_lossy().to_string());
fn foo(s: &str) {}
```

Example of **correct** code:

```rust
let path = std::path::Path::new("x");
foo(&path.to_string_lossy());
fn foo(s: &str) {}
```

## Known problems

`unnecessary_to_owned` can falsely trigger if `IntoIterator::into_iter` is applied to an
owned copy of a resource and the resource is later used mutably. See
[#8148](https://github.com/rust-lang/rust-clippy/issues/8148).

## Further Reading

* [Clippy - unnecessary_to_owned](https://clippy.rust-lang.org/stable/index.html#unnecessary_to_owned)
