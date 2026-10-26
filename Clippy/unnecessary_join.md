Pattern: Unnecessary `Vec` collect before `join()`

Issue: -

## Description

`.collect::<String>()` is more concise and might be more performant

## What it does

Checks for usage of `.collect::<Vec<String>>().join("")` on iterators.

## Examples

Example of **incorrect** code:

```rust
let vector = vec!["hello",  "world"];
let output = vector.iter().map(|item| item.to_uppercase()).collect::<Vec<String>>().join("");
println!("{}", output);
```

Example of **correct** code:

```rust
let vector = vec!["hello",  "world"];
let output = vector.iter().map(|item| item.to_uppercase()).collect::<String>();
println!("{}", output);
```

## Known problems

While `.collect::<String>()` is sometimes more performant, there are cases where
using `.collect::<String>()` over `.collect::<Vec<String>>().join("")`
will prevent loop unrolling and will result in a negative performance impact.

Additionally, differences have been observed between aarch64 and x86_64 assembly output,
with aarch64 tending to producing faster assembly in more cases when using `.collect::<String>()`

## Further Reading

* [Clippy - unnecessary_join](https://clippy.rust-lang.org/stable/index.html#unnecessary_join)
