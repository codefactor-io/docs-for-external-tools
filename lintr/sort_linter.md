Pattern: Malformed use of `order()`/`sort()`

Issue: -

## Description

This linter checks for some common mistakes when using `order()` or `sort()`.

First, it requires usage of `sort()` over `.[order(.)]`.

`sort()` is the dedicated option to sort a list or vector. It is more legible
and around twice as fast as `.[order(.)]`, with the gap in performance
growing with the vector size.

Second, it requires usage of `is.unsorted)` over equivalents using `sort()`.

The base function `is.unsorted()` exists to test the sortedness of a vector.
  Prefer it to inefficient and less-readable equivalents like
  `x != sort(x)`. The same goes for checking `x == sort(x)` -- use
  `!is.unsorted(x)` instead.

Moreover, use of `x == sort(x)` can be risky because `sort()` drops missing
  elements by default, meaning `==` might end up trying to compare vectors
  of differing lengths.

## Examples

```r
# will produce lints
lint(
  text = "x[order(x)]",
  linters = sort_linter()
)

lint(
  text = "x[order(x, decreasing = TRUE)]",
  linters = sort_linter()
)

lint(
  text = "sort(x) == x",
  linters = sort_linter()
)

# okay
lint(
  text = "x[sample(order(x))]",
  linters = sort_linter()
)

lint(
  text = "y[order(x)]",
  linters = sort_linter()
)

lint(
  text = "sort(x, decreasing = TRUE) == x",
  linters = sort_linter()
)

# If you are sorting several objects based on the order of one of them, such
# as:
x <- sample(1:26)
y <- letters
newx <- x[order(x)]
newy <- y[order(x)]
# This will be flagged by the linter. However, in this very specific case,
# it would be clearer and more efficient to run order() once and assign it
# to an object, rather than mix and match order() and sort()
index <- order(x)
newx <- x[index]
newy <- y[index]
```

## Further Reading

* [lintr - sort_linter](https://lintr.r-lib.org/reference/sort_linter.html)