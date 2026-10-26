Pattern: Missing enforced import rename

Issue: -

## Description

Consistency is important; if a project has defined import renames, then they should be
followed. More practically, some item names are too vague outside of their defining scope,
in which case this can enforce a more meaningful naming.

## What it does

Checks for imports that do not rename the item as specified
in the `enforced-import-renames` config option.

Note: Even though this lint is warn-by-default, it will only trigger if
import renames are defined in the `clippy.toml` file.

## Examples

An example clippy.toml configuration:
```toml
# clippy.toml
enforced-import-renames = [
    { path = "serde_json::Value", rename = "JsonValue" },
]
```

```rust
use serde_json::Value;
```
Use instead:
```rust
use serde_json::Value as JsonValue;
```

## Further Reading

* [Clippy - missing_enforced_import_renames](https://clippy.rust-lang.org/stable/index.html#missing_enforced_import_renames)
