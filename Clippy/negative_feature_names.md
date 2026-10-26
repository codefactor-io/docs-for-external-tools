Pattern: Negative feature name

Issue: -

## Description

Features are supposed to be additive, and negatively-named features violate it.

## What it does

Checks for negative feature names with prefix `no-` or `not-`

## Examples

Example of **incorrect** code:

```toml
# The `Cargo.toml` with negative feature names
[features]
default = []
no-abc = []
not-def = []

```

Example of **correct** code:

```toml
[features]
default = ["abc", "def"]
abc = []
def = []

```

## Further Reading

* [Clippy - negative_feature_names](https://clippy.rust-lang.org/stable/index.html#negative_feature_names)
