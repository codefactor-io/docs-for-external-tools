Pattern: `String` append with `x = x + y`

Issue: -

## Description

It's not really bad, but some people think that the
`.push_str(_)` method is more readable.

## What it does

Checks for string appends of the form `x = x + y` (without
`let`!).

## Examples

```rust
let mut x = "Hello".to_owned();
x = x + ", World";

// More readable
x += ", World";
x.push_str(", World");
```

## Further Reading

* [Clippy - string_add_assign](https://clippy.rust-lang.org/stable/index.html#string_add_assign)
