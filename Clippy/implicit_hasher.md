Pattern: Missing generalization over hasher type

Issue: -

## Description

`HashMap` or `HashSet` with custom hashers cannot be
used with them.

## What it does

Checks for public `impl` or `fn` missing generalization
over different hashers and implicitly defaulting to the default hashing
algorithm (`SipHash`).

## Examples

Example of **incorrect** code:

```rust
impl<K: Hash + Eq, V> Serialize for HashMap<K, V> { }

pub fn foo(map: &mut HashMap<i32, i32>) { }
```

Example of **correct** code:

```rust
impl<K: Hash + Eq, V, S: BuildHasher> Serialize for HashMap<K, V, S> { }

pub fn foo<S: BuildHasher>(map: &mut HashMap<i32, i32, S>) { }
```

## Known problems

Suggestions for replacing constructors can contain
false-positives. Also applying suggestions can require modification of other
pieces of code, possibly including external crates.

## Further Reading

* [Clippy - implicit_hasher](https://clippy.rust-lang.org/stable/index.html#implicit_hasher)
