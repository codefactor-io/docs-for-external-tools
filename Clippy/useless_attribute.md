Pattern: Useless attribute on `extern crate` or `use`

Issue: -

## Description

Lint attributes have no effect on crate imports. Most
likely a `!` was forgotten.

## What it does

Checks for `extern crate` and `use` items annotated with
lint attributes.

This lint permits lint attributes for lints emitted on the items themself.
For `use` items these lints are:
* ambiguous_glob_reexports
* dead_code
* deprecated
* hidden_glob_reexports
* unreachable_pub
* unused
* unused_braces
* unused_import_braces
* clippy::disallowed_types
* clippy::enum_glob_use
* clippy::macro_use_imports
* clippy::module_name_repetitions
* clippy::redundant_pub_crate
* clippy::single_component_path_imports
* clippy::unsafe_removed_from_name
* clippy::wildcard_imports

For `extern crate` items these lints are:
* `unused_imports` on items with `#[macro_use]`

## Examples

Example of **incorrect** code:

```rust
#[deny(dead_code)]
extern crate foo;
#[forbid(dead_code)]
use foo::bar;
```

Example of **correct** code:

```rust
#[allow(unused_imports)]
use foo::baz;
#[allow(unused_imports)]
#[macro_use]
extern crate baz;
```

## Further Reading

* [Clippy - useless_attribute](https://clippy.rust-lang.org/stable/index.html#useless_attribute)
