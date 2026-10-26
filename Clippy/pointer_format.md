Pattern: Formatting of pointer value

Issue: -

## Description

The addresses are only useful in very specific contexts, and certain projects may want to keep addresses of
certain data structures or functions from prying hacker eyes as an additional line of security.

## What it does

Detects [pointer format] as well as `Debug` formatting of raw pointers or function pointers
or any types that have a derived `Debug` impl that recursively contains them.

## Examples

```rust
let foo = &0_u32;
fn bar() {}
println!("{:p}", foo);
let _ = format!("{:?}", &(bar as fn()));
```

[pointer format]: https://doc.rust-lang.org/std/fmt/index.html#formatting-traits

## Known problems

The lint currently only looks through derived `Debug` implementations. Checking whether a manual
implementation prints an address is left as an exercise to the next lint implementer.

## Further Reading

* [Clippy - pointer_format](https://clippy.rust-lang.org/stable/index.html#pointer_format)
