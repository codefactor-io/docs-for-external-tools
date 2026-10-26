Pattern: Double-space line break in doc comment

Issue: -

## Description

Double spaces, when used as hard line break in doc comments, can be difficult to see, and may
accidentally be removed during automatic formatting or manual refactoring. The use of a backslash (`\`)
is clearer in this regard.

## What it does

Detects doc comments that use double spaces as hard line break, instead of backslash (`\`).

## Examples

The two replacement dots (`··`) in this example represent a double space.
```rust
/// This function adds two numbers and returns the result··
/// Overflow can occur when the max value is exceeded.
fn add(l: i32, r: i32) -> i32 {
    l + r
}
```

Use instead:
```rust
/// This function adds two numbers and returns the result\
/// Overflow can occur when the max value is exceeded.
fn add(l: i32, r: i32) -> i32 {
    l + r
}
```

## Further Reading

* [Clippy - doc_comment_double_space_linebreaks](https://clippy.rust-lang.org/stable/index.html#doc_comment_double_space_linebreaks)
