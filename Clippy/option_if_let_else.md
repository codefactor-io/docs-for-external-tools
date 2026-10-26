Pattern: Missing use of `Option::map_or()`

Issue: -

## Description

Using the dedicated functions of the `Option` type is clearer and
more concise than an `if let` expression.

## What it does

Lints usage of `if let Some(v) = ... { y } else { x }` and
`match .. { Some(v) => y, None/_ => x }` which are more
idiomatically done with `Option::map_or` (if the else bit is a pure
expression) or `Option::map_or_else` (if the else bit is an impure
expression).

## Examples

Example of **incorrect** code:

```rust
let _ = if let Some(foo) = optional {
    foo
} else {
    5
};
let _ = match optional {
    Some(val) => val + 1,
    None => 5
};
let _ = if let Some(foo) = optional {
    foo
} else {
    let y = do_complicated_function();
    y*y
};
```

Example of **correct** code:

```rust
let _ = optional.map_or(5, |foo| foo);
let _ = optional.map_or(5, |val| val + 1);
let _ = optional.map_or_else(||{
    let y = do_complicated_function();
    y*y
}, |foo| foo);
```

## Notes

This lint uses a deliberately conservative metric for checking if the
inside of either body contains loop control expressions `break` or
`continue` (which cannot be used within closures). If these are found,
this lint will not be raised.

## Further Reading

* [Clippy - option_if_let_else](https://clippy.rust-lang.org/stable/index.html#option_if_let_else)
