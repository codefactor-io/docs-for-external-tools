Pattern: Inconsistent empty class

Issue: -

## Description

Enforces consistent style for empty class definitions.

The supported styles are:

	class_definition (default) - prefer standard class definition over `Class.new`

	class_new - prefer `Class.new` over class definition

## Examples

#### EnforcedStyle: class_keyword (default)

```ruby
# bad
FooError = Class.new(StandardError)

# okish
class FooError < StandardError; end

# good
class FooError < StandardError
end
```

#### EnforcedStyle: class_new

```
# bad
class FooError < StandardError
end

# bad
class FooError < StandardError; end

# good
FooError = Class.new(StandardError)
```

## Further Reading

* [RuboCop - Style/EmptyClassDefinition](https://docs.rubocop.org/rubocop/latest/cops_style.html#styleemptyclassdefinition)
