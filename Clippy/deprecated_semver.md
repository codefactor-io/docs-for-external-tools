Pattern: Non-semver `since` in `#[deprecated]`

Issue: -

## Description

For checking the version of the deprecation, it must be
a valid semver. Failing that, the contained information is useless.

## What it does

Checks for `#[deprecated]` annotations with a `since`
field that is not a valid semantic version. Also allows "TBD" to signal
future deprecation.

## Examples

Example of **incorrect** code:

```rust
#[deprecated(since = "forever")]
fn something_else() { /* ... */ }
```

## Further Reading

* [Clippy - deprecated_semver](https://clippy.rust-lang.org/stable/index.html#deprecated_semver)
