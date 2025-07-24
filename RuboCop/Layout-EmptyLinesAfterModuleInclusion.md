Pattern: Empty line after module inclusion

Issue: -

## Description

Checks for an empty line after a module inclusion method (extend, include and prepend), or a group of them.

## Examples

```ruby
# bad
class Foo
  include Bar
  attr_reader :baz
end

# good
class Foo
  include Bar

  attr_reader :baz
end

# also good - multiple module inclusions grouped together
class Foo
  extend Bar
  include Baz
  prepend Qux
end
```

## Further Reading

* [RuboCop - Layout/EmptyLinesAfterModuleInclusion](https://docs.rubocop.org/rubocop/cops_layout.html#layoutemptylinesaftermoduleinclusion)