Pattern: Group priority equal to rule in `Cargo.toml`

Issue: -

## Description

The order of lints in the `[lints]` is ignored, to have a lint override a group the
`priority` field needs to be used, otherwise the sort order is undefined.

## What it does

Checks for lint groups with the same priority as lints in the `Cargo.toml`
[`[lints]` table](https://doc.rust-lang.org/cargo/reference/manifest.html#the-lints-section).

This lint will be removed once [cargo#12918](https://github.com/rust-lang/cargo/issues/12918)
is resolved.

## Examples

Example of **incorrect** code:

```toml
# Passed as `--allow=clippy::similar_names --warn=clippy::pedantic`
# which results in `similar_names` being `warn`
[lints.clippy]
pedantic = "warn"
similar_names = "allow"
```

Example of **correct** code:

```toml
# Passed as `--warn=clippy::pedantic --allow=clippy::similar_names`
# which results in `similar_names` being `allow`
[lints.clippy]
pedantic = { level = "warn", priority = -1 }
similar_names = "allow"
```

## Known problems

Does not check lints inherited using `lints.workspace = true`

## Further Reading

* [Clippy - lint_groups_priority](https://clippy.rust-lang.org/stable/index.html#lint_groups_priority)
