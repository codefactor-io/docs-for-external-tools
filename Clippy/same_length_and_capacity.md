Pattern: Same length and capacity in `from_raw_parts()`

Issue: -

## Description

If the same expression is being passed for the length and
capacity, it is most likely a semantic error. In the case of a
Vec, for example, the only way to end up with one that has
the same length and capacity is by going through a boxed slice,
e.g. `Box::from(some_vec)`, which shrinks the capacity to match
the length.

## What it does

Checks for usages of `Vec::from_raw_parts` and `String::from_raw_parts`
where the same expression is used for the length and the capacity.

## Examples

Example of **incorrect** code:

```rust
#![feature(vec_into_raw_parts)]
let mut original: Vec::<i32> = Vec::with_capacity(20);
original.extend([1, 2, 3, 4, 5]);

let (ptr, mut len, cap) = original.into_raw_parts();

// I will add three more integers:
unsafe {
   let ptr = ptr as *mut i32;

   for i in 6..9 {
       *ptr.add(i - 1) = i as i32;
       len += 1;
   }
}

// But I forgot the capacity was separate from the length:
let reconstructed = unsafe { Vec::from_raw_parts(ptr, len, len) };
```

Example of **correct** code:

```rust
#![feature(vec_into_raw_parts)]
let mut original: Vec::<i32> = Vec::with_capacity(20);
original.extend([1, 2, 3, 4, 5]);

let (ptr, mut len, cap) = original.into_raw_parts();

// I will add three more integers:
unsafe {
   let ptr = ptr as *mut i32;

   for i in 6..9 {
       *ptr.add(i - 1) = i as i32;
       len += 1;
   }
}

// This time, leverage the previously saved capacity:
let reconstructed = unsafe { Vec::from_raw_parts(ptr, len, cap) };
```

## Further Reading

* [Clippy - same_length_and_capacity](https://clippy.rust-lang.org/stable/index.html#same_length_and_capacity)
