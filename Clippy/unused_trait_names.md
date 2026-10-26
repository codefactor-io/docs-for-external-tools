Pattern: Trait imported by name but used anonymously

Issue: -

## Description

Traits imported that aren't used directly can be imported anonymously with `use Trait as _`.
It is more explicit, avoids polluting the current scope with unused names and can be useful to show which imports are required for traits.

## What it does

Checks for `use Trait` where the Trait is only used for its methods and not referenced by a path directly.

## Examples

Example of **incorrect** code:

```rust
use std::fmt::Write;

fn main() {
    let mut s = String::new();
    let _ = write!(s, "hello, world!");
    println!("{s}");
}
```

Example of **correct** code:

```rust
use std::fmt::Write as _;

fn main() {
    let mut s = String::new();
    let _ = write!(s, "hello, world!");
    println!("{s}");
}
```

## Further Reading

* [Clippy - unused_trait_names](https://clippy.rust-lang.org/stable/index.html#unused_trait_names)
