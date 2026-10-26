Pattern: Print macro in formatting trait impl

Issue: -

## Description

Using a print macro is likely unintentional since formatting traits
should write to the `Formatter`, not stdout/stderr.

## What it does

Checks for usage of `println`, `print`, `eprintln` or `eprint` in an
implementation of a formatting trait.

## Examples

Example of **incorrect** code:

```rust
use std::fmt::{Display, Error, Formatter};

struct S;
impl Display for S {
    fn fmt(&self, f: &mut Formatter) -> Result<(), Error> {
        println!("S");

        Ok(())
    }
}
```

Example of **correct** code:

```rust
use std::fmt::{Display, Error, Formatter};

struct S;
impl Display for S {
    fn fmt(&self, f: &mut Formatter) -> Result<(), Error> {
        writeln!(f, "S");

        Ok(())
    }
}
```

## Further Reading

* [Clippy - print_in_format_impl](https://clippy.rust-lang.org/stable/index.html#print_in_format_impl)
