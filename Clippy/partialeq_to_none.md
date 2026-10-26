Pattern: Comparison to `None` with `==` or `!=`

Issue: -

## Description

A programmer checking if some `foo` is `None` via a comparison `foo == None`
is usually inspired from other programming languages (e.g. `foo is None`
in Python).
Checking if a value of type `Option<T>` is (not) equal to `None` in that
way relies on `T: PartialEq` to do the comparison, which is unneeded.

## What it does

Checks for binary comparisons to a literal `Option::None`.

## Examples

Example of **incorrect** code:

```rust
fn foo(f: Option<u32>) -> &'static str {
    if f != None { "yay" } else { "nay" }
}
```

Example of **correct** code:

```rust
fn foo(f: Option<u32>) -> &'static str {
    if f.is_some() { "yay" } else { "nay" }
}
```

## Further Reading

* [Clippy - partialeq_to_none](https://clippy.rust-lang.org/stable/index.html#partialeq_to_none)
