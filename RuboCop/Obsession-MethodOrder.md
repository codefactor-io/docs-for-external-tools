Pattern: Inconsistent private method order

Issue: -

## Description

Checks for private/protected methods that are not ordered correctly.

Note 1: the order of public methods is not enforced. They can be defined in any order the developer wants, like by order of importance. This is because public methods are usually called outside of the class and often not called within the class at all. If possible though, developers should still try to order their public methods when it makes sense.

Note 2: for top to bottom styles, method order cannot be computed for methods called by `send`, metaprogramming, private methods called by superclasses or modules, etc. This cop's suggestions and autocorrections may be slightly off for these cases.

Note 3: for simplicity, protected methods do not have to be ordered if there are both a protected section and a private section.

## Examples

Example of **incorrect** code with `EnforcedStyle: drill_down` (default):
```ruby
class Foo
  def perform
    return if method_a?
    method_b
    method_c
  end

  private

  def method_c; ...; end
  def method_b; ...; end
  def method_a?; ...; end
end
```

Example of **correct** code with `EnforcedStyle: drill_down` (default):
```ruby
class Foo
  def perform
    return if method_a?
    method_b
    method_c
  end

  private

  def method_a?; ...; end
  def method_b; ...; end
  def method_c; ...; end
end
```

Example of **incorrect** code with `EnforcedStyle: drill_down` (default):
```ruby
class Foo
  def perform
    method_a
    method_b
  end

  private

  def method_a; method_c; end
  def method_b; method_c; end
  def method_c; ...; end
end
```

Example of **correct** code with `EnforcedStyle: drill_down` (default):
```ruby
class Foo
  def perform
    method_a
    method_b
  end

  private

  def method_a; method_c; end
  def method_c; ...; end
  def method_b; method_c; end
end
```

Example of **incorrect** code with `EnforcedStyle: step_down`:
```ruby
class Foo
  def perform
    method_a
    method_b
  end

  private

  def method_a; method_c; end
  def method_c; ...; end
  def method_b; method_c; end
end
```

Example of **correct** code with `EnforcedStyle: step_down`:
```ruby
class Foo
  def perform
    method_a
    method_b
  end

  private

  def method_a; method_c; end
  def method_b; method_c; end
  def method_c; ...; end
end
```

Example of **incorrect** code with `EnforcedStyle: alphabetical`:
```ruby
class Foo
  def perform; ...; end

  private

  def method_c; ...; end
  def method_b; ...; end
  def method_a; ...; end
end
```

Example of **correct** code with `EnforcedStyle: alphabetical`:
```ruby
class Foo
  def perform; ...; end

  private

  def method_a; ...; end
  def method_b; ...; end
  def method_c; ...; end
end
```