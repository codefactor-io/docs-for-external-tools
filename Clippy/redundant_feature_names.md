Pattern: Redundant feature name prefix or suffix

Issue: -

## Description

These prefixes and suffixes have no significant meaning.

## What it does

Checks for feature names with prefix `use-`, `with-` or suffix `-support`

## Examples

Example of **incorrect** code:

```toml
# The `Cargo.toml` with feature name redundancy
[features]
default = ["use-abc", "with-def", "ghi-support"]
use-abc = []  // redundant
with-def = []   // redundant
ghi-support = []   // redundant
```

Example of **correct** code:

```toml
[features]
default = ["abc", "def", "ghi"]
abc = []
def = []
ghi = []
```

## Further Reading

* [Clippy - redundant_feature_names](https://clippy.rust-lang.org/stable/index.html#redundant_feature_names)
