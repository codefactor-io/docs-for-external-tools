Pattern: Tab character in doc comment

Issue: -

## Description

The rust style-guide promotes spaces instead of tabs for indentation.
To keep a consistent view on the source, also doc comments should not have tabs.
Also, explaining ascii-diagrams containing tabs can get displayed incorrectly when the
display settings of the author and reader differ.

## What it does

Checks doc comments for usage of tab characters.

## Examples

```rust
///
/// Struct to hold two strings:
/// 	- first		one
/// 	- second	one
pub struct DoubleString {
   ///
   /// 	- First String:
   /// 		- needs to be inside here
   first_string: String,
   ///
   /// 	- Second String:
   /// 		- needs to be inside here
   second_string: String,
}
```

Will be converted to:
```rust
///
/// Struct to hold two strings:
///     - first        one
///     - second    one
pub struct DoubleString {
   ///
   ///     - First String:
   ///         - needs to be inside here
   first_string: String,
   ///
   ///     - Second String:
   ///         - needs to be inside here
   second_string: String,
}
```

## Further Reading

* [Clippy - tabs_in_doc_comments](https://clippy.rust-lang.org/stable/index.html#tabs_in_doc_comments)
