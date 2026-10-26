Pattern: Redundant single-component import

Issue: -

## Description

Import with single component use path such as `use cratename;`
is not necessary, and thus should be removed.

## What it does

Checking for imports with single component use path.

## Examples

```rust
use regex;

fn main() {
    regex::Regex::new(r"^\d{4}-\d{2}-\d{2}$").unwrap();
}
```
Better as
```rust
fn main() {
    regex::Regex::new(r"^\d{4}-\d{2}-\d{2}$").unwrap();
}
```

## Further Reading

* [Clippy - single_component_path_imports](https://clippy.rust-lang.org/stable/index.html#single_component_path_imports)
