Pattern: Use of `map()` and `flatten()` combination

Issue: -

## Description

Readability. This can be written more concisely with `Iterator::flat_map`, `Option::and_then`, and
`Result::and_then`.

## What it does

Checks for usage of `_.map(_).flatten(_)` on `Iterator`, `Option`, and `Result`.

## Examples

Example of **incorrect** code:

```rust
let vec = vec![vec![1]];
vec.iter().map(|x| x.iter()).flatten();

let opt = Some(5);
opt.map(|x| Some(x * 2)).flatten();

let res: Result<i32, String> = Ok(5);
res.map(|x| Ok(x * 2)).flatten();
```

Example of **correct** code:

```rust
let vec = vec![vec![1]];
vec.iter().flat_map(|x| x.iter());

let opt = Some(5);
opt.and_then(|x| Some(x * 2));

let res: Result<i32, String> = Ok(5);
res.and_then(|x| Ok(x * 2));
```

## Further Reading

* [Clippy - map_flatten](https://clippy.rust-lang.org/stable/index.html#map_flatten)
