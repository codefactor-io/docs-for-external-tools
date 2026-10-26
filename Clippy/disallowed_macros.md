Pattern: Use of disallowed macro

Issue: -

## Description

Some macros are undesirable in certain contexts, and it's beneficial to
lint for them as needed.

## What it does

Denies the configured macros in clippy.toml

Note: Even though this lint is warn-by-default, it will only trigger if
macros are defined in the clippy.toml file.

## Examples

An example clippy.toml configuration:
```toml
# clippy.toml
disallowed-macros = [
    # Can use a string as the path of the disallowed macro.
    "std::print",
    # Can also use an inline table with a `path` key.
    { path = "std::println" },
    # When using an inline table, can add a `reason` for why the macro
    # is disallowed.
    { path = "serde::Serialize", reason = "no serializing" },
    # This would normally error if the path is incorrect, but with `allow-invalid` = `true`,
    # it will be silently ignored
    { path = "std::invalid_macro", reason = "use alternative instead", allow-invalid = true }
]
```
```rust
use serde::Serialize;

println!("warns");

// The diagnostic will contain the message "no serializing"
#[derive(Serialize)]
struct Data {
    name: String,
    value: usize,
}
```

## Further Reading

* [Clippy - disallowed_macros](https://clippy.rust-lang.org/stable/index.html#disallowed_macros)
