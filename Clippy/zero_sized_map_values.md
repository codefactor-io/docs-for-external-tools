Pattern: Map with zero-sized value type

Issue: -

## Description

Since there is only a single value for a zero-sized type, a map
containing zero sized values is effectively a set. Using a set in that case improves
readability and communicates intent more clearly.

## What it does

Checks for maps with zero-sized value types anywhere in the code.

## Examples

Example of **incorrect** code:

```rust
fn unique_words(text: &str) -> HashMap<&str, ()> {
    todo!();
}
```

Example of **correct** code:

```rust
fn unique_words(text: &str) -> HashSet<&str> {
    todo!();
}
```

## Known problems

* A zero-sized type cannot be recovered later if it contains private fields.
* This lints the signature of public items

## Further Reading

* [Clippy - zero_sized_map_values](https://clippy.rust-lang.org/stable/index.html#zero_sized_map_values)
