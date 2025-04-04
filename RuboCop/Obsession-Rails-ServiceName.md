Pattern: Inconsistent service class name

Issue: -

## Description

Checks that service classes follow a consistent naming convention. Service classes should have names that clearly describe what they do and end with a verb or action word.

## Examples

Example of **incorrect** code:
```ruby
class UserImport
  def perform
    # ...
  end
end
```

```ruby
class CompanyCreator
  def perform
    # ...
  end
end
```

Example of **correct** code:
```ruby
class ImportUser
  def perform
    # ...
  end
end
```

```ruby
class CreateCompany
  def perform
    # ...
  end
end
```