Pattern: Missing `#[inline]` on public item

Issue: -

## Description

When a function is not marked `#[inline]`, it is not
[a “small” candidate for automatic inlining][small], and LTO is not in use, then it is not
possible for the function to be inlined into the code of any crate other than the one in
which it is defined.  Depending on the role of the function and the relationship of the crates,
this could significantly reduce performance.

Certain types of crates might intend for most of the methods in their public API to be able
to be inlined across crates even when LTO is disabled.
This lint allows those crates to require all exported methods to be `#[inline]` by default, and
then opt out for specific methods where this might not make sense.

## What it does

It lints if an exported function, method, trait method with default impl,
or trait method impl is not `#[inline]`.

## Examples

```rust
pub fn foo() {} // missing #[inline]
fn ok() {} // ok
#[inline] pub fn bar() {} // ok
#[inline(always)] pub fn baz() {} // ok

pub trait Bar {
  fn bar(); // ok
  fn def_bar() {} // missing #[inline]
}

struct Baz;
impl Baz {
    fn private() {} // ok
}

impl Bar for Baz {
  fn bar() {} // ok - Baz is not exported
}

pub struct PubBaz;
impl PubBaz {
    fn private() {} // ok
    pub fn not_private() {} // missing #[inline]
}

impl Bar for PubBaz {
    fn bar() {} // missing #[inline]
    fn def_bar() {} // missing #[inline]
}
```

[small]: https://github.com/rust-lang/rust/pull/116505

## Further Reading

* [Clippy - missing_inline_in_public_items](https://clippy.rust-lang.org/stable/index.html#missing_inline_in_public_items)
