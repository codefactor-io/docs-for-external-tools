Pattern: Use of absolute path

Issue: -

## Description

Many codebases have their own style when it comes to importing, but one that is seldom used
is using absolute paths *everywhere*. This is generally considered unidiomatic, and you
should add a `use` statement.

The default maximum segments (2) is pretty strict, you may want to increase this in
`clippy.toml`.

Note: One exception to this is code from macro expansion - this does not lint such cases, as
using absolute paths is the proper way of referencing items in one.

## What it does

Checks for usage of items through absolute paths, like `std::f64::consts::PI`.

## Examples

```rust
let x = std::f64::consts::PI;
```
Use any of the below instead, or anything else:
```rust
use std::f64;
use std::f64::consts;
use std::f64::consts::PI;
let x = f64::consts::PI;
let x = consts::PI;
let x = PI;
use std::f64::consts as f64_consts;
let x = f64_consts::PI;
```

## Known issues

There are currently a few cases which are not caught by this lint:
* Macro calls. e.g. `path::to::macro!()`
* Derive macros. e.g. `#[derive(path::to::macro)]`
* Attribute macros. e.g. `#[path::to::macro]`

## Further Reading

* [Clippy - absolute_paths](https://clippy.rust-lang.org/stable/index.html#absolute_paths)
