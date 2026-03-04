Pattern: Use of `File.open` without a block

Issue: -

## Description

Checks for `File.open` without a block, which can leak file descriptors.

When `File.open` is called without a block, the caller is responsible for closing the file descriptor. If it is not explicitly closed, it will only be closed when the garbage collector runs, which may lead to resource exhaustion. Using the block form ensures the file is automatically closed when the block exits.

## Examples

```ruby
# bad
f = File.open('file')

# bad
File.open('file').read

# good
File.open('file') do |f|
  f.read
end

# good
File.open('file', &:read)

# good - use File.read for one-shot reads
File.read('file')
```

## Further Reading

* [RuboCop - Style/FileOpen](https://docs.rubocop.org/rubocop/latest/cops_style.html#stylefileopen)
