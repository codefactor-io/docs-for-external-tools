Pattern: Memoizing `find_by` results with `||=`

Issue: -

## Description

Avoid memoizing `find_by` results with `||=`.

It is common to see code that attempts to memoize `find_by` result by `||=`, but `find_by` may return `nil`, in which case it is not memoized as intended.

## Examples

```ruby
# bad - exclusively doing memoization
def current_user
  @current_user ||= User.find_by(id: session[:user_id])
end

# good
def current_user
  return @current_user if defined?(@current_user)

  @current_user = User.find_by(id: session[:user_id])
end

# bad - method contains other code
def current_user
  @current_user ||= User.find_by(id: session[:user_id])
  @current_user.do_something
end

# good
def current_user
  if defined?(@current_user)
    @current_user
  else
    @current_user = User.find_by(id: session[:user_id])
  end
  @current_user.do_something
end
```

## Further Reading

* [RuboCop - Rails/FindByOrAssignmentMemoization](https://docs.rubocop.org/rubocop-rails/cops_rails.html#railsfindbyorassignmentmemoization)
