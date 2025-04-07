Pattern: Negation matcher after `visit`

Issue: -

## Description

Do not allow negative matchers to be used immediately after `visit`.

## Examples

```ruby
# bad
visit foo_path
expect(page).to have_no_link('bar')
expect(page).to have_css('a')

# good
visit foo_path
expect(page).to have_css('a')
expect(page).to have_no_link('bar')

# bad
visit foo_path
expect(page).not_to have_link('bar')
expect(page).to have_css('a')

# good
visit foo_path
expect(page).to have_css('a')
expect(page).not_to have_link('bar')
```

## Further Reading

* [RuboCop - Capybara/NegationMatcherAfterVisit](https://docs.rubocop.org/rubocop-capybara/cops_capybara.html#capybaranegationmatcheraftervisit)

