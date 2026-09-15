Pattern: Runtime mutation of ActiveSupport callback chain

Issue: -

## Description

Avoid mutating ActiveSupport callback chains at runtime.

Calls such as `User.skip_callback` and `User.set_callback` mutate callback chains at process scope.

## Examples

```ruby
# bad
Site.skip_callback(:commit, :after, :after_owner_change)

# bad
Site.set_callback(
  :commit, :after, :after_owner_change,
  if: :saved_change_to_owner?
)

# good
class User < ApplicationRecord
  skip_callback :commit, :after, :after_owner_change
end
```

## Further Reading

* [RuboCop - ThreadSafety/ActiveSupportCallbacks](https://github.com/rubocop/rubocop-thread_safety/blob/master/lib/rubocop/cop/thread_safety/active_support_callbacks.rb)
