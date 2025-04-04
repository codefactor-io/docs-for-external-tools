Pattern: Testing private method

Issue: -

## Description

Checks for `describe` blocks that test private methods.

If you are doing black box unit testing, it means that you are only interested in testing external behavior, a.k.a public interface, a.k.a public methods. Private methods are considered implementation details and are not directly tested.

If you need to test a Rails callback, test it indirectly through its corresponding Rails public method, e.g. #create, #save, etc.

## Examples

Given this class:
```ruby
class Comment < ApplicationRecord
  after_create_commit :notify_users

  private

  def notify_users
    ...
  end
end
```

Example of **incorrect** code:
```ruby
describe '#notify_users' do
  ...
end
```

Example of **correct** code:
```ruby
describe '#create' do
  it 'notifies users' do
    ...
  end
end
```