Pattern: Inconsistent service method name

Issue: -

## Description

Checks for services whose single public method is not named `perform`. Services and jobs with only one public method should have their method named `perform` for consistency. The choice of `perform` as a name is inspired from ActiveJob and makes it easier to make services and jobs interchangeable.

## Examples

Example of **incorrect** code:
```ruby
class ImportCompany
  def import
    ...
  end
end
```

```ruby
class ImportCompany
  def execute
    ...
  end
end
```

Example of **correct** code:
```ruby
class ImportCompany
  def perform
    ...
  end
end
```