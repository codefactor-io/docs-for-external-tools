Pattern: Use of `have_content` or `have_no_content`

Issue: -

## Description

Checks for usage of `have_content` and `have_no_content`.

Capybara provides `have_text` and `have_no_text` matchers that are more concise and preferred over their aliases `have_content` and `have_no_content`.

## Examples

```ruby
# bad
expect(page).to have_content('capy')
expect(page).to have_no_content('bara')

# good
expect(page).to have_text('capy')
expect(page).to have_no_text('bara')
```

## Further Reading

* [Capybara/RSpec/HaveContent](https://docs.rubocop.org/rubocop-capybara/latest/cops_capybara_rspec.html#capybararspechavecontent)
