Pattern: Constant reassignment

Issue: -

## Description

Constant reassignment in Ruby is problematic:

In Ruby, when you reassign a constant, you get a warning message because it goes against several important programming principles:

1. Violation of immutability - Constants are meant to represent values that shouldn't change during program execution. When you reassign them, you break this contract, making your code less predictable and harder to reason about.

```ruby
MAX_USERS = 100
MAX_USERS = 200  # warning: already initialized constant MAX_USERS
```

2. Thread safety concerns - If multiple threads are accessing a constant and one thread reassigns it, it can lead to race conditions and unpredictable behavior.

3. Performance implications - Ruby optimizes constant lookups because it assumes they won't change. Reassignment can impact these optimizations.

4. Code maintainability - When other developers see a constant, they expect it to remain constant. Reassignment makes the code harder to understand and maintain.

Instead of reassigning constants, you should:
- Use variables if the value needs to change
- Use frozen objects to ensure true immutability
- Consider using configuration objects or environment variables for values that might need to change

```ruby
# Better approach
SETTINGS = { max_users: 100 }.freeze  # Can't be modified
```

## Examples

```ruby
# bad
X = :foo
X = :bar

# bad
class A
  X = :foo
  X = :bar
end

# bad
module A
  X = :foo
  X = :bar
end

# good - keep only one assignment
X = :bar

class A
  X = :bar
end

module A
  X = :bar
end

# good - use OR assignment
X = :foo
X ||= :bar

# good - use conditional assignment
X = :foo
X = :bar unless defined?(X)

# good - remove the assigned constant first
class A
  X = :foo
  remove_const :X
  X = :bar
end
```

## Further Reading

* [RuboCop - Lint/ConstantReassignment](https://docs.rubocop.org/rubocop/cops_lint.html#lintconstantreassignment)
