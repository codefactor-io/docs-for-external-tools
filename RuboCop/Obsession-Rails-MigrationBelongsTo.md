Pattern: Missing use of `belongs_to`

Issue: -

## Description

Checks for migrations that use `references` instead of `belongs_to`. Instead of adding `references` in migrations, use the `belongs_to` alias. It reads nicer and is more similar to the `belongs_to` declarations that you find in model code.

## Examples

Example of **incorrect** code:
```ruby
def change
  add_reference :blog_posts, :user
end
```

```ruby
def change
  create_table :blog_posts do |t|
    t.references :user
  end
end
```

Example of **correct** code:
```ruby
def change
  add_belongs_to :blog_posts, :user
end
```

```ruby
def change
  create_table :blog_posts do |t|
    t.belongs_to :user
  end
end
```