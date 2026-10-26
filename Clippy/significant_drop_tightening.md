Pattern: Late drop of significant-drop value

Issue: -

## Description

Elements marked with `#[clippy::has_significant_drop]` are generally synchronizing
primitives that manage shared resources, as such, it is desired to release them as soon as
possible to avoid unnecessary resource contention.

## What it does

Searches for elements marked with `#[clippy::has_significant_drop]` that could be early
dropped but are in fact dropped at the end of their scopes. In other words, enforces the
"tightening" of their possible lifetimes.

## Examples

Example of **incorrect** code:

```rust
fn main() {
  let lock = some_sync_resource.lock();
  let owned_rslt = lock.do_stuff_with_resource();
  // Only `owned_rslt` is needed but `lock` is still held.
  do_heavy_computation_that_takes_time(owned_rslt);
}
```

Example of **correct** code:

```rust
fn main() {
    let owned_rslt = some_sync_resource.lock().do_stuff_with_resource();
    do_heavy_computation_that_takes_time(owned_rslt);
}
```

## Further Reading

* [Clippy - significant_drop_tightening](https://clippy.rust-lang.org/stable/index.html#significant_drop_tightening)
