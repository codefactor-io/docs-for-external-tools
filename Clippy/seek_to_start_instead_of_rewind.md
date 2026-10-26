Pattern: Missing use of `rewind()`

Issue: -

## Description

Readability. There is a specific method that was implemented for
this exact scenario.

## What it does

Checks for jumps to the start of a stream that implements `Seek`
and uses the `seek` method providing `Start` as parameter.

## Examples

Example of **incorrect** code:

```rust
fn foo<T: io::Seek>(t: &mut T) {
    t.seek(io::SeekFrom::Start(0));
}
```

Example of **correct** code:

```rust
fn foo<T: io::Seek>(t: &mut T) {
    t.rewind();
}
```

## Further Reading

* [Clippy - seek_to_start_instead_of_rewind](https://clippy.rust-lang.org/stable/index.html#seek_to_start_instead_of_rewind)
