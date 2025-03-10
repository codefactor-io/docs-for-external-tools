Pattern: Undecorated string

Issue: -

## Description

Looks for strings that appear to be sentences but are not decorated. Sentences are determined by the `STRING_REGEXP`.

## Examples

```ruby
# bad
"Result is bad."

# good
_("Result is good.")
```

## Further Reading

* [RuboCop - I18n/GetText/DecorateString](https://www.rubydoc.info/gems/rubocop-i18n/3.2.3#i18n-gettext-decoratestring)
