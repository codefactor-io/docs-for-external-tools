Pattern: Missing use of `ActionController::Parameters#expect`

Issue: -

## Description

Enforces the use of `ActionController::Parameters#expect` as a method for strong parameter handling.

## Examples

```ruby
# bad
params.require(:user).permit(:name, :age)
params.permit(user: [:name, :age]).require(:user)

# good
params.expect(user: [:name, :age])
```

## Further Reading

* [RuboCop - Rails/StrongParametersExpect](https://docs.rubocop.org/rubocop-rails/cops_rails.html#railsstrongparametersexpect)
