Pattern: Unbounded range in `for` loop

Issue: -

## Description

Using a unbounded range over char and integers will unexpectedly not handle overflows so it will lead to panics
or infinite loops.

Instead there should be a max value set, usually the `MAX` constant for a given type such as `'\0'..char::MAX`
or `250..u8::MAX`.

## What it does

Checks for unbounded for loops over char or integers.

## Examples

Example of **incorrect** code:

```rust
for i in 250u8.. {
  println!("{i}");
}
```

Example of **correct** code:

```rust
for i in 250u8..=u8::MAX {
  println!("{i}");
}
```

## Further Reading

* [Clippy - for_unbounded_range](https://clippy.rust-lang.org/stable/index.html#for_unbounded_range)
