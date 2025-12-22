Pattern: Inconsistent HTTP status name

Issue: -

## Description

Enforces consistency by using the current HTTP status names.


## Examples

```ruby
# bad
render json: { error: "Invalid data" }, status: :unprocessable_entity
head :payload_too_large

# good
render json: { error: "Invalid data" }, status: :unprocessable_content
head :content_too_large
```

## Further Reading

* [RuboCop - Rails/HttpStatusNameConsistency](https://docs.rubocop.org/rubocop-rails/cops_rails.html#railshttpstatusnameconsistency)
