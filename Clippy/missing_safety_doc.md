Pattern: Missing `# Safety` section in docs

Issue: -

## Description

Unsafe functions should document their safety
preconditions, so that users can be sure they are using them safely.

## What it does

Checks for the doc comments of publicly visible
unsafe functions and warns if there is no `# Safety` section.

## Examples

```rust
/// This function should really be documented
pub unsafe fn start_apocalypse(u: &mut Universe) {
    unimplemented!();
}
```

At least write a line about safety:

```rust
/// # Safety
///
/// This function should not be called before the horsemen are ready.
pub unsafe fn start_apocalypse(u: &mut Universe) {
    unimplemented!();
}
```

## Further Reading

* [Clippy - missing_safety_doc](https://clippy.rust-lang.org/stable/index.html#missing_safety_doc)
