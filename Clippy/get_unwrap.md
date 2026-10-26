Pattern: Use of `get().unwrap()` instead of indexing

Issue: -

## Description

Using the Index trait (`[]`) is more clear and more
concise.

## What it does

Checks for usage of `.get().unwrap()` (or
`.get_mut().unwrap`) on a standard library type which implements `Index`

## Examples

Example of **incorrect** code:

```rust
let mut some_vec = vec![0, 1, 2, 3];
let last = some_vec.get(3).unwrap();
*some_vec.get_mut(0).unwrap() = 1;
```

Example of **correct** code:

```rust
let mut some_vec = vec![0, 1, 2, 3];
let last = some_vec[3];
some_vec[0] = 1;
```

## Known problems

Not a replacement for error handling: Using either
`.unwrap()` or the Index trait (`[]`) carries the risk of causing a `panic`
if the value being accessed is `None`. If the use of `.get().unwrap()` is a
temporary placeholder for dealing with the `Option` type, then this does
not mitigate the need for error handling. If there is a chance that `.get()`
will be `None` in your program, then it is advisable that the `None` case
is handled in a future refactor instead of using `.unwrap()` or the Index
trait.

## Further Reading

* [Clippy - get_unwrap](https://clippy.rust-lang.org/stable/index.html#get_unwrap)
