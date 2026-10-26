Pattern: Missing `# Panics` section in docs

Issue: -

## Description

Documenting the scenarios in which panicking occurs
can help callers who do not want to panic to avoid those situations.

## What it does

Checks the doc comments of publicly visible functions that
may panic and warns if there is no `# Panics` section.

## Examples

Since the following function may panic it has a `# Panics` section in
its doc comment:

```rust
/// # Panics
///
/// Will panic if y is 0
pub fn divide_by(x: i32, y: i32) -> i32 {
    if y == 0 {
        panic!("Cannot divide by 0")
    } else {
        x / y
    }
}
```

Individual panics within a function can be ignored with `#[expect]` or
`#[allow]`:

```rust
pub fn will_not_panic(x: usize) {
    #[expect(clippy::missing_panics_doc, reason = "infallible")]
    let y = NonZeroUsize::new(1).unwrap();

    // If any panics are added in the future the lint will still catch them
}
```

## Further Reading

* [Clippy - missing_panics_doc](https://clippy.rust-lang.org/stable/index.html#missing_panics_doc)
