Pattern: Use of underscore-prefixed item

Issue: -

## Description

A single leading underscore is usually used to indicate
that a item will not be used. Using such a item breaks this
expectation.

## What it does

Checks for the use of item with a single leading
underscore.

## Examples

Example of **incorrect** code:

```rust
fn _foo() {}

struct _FooStruct {}

fn main() {
    _foo();
    let _ = _FooStruct{};
}
```

Example of **correct** code:

```rust
fn foo() {}

struct FooStruct {}

fn main() {
    foo();
    let _ = FooStruct{};
}
```

## Further Reading

* [Clippy - used_underscore_items](https://clippy.rust-lang.org/stable/index.html#used_underscore_items)
