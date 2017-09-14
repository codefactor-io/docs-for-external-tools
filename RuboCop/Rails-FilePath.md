Pattern: Rails/FilePath

Issue: -

## Description

This cop is used to identify usages of file path joining process
to use `Rails.root.join` clause.

### Example

```ruby
# bad
Rails.root.join('app/models/goober')
File.join(Rails.root, 'app/models/goober')
"#{Rails.root}/app/models/goober"

# good
Rails.root.join('app', 'models', 'goober')
```

## Further Reading

* [RuboCop - Rails/FilePath](https://rubocop.readthedocs.io/en/latest/cops_rails/#railsfilepath)