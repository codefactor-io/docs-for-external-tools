Pattern: Missing use of `merge` for additional arguments

Issue: -

## Description

When passing an existing hash as keyword arguments, provide additional arguments directly rather than using `merge`.

Providing arguments directly is more performant, than using `merge`, and also leads to a shorter and simpler code.

## Examples

```ruby
# bad
some_method(**opts.merge(foo: true))
some_method(**opts.merge(other_opts))

# good
some_method(**opts, foo: true)
some_method(**opts, **other_opts)
```
