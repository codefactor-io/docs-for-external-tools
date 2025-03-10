Pattern: Missing use of `File::NULL`

Issue: -

## Description

Use `File::NULL` instead of hardcoding the null device (`/dev/null` on Unix-like OSes, NUL or NUL: on Windows), so that code is platform independent. Only looks for full string matches, substrings within a longer string are not considered.

## Examples

```ruby
# bad
'/dev/null'
'NUL'
'NUL:'

# good
File::NULL

# ok - inside an array
null_devices = %w[/dev/null nul]

# ok - inside a hash
{ unix: "/dev/null", windows: "nul" }
```

## Further Reading

* [RuboCop - Style/FileNull](https://docs.rubocop.org/rubocop/cops_style.html#stylefilenull)
