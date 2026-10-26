Pattern: Missing `Default` implementation

Issue: -

## Description

The user might expect to be able to use
[`Default`](https://doc.rust-lang.org/std/default/trait.Default.html) as the
type can be constructed without arguments.

## What it does

Checks for public types with a `pub fn new() -> Self` method and no
implementation of
[`Default`](https://doc.rust-lang.org/std/default/trait.Default.html).

## Examples

```rust
pub struct Foo(Bar);

impl Foo {
    pub fn new() -> Self {
        Foo(Bar::new())
    }
}
```

To fix the lint, add a `Default` implementation that delegates to `new`:

```rust
pub struct Foo(Bar);

impl Default for Foo {
    fn default() -> Self {
        Foo::new()
    }
}
```

## Further Reading

* [Clippy - new_without_default](https://clippy.rust-lang.org/stable/index.html#new_without_default)
