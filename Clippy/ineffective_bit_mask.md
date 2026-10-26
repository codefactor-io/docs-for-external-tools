Pattern: Ineffective bit mask in comparison

Issue: -

## Description

Not equally evil as [`bad_bit_mask`](#bad_bit_mask),
but still a bit misleading, because the bit mask is ineffective.

## What it does

Checks for bit masks in comparisons which can be removed
without changing the outcome. The basic structure can be seen in the
following table:

|Comparison| Bit Op   |Example     |equals |
|----------|----------|------------|-------|
|`>` / `<=`|`\|` / `^`|`x \| 2 > 3`|`x > 3`|
|`<` / `>=`|`\|` / `^`|`x ^ 1 < 4` |`x < 4`|

## Examples

Example of **incorrect** code:

```rust
if (x | 1 > 3) {  }
```

Example of **correct** code:

```rust
if (x >= 2) {  }
```

## Known problems

False negatives: This lint will only match instances
where we have figured out the math (which is for a power-of-two compared
value). This means things like `x | 1 >= 7` (which would be better written
as `x >= 6`) will not be reported (but bit masks like this are fairly
uncommon).

## Further Reading

* [Clippy - ineffective_bit_mask](https://clippy.rust-lang.org/stable/index.html#ineffective_bit_mask)
