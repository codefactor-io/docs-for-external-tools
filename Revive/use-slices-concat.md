Pattern: Missing use of `slices.Concat`

Issue: -

## Description

Since Go 1.22 the `slices` package provides the `slices.Concat` function that concatenates slices into a new one.
The rule proposes to replace appends to an empty slice, which do the same in a more convoluted way, with a call to `slices.Concat`.

The rule does not use type information, thus it can report appends that `slices.Concat` can not replace,
for example the append of a `string` to a `[]byte`.
Mind also that `slices.Concat` returns `nil` where the appends return an empty slice when all the concatenated slices are empty.

## Examples

Example of **incorrect** code:

```go
content := append(append([]byte{}, magic...), payload...)

allRanges := append([]ignoredRange{}, inlineRanges...)
allRanges = append(allRanges, expandedRanges...)
```

Example of **correct** code:

```go
content := slices.Concat(magic, payload)

allRanges := slices.Concat(inlineRanges, expandedRanges)
```

## Further Reading

* [Revive - use-slices-concat](https://revive.run/r/#use-slices-concat)
