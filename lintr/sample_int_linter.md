Pattern: Missing use of `sample.int()`

Issue: -

## Description

`sample.int()` is preferable to `sample()` for the case of sampling numbers between 1 and `n`. `sample` calls `sample.int()` "under the hood".

## Examples

```r
# will produce lints
lint(
  text = "sample(1:10, 2)",
  linters = sample_int_linter()
)

lint(
  text = "sample(seq(4), 2)",
  linters = sample_int_linter()
)

lint(
  text = "sample(seq_len(8), 2)",
  linters = sample_int_linter()
)

# okay
lint(
  text = "sample(seq(1, 5, by = 2), 2)",
  linters = sample_int_linter()
)

lint(
  text = "sample(letters, 2)",
  linters = sample_int_linter()
)
```

## Further Reading

* [lintr - sample_int_linter](https://lintr.r-lib.org/reference/sample_int_linter.html)