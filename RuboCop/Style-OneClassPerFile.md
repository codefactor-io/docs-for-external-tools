Pattern: Mutiple classes per file

Issue: -

## Description

Checks that each source file defines at most one top-level class or module.

Keeping one class or module per file makes it easier to find and navigate code, and follows the convention used by most Ruby projects.

Classes and modules listed in `AllowedClasses` are not counted toward the limit. This is useful for small ancillary classes like custom exception classes that logically belong with the main class.

## Examples

```ruby
# bad
class Foo
end

class Bar
end

# bad
class Foo
end

module Bar
end

# good
class Foo
end

# good
class Foo
  class Bar
  end
end
```

## Further Reading

* [RuboCop - Style/OneClassPerFile](https://docs.rubocop.org/rubocop/latest/cops_style.html#styleoneclassperfile)
