Pattern: Function with large stack frame

Issue: -

## Description

The stack region of memory is very limited in size (usually *much* smaller than the heap) and attempting to
use too much will result in a stack overflow and crash the program.
To avoid this, you should consider allocating large types on the heap instead (e.g. by boxing them).

Keep in mind that the code path to construction of large types does not even need to be reachable;
it purely needs to *exist* inside of the function to contribute to the stack size.
For example, this causes a stack overflow even though the branch is unreachable:
```rust
fn main() {
    if false {
        let x = [0u8; 10000000]; // 10 MB stack array
        black_box(&x);
    }
}
```

## What it does

Checks for functions that use a lot of stack space.

This often happens when constructing a large type, such as an array with a lot of elements,
or constructing *many* smaller-but-still-large structs, or copying around a lot of large types.

This lint is a more general version of [`large_stack_arrays`](https://rust-lang.github.io/rust-clippy/master/#large_stack_arrays)
that is intended to look at functions as a whole instead of only individual array expressions inside of a function.

## Examples

This function creates four 500 KB arrays on the stack. Quite big but just small enough to not trigger `large_stack_arrays`.
However, looking at the function as a whole, it's clear that this uses a lot of stack space.
```rust
struct QuiteLargeType([u8; 500_000]);
fn foo() {
    // ... some function that uses a lot of stack space ...
    let _x1 = QuiteLargeType([0; 500_000]);
    let _x2 = QuiteLargeType([0; 500_000]);
    let _x3 = QuiteLargeType([0; 500_000]);
    let _x4 = QuiteLargeType([0; 500_000]);
}
```

Instead of doing this, allocate the arrays on the heap.
This currently requires going through a `Vec` first and then converting it to a `Box`:
```rust
struct NotSoLargeType(Box<[u8]>);

fn foo() {
    let _x1 = NotSoLargeType(vec![0; 500_000].into_boxed_slice());
//                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  Now heap allocated.
//                                                                The size of `NotSoLargeType` is 16 bytes.
//  ...
}
```

## Known issues

False positives. The stack size that clippy sees is an estimated value and can be vastly different
from the actual stack usage after optimizations passes have run (especially true in release mode).
Modern compilers are very smart and are able to optimize away a lot of unnecessary stack allocations.
In debug mode however, it is usually more accurate.

This lint works by summing up the size of all variables that the user typed, variables that were
implicitly introduced by the compiler for temporaries, function arguments and the return value,
and comparing them against a (configurable, but high-by-default).

## Further Reading

* [Clippy - large_stack_frames](https://clippy.rust-lang.org/stable/index.html#large_stack_frames)
