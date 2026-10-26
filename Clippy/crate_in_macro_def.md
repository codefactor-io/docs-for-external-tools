Pattern: Use of `crate` instead of `$crate` in macro

Issue: -

## Description

`crate` refers to the macro call's crate, whereas `$crate` refers to the macro definition's
crate. Rarely is the former intended. See:
https://doc.rust-lang.org/reference/macros-by-example.html#hygiene

## What it does

Checks for usage of `crate` as opposed to `$crate` in a macro definition.

## Examples

```rust
#[macro_export]
macro_rules! print_message {
    () => {
        println!("{}", crate::MESSAGE);
    };
}
pub const MESSAGE: &str = "Hello!";
```
Use instead:
```rust
#[macro_export]
macro_rules! print_message {
    () => {
        println!("{}", $crate::MESSAGE);
    };
}
pub const MESSAGE: &str = "Hello!";
```

Note that if the use of `crate` is intentional, an `allow` attribute can be applied to the
macro definition, e.g.:
```rust
#[allow(clippy::crate_in_macro_def)]
macro_rules! ok { ... crate::foo ... }
```

## Further Reading

* [Clippy - crate_in_macro_def](https://clippy.rust-lang.org/stable/index.html#crate_in_macro_def)
