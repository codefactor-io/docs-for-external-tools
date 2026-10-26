Pattern: Unnecessary `if` returning boolean literals

Issue: -

## Description

Redundant code.

## What it does

Checks for expressions of the form `if c { true } else {
false }` (or vice versa) and suggests using the condition directly.

## Examples

Example of **incorrect** code:

```rust
if x {
    false
} else {
    true
}
```

Example of **correct** code:

```rust
!x
```

## Known problems

Maybe false positives: Sometimes, the two branches are
painstakingly documented (which we, of course, do not detect), so they *may*
have some value. Even then, the documentation can be rewritten to match the
shorter code.

## Further Reading

* [Clippy - needless_bool](https://clippy.rust-lang.org/stable/index.html#needless_bool)
