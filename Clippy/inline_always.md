Pattern: Use of `#[inline(always)]`

Issue: -

## Description

While there are valid uses of this annotation (and once
you know when to use it, by all means `allow` this lint), it's a common
newbie-mistake to pepper one's code with it.

As a rule of thumb, before slapping `#[inline(always)]` on a function,
measure if that additional function call really affects your runtime profile
sufficiently to make up for the increase in compile time.

## What it does

Checks for items annotated with `#[inline(always)]`,
unless the annotated function is empty or simply panics.

## Examples

Example of **incorrect** code:

```rust
#[inline(always)]
fn not_quite_hot_code(..) { ... }
```

## Known problems

False positives, big time. This lint is meant to be
deactivated by everyone doing serious performance work. This means having
done the measurement.

## Further Reading

* [Clippy - inline_always](https://clippy.rust-lang.org/stable/index.html#inline_always)
