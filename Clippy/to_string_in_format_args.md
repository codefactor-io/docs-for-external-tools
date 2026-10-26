Pattern: Unnecessary `to_string()` in format args

Issue: -

## Description

Since the type implements `Display`, the use of `to_string` is
unnecessary.

## What it does

Checks for [`ToString::to_string`](https://doc.rust-lang.org/std/string/trait.ToString.html#tymethod.to_string)
applied to a type that implements [`Display`](https://doc.rust-lang.org/std/fmt/trait.Display.html)
in a macro that does formatting.

## Examples

Example of **incorrect** code:

```rust
println!("error: something failed at {}", Location::caller().to_string());
```

Example of **correct** code:

```rust
println!("error: something failed at {}", Location::caller());
```

## Further Reading

* [Clippy - to_string_in_format_args](https://clippy.rust-lang.org/stable/index.html#to_string_in_format_args)
