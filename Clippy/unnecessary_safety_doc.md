Pattern: `# Safety` docs on safe public item

Issue: -

## Description

Safe functions and traits are safe to implement and therefore do not
need to describe safety preconditions that users are required to uphold.

## What it does

Checks for the doc comments of publicly visible
safe functions and traits and warns if there is a `# Safety` section.

## Examples

```rust
/// # Safety
///
/// This function should not be called before the horsemen are ready.
pub fn start_apocalypse_but_safely(u: &mut Universe) {
    unimplemented!();
}
```

The function is safe, so there shouldn't be any preconditions
that have to be explained for safety reasons.

```rust
/// This function should really be documented
pub fn start_apocalypse(u: &mut Universe) {
    unimplemented!();
}
```

## Further Reading

* [Clippy - unnecessary_safety_doc](https://clippy.rust-lang.org/stable/index.html#unnecessary_safety_doc)
