Pattern: Volatile access to composite type

Issue: -

## Description

Volatile operations are typically used with memory mapped IO devices,
where the precise number and ordering of load and store instructions is
important because they can have side effects. This is well defined for
primitive types like `u32`, but less well defined for structures and
other composite types. In practice it's implementation defined, and the
behavior can be rustc-version dependent.

As a result, code should only apply `write_volatile`/`read_volatile` to
primitive types to be fully well-defined.

## What it does

This lint warns when volatile load/store operations
(`write_volatile`/`read_volatile`) are applied to composite types.

## Examples

```rust
struct MyDevice {
    addr: usize,
    count: usize
}

fn start_device(device: *mut MyDevice, addr: usize, count: usize) {
    unsafe {
        device.write_volatile(MyDevice { addr, count });
    }
}
```
Instead, operate on each primtive field individually:
```rust
struct MyDevice {
    addr: usize,
    count: usize
}

fn start_device(device: *mut MyDevice, addr: usize, count: usize) {
    unsafe {
        (&raw mut (*device).addr).write_volatile(addr);
        (&raw mut (*device).count).write_volatile(count);
    }
}
```

## Further Reading

* [Clippy - volatile_composites](https://clippy.rust-lang.org/stable/index.html#volatile_composites)
