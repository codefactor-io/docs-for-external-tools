Pattern: Malformed decorated message

Issue: -

## Description

Looks for any raise or fail functions and checks that the user visible message is using gettext decoration with the `_()` function. This cop makes sure the message is decorated, as well as checking that the formatting of the message is compliant according to the follow rules.

## Examples

```ruby
# bad
raise("Warning")

# good
raise(_("Warning"))
```

## Further Reading

* [RuboCop - decorate_function_message](https://github.com/rubocop/rubocop-i18n/blob/master/lib/rubocop/cop/i18n/gettext/decorate_function_message.rb)
