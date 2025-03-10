Pattern: Redundant type conversion

Issue: -

## Description

Checks for redundant uses of `to_s`, `to_sym`, `to_i`, `to_f`, `to_r`, `to_c`,
`to_a`, `to_h`, and `to_set`.

When one of these methods is called on an object of the same type, that object
is returned, making the call unnecessary. The cop detects conversion methods called
on object literals, class constructors, class `[]` methods, and the `Kernel` methods
`String()`, `Integer()`, `Float()`, `Rational()`, `Complex()` and `Array()`.

## Examples

```ruby
# bad
"text".to_s
:sym.to_sym
42.to_i
8.5.to_f
12r.to_r
1i.to_c
[].to_a
{}.to_h
Set.new.to_set

# good
"text"
:sym
42
8.5
12r
1i
[]
{}
Set.new

# bad
Integer(var).to_i

# good
Integer(var)

# good - chaining to a type constructor with exceptions suppressed
# in this case, `Integer()` could return `nil`
Integer(var, exception: false).to_i

# bad - chaining the same conversion
foo.to_s.to_s

# good
foo.to_s

# bad - chaining a conversion to a method that is expected to return the same type
inspect.to_s

# good
inspect
```

## Further Reading

* [RuboCop - Lint/RedundantTypeConversion](https://docs.rubocop.org/rubocop/cops_lint.html#lintredundanttypeconversion)
