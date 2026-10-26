Pattern: Collection that is never read

Issue: -

## Description

Putting effort into constructing a collection but then never querying it might indicate that
the author forgot to do whatever they intended to do with the collection. Example: Clone
a vector, sort it for iteration, but then mistakenly iterate the original vector
instead.

## What it does

Checks for collections that are never queried.

## Examples

Example of **incorrect** code:

```rust
let mut sorted_samples = samples.clone();
sorted_samples.sort();
for sample in &samples { // Oops, meant to use `sorted_samples`.
    println!("{sample}");
}
```

Example of **correct** code:

```rust
let mut sorted_samples = samples.clone();
sorted_samples.sort();
for sample in &sorted_samples {
    println!("{sample}");
}
```

## Further Reading

* [Clippy - collection_is_never_read](https://clippy.rust-lang.org/stable/index.html#collection_is_never_read)
