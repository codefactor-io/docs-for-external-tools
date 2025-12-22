Pattern: `Module` member existence check

Issue: -

## Description

Checks for usage of `Module` methods returning arrays that can be replaced with equivalent predicates.

Calling a method returning an array then checking if an element is inside it is much slower than using an equivalent predicate method. For example, `instance_methods.include?` will return an array of all public and protected instance methods in the module, then check if a given method is inside that array, while `method_defined?` will do direct method lookup, which is much faster and consumes less memory.

## Examples

```ruby
# bad
Array.instance_methods.include?(:size)
Array.instance_methods.member?(:size)
Array.instance_methods(true).include?(:size)

Array.instance_methods(false).include?(:find)

# good
Array.method_defined?(:size)

Array.method_defined?(:find, false)
```

## Further Reading

* [RuboCop - Style/ModuleMemberExistenceCheck](https://docs.rubocop.org/rubocop/cops_style.html#stylemodulememberexistencecheck)
