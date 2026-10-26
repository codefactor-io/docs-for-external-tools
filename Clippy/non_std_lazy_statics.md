Pattern: Missing use of `std::sync::LazyLock`

Issue: -

## Description

- Reduces the need for an extra dependency
- Enforce convention of using standard library types when possible

## What it does

Lints when `once_cell::sync::Lazy` or `lazy_static!` are used to define a static variable,
and suggests replacing such cases with `std::sync::LazyLock` instead.

Note: This lint will not trigger in crate with `no_std` context, or with MSRV < 1.80.0. It
also will not trigger on `once_cell::sync::Lazy` usage in crates which use other types
from `once_cell`, such as `once_cell::race::OnceBox`.

## Examples

Example of **incorrect** code:

```rust
lazy_static! {
    static ref FOO: String = "foo".to_uppercase();
}
static BAR: once_cell::sync::Lazy<String> = once_cell::sync::Lazy::new(|| "BAR".to_lowercase());
```

Example of **correct** code:

```rust
static FOO: std::sync::LazyLock<String> = std::sync::LazyLock::new(|| "FOO".to_lowercase());
static BAR: std::sync::LazyLock<String> = std::sync::LazyLock::new(|| "BAR".to_lowercase());
```

## Further Reading

* [Clippy - non_std_lazy_statics](https://clippy.rust-lang.org/stable/index.html#non_std_lazy_statics)
