Pattern: Missing use of `slices` package

Issue: -

## Description

Since Go 1.21 the `slices` package proposes methods that are faster and easier to use than their equivalents in `sort` package. The rule proposes to replace these legacy idioms with calls to the new methods.

## Examples

Example of **incorrect** code:

```r
sort.Float64s(temperatures)
sort.Ints(years)
sort.Strings(names)
sort.Slice(cfg.Dependencies, func(i, j int) bool {
	return cfg.Dependencies[i].Name < cfg.Dependencies[j].Name
})
```

Example of **correct** code:

```r
slices.Sort(temperatures)
slices.Sort(years)
slices.Sort(names)
slices.SortFunc(cfg.Dependencies, func(a, b config.Dependency) int {
	return cmp.Compare(a.Name, b.Name)
})
```

## Further Reading

* [Revive - use-slices-sort](https://revive.run/r#use-slices-sort)