Pattern: Missing use of `matches!`

Issue: -

## Description

Readability and needless complexity.

## What it does

Checks for `match`  or `if let` expressions producing a
`bool` that could be written using `matches!`

## Examples

Example of **incorrect** code:

```rust
let x = Some(5);

let a = match x {
    Some(0) => true,
    _ => false,
};

let a = if let Some(0) = x {
    true
} else {
    false
};
```

Example of **correct** code:

```rust
let x = Some(5);
let a = matches!(x, Some(0));
```

## Known problems

This lint falsely triggers, if there are arms with
`cfg` attributes that remove an arm evaluating to `false`.

## Further Reading

* [Clippy - match_like_matches_macro](https://clippy.rust-lang.org/stable/index.html#match_like_matches_macro)
