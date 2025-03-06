Pattern: Unnecessary constant scoping

Issue: -

## Description

Checks for unnecessary constant scoping. Private constants must be defined using `private_constant` or `class << self`. Even if `private` access modifier is used, it is public scope despite its appearance.


## Examples

```ruby
# bad
class Foo
  private
  PRIVATE_CONST = 42
end

# good
class Foo
  PRIVATE_CONST = 42
  private_constant :PRIVATE_CONST
end

# good
class Foo
  class << self
    private
    PRIVATE_CONST = 42
  end
end

# good
class Foo
  PUBLIC_CONST = 42 # If private scope is not intended.
end
```

## Further Reading

* [RuboCop - Lint/UselessConstantScoping](https://docs.rubocop.org/rubocop/cops_lint.html#lintuselessconstantscoping)
