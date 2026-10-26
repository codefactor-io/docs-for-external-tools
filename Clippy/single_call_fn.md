Pattern: Function called only once

Issue: -

## Description

If a function is only used once (perhaps because it used to be used more widely),
then the code could be simplified by moving that function's code into its caller.

However, there are reasons not to do this everywhere:

* Splitting a large function into multiple parts often improves readability
  by giving names to its parts.
* A function’s signature might serve a necessary purpose, such as constraining
  the type of a closure passed to it.
* Generic functions might call non-generic functions to reduce duplication
  in the produced machine code.

If this lint is used, prepare to `#[allow]` it a lot.

## What it does

Checks for functions that are only used once. Does not lint tests.

## Examples

Example of **incorrect** code:

```rust
pub fn a<T>(t: &T)
where
    T: AsRef<str>,
{
    a_inner(t.as_ref())
}

fn a_inner(t: &str) {
    /* snip */
}

```

Example of **correct** code:

```rust
pub fn a<T>(t: &T)
where
    T: AsRef<str>,
{
    let t = t.as_ref();
    /* snip */
}

```

## Further Reading

* [Clippy - single_call_fn](https://clippy.rust-lang.org/stable/index.html#single_call_fn)
