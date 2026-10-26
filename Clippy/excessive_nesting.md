Pattern: Excessive block nesting

Issue: -

## Description

It can severely hinder readability.

## What it does

Checks for blocks which are nested beyond a certain threshold.

Note: Even though this lint is warn-by-default, it will only trigger if a maximum nesting level is defined in the clippy.toml file.

## Examples

An example clippy.toml configuration:
```toml
# clippy.toml
excessive-nesting-threshold = 3
```
```rust
// lib.rs
pub mod a {
    pub struct X;
    impl X {
        pub fn run(&self) {
            if true {
                // etc...
            }
        }
    }
}
```
Use instead:
```rust
// a.rs
fn private_run(x: &X) {
    if true {
        // etc...
    }
}

pub struct X;
impl X {
    pub fn run(&self) {
        private_run(self);
    }
}
```
```rust
// lib.rs
pub mod a;
```

## Further Reading

* [Clippy - excessive_nesting](https://clippy.rust-lang.org/stable/index.html#excessive_nesting)
