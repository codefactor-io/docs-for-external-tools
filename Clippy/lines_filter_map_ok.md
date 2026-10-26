Pattern: `filter_map(Result::ok)` on `io::Lines`

Issue: -

## Description

`Lines` instances might produce a never-ending stream of `Err`, in which case
`filter_map(Result::ok)` will enter an infinite loop while waiting for an
`Ok` variant. Calling `next()` once is sufficient to enter the infinite loop,
even in the absence of explicit loops in the user code.

This situation can arise when working with user-provided paths. On some platforms,
`std::fs::File::open(path)` might return `Ok(fs)` even when `path` is a directory,
but any later attempt to read from `fs` will return an error.

## What it does

Checks for usage of `lines.filter_map(Result::ok)` or `lines.flat_map(Result::ok)`
when `lines` has type `std::io::Lines`.

## Examples

Example of **incorrect** code:

```rust
let mut lines = BufReader::new(File::open("some-path")?).lines().filter_map(Result::ok);
// If "some-path" points to a directory, the next statement never terminates:
let first_line: Option<String> = lines.next();
```

Example of **correct** code:

```rust
let mut lines = BufReader::new(File::open("some-path")?).lines().map_while(Result::ok);
let first_line: Option<String> = lines.next();
```

## Known problems

This lint suggests replacing `filter_map()` or `flat_map()` applied to a `Lines`
instance in all cases. There are two cases where the suggestion might not be
appropriate or necessary:

- If the `Lines` instance can never produce any error, or if an error is produced
  only once just before terminating the iterator, using `map_while()` is not
  necessary but will not do any harm.
- If the `Lines` instance can produce intermittent errors then recover and produce
  successful results, using `map_while()` would stop at the first error.

## Further Reading

* [Clippy - lines_filter_map_ok](https://clippy.rust-lang.org/stable/index.html#lines_filter_map_ok)
