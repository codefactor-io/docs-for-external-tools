Pattern: Deprecated `cfg_attr(rustfmt)`

Issue: -

## Description

Since tool_attributes ([rust-lang/rust#44690](https://github.com/rust-lang/rust/issues/44690))
are stable now, they should be used instead of the old `cfg_attr(rustfmt)` attributes.

## What it does

Checks for `#[cfg_attr(rustfmt, rustfmt_skip)]` and suggests to replace it
with `#[rustfmt::skip]`.

## Examples

Example of **incorrect** code:

```rust
#[cfg_attr(rustfmt, rustfmt_skip)]
fn main() { }
```

Example of **correct** code:

```rust
#[rustfmt::skip]
fn main() { }
```

## Known problems

This lint doesn't detect crate level inner attributes, because they get
processed before the PreExpansionPass lints get executed. See
[#3123](https://github.com/rust-lang/rust-clippy/pull/3123#issuecomment-422321765)

## Further Reading

* [Clippy - deprecated_cfg_attr](https://clippy.rust-lang.org/stable/index.html#deprecated_cfg_attr)
