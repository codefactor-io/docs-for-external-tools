Pattern: Integer literal with leading zero

Issue: -

## Description

In some languages (including the infamous C language
and most of its
family), this marks an octal constant. In Rust however, this is a decimal
constant. This could
be confusing for both the writer and a reader of the constant.

## What it does

Warns if an integral constant literal starts with `0`.

## Examples

In Rust:
```rust
fn main() {
    let a = 0123;
    println!("{}", a);
}
```

prints `123`, while in C:

```c
#include <stdio.h>

int main() {
    int a = 0123;
    printf("%d\n", a);
}
```

prints `83` (as `83 == 0o123` while `123 == 0o173`).

## Further Reading

* [Clippy - zero_prefixed_literal](https://clippy.rust-lang.org/stable/index.html#zero_prefixed_literal)
