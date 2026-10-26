Pattern: Function with high cognitive complexity

Issue: -

## Description

Ideally, we would like to be able to measure how hard a function is
to understand given its context (what we call its Cognitive Complexity).
But that's not what this lint does. See "Known problems"

## What it does

We used to think it measured how hard a method is to understand.

## Known problems

The true Cognitive Complexity of a method is not something we can
calculate using modern technology. This lint has been left in
`restriction` so as to not mislead users into using this lint as a
measurement tool.

For more detailed information, see [rust-clippy#3793](https://github.com/rust-lang/rust-clippy/issues/3793)

## Lints to consider instead of this

* [`excessive_nesting`](https://rust-lang.github.io/rust-clippy/master/index.html#excessive_nesting)
* [`too_many_lines`](https://rust-lang.github.io/rust-clippy/master/index.html#too_many_lines)

## Further Reading

* [Clippy - cognitive_complexity](https://clippy.rust-lang.org/stable/index.html#cognitive_complexity)
