Pattern: Missing `# Errors` section in docs

Issue: -

## Description

Documenting the type of errors that can be returned from a
function can help callers write code to handle the errors appropriately.

## What it does

Checks the doc comments of publicly visible functions that
return a `Result` type and warns if there is no `# Errors` section.

## Examples

Since the following function returns a `Result` it has an `# Errors` section in
its doc comment:

```rust
/// # Errors
///
/// Will return `Err` if `filename` does not exist or the user does not have
/// permission to read it.
pub fn read(filename: String) -> io::Result<String> {
    unimplemented!();
}
```

## Further Reading

* [Clippy - missing_errors_doc](https://clippy.rust-lang.org/stable/index.html#missing_errors_doc)
