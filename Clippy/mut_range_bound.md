Pattern: Mutable range bound in `for` loop

Issue: -

## Description

One might think that modifying the mutable variable changes the loop bounds. It doesn't.

## What it does

Checks for loops with a range bound that is a mutable variable.

## Examples

Example of **incorrect** code:

```rust
let mut foo = 42;
for i in 0..foo {
    foo -= 1;
    println!("{i}"); // prints numbers from 0 to 41, not 0 to 21
}
```

## Known problems

False positive when mutation is followed by a `break`, but the `break` is not immediately
after the mutation:

```rust
let mut x = 5;
for _ in 0..x {
    x += 1; // x is a range bound that is mutated
    ..; // some other expression
    break; // leaves the loop, so mutation is not an issue
}
```

False positive on nested loops ([#6072](https://github.com/rust-lang/rust-clippy/issues/6072))

## Further Reading

* [Clippy - mut_range_bound](https://clippy.rust-lang.org/stable/index.html#mut_range_bound)
