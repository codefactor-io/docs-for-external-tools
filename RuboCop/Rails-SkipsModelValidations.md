Pattern: Rails/SkipsModelValidations

Issue: -

## Description

This cop checks for the use of methods which skip
validations which are listed in
http://guides.rubyonrails.org/active_record_validations.html#skipping-validations

### Example

```ruby
# bad
Article.first.decrement!(:view_count)
DiscussionBoard.decrement_counter(:post_count, 5)
Article.first.increment!(:view_count)
DiscussionBoard.increment_counter(:post_count, 5)
person.toggle :active
product.touch
Billing.update_all("category = 'authorized', author = 'David'")
user.update_attribute(website: 'example.com')
user.update_columns(last_request_at: Time.current)
Post.update_counters 5, comment_count: -1, action_count: 1

# good
user.update_attributes(website: 'example.com')
FileUtils.touch('file')
```

## Default configuration

Attribute | Value
--- | ---
Blacklist | decrement!, decrement_counter, increment!, increment_counter, toggle!, touch, update_all, update_attribute, update_column, update_columns, update_counters

## Further Reading

* [RuboCop - Rails/SkipsModelValidations](https://rubocop.readthedocs.io/en/latest/cops_rails/#railsskipsmodelvalidations)
* [http://guides.rubyonrails.org/active_record_validations.html#skipping-validations](http://guides.rubyonrails.org/active_record_validations.html#skipping-validations)