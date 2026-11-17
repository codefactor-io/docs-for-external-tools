Pattern: Unnecessary `if` returning boolean literals

Issue: -

## Description

Redundant code.

## What it does

Checks for expressions of the form `if c { true } else {
false }` (or vice versa) and suggests using the condition directly.

This also covers the early-return guard form, where a condition returns a
tuple-like based on it.

## Examples

```rust
if x {
    false
} else {
    true
}
```

Use instead:
```rust
!x
```

Or, for the early-return guard form:
```rust
if c {
    return Ok(true);
}
Ok(false)
```

Use instead:
```rust
Ok(c)
```

## Known problems

Maybe false positives: Sometimes, the two branches are
painstakingly documented (which we, of course, do not detect), so they *may*
have some value. Even then, the documentation can be rewritten to match the
shorter code.

## Further Reading

* [Clippy - needless_bool](https://clippy.rust-lang.org/stable/index.html#needless_bool)
