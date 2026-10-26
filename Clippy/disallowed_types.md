Pattern: Use of disallowed type

Issue: -

## Description

Some types are undesirable in certain contexts.

## What it does

Denies the configured types in clippy.toml.

Note: Even though this lint is warn-by-default, it will only trigger if
types are defined in the clippy.toml file.

## Examples

An example clippy.toml configuration:
```toml
# clippy.toml
disallowed-types = [
    # Can use a string as the path of the disallowed type.
    "std::collections::BTreeMap",
    # Can also use an inline table with a `path` key.
    { path = "std::net::TcpListener" },
    # When using an inline table, can add a `reason` for why the type
    # is disallowed.
    { path = "std::net::Ipv4Addr", reason = "no IPv4 allowed" },
    # Can also add a `replacement` that will be offered as a suggestion.
    { path = "std::sync::Mutex", reason = "prefer faster & simpler non-poisonable mutex", replacement = "parking_lot::Mutex" },
    # This would normally error if the path is incorrect, but with `allow-invalid` = `true`,
    # it will be silently ignored
    { path = "std::invalid::Type", reason = "use alternative instead", allow-invalid = true }
]
```

```rust
use std::collections::BTreeMap;
// or its use
let x = std::collections::BTreeMap::new();
```
Use instead:
```rust
// A similar type that is allowed by the config
use std::collections::HashMap;
```

## Further Reading

* [Clippy - disallowed_types](https://clippy.rust-lang.org/stable/index.html#disallowed_types)
