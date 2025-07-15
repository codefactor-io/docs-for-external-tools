Pattern: Use of restricted character

Issue: -

## Description

Checks given banned characters in identifiers(func, var, const). Comments are not checked.

## Configuration

This rule requires a slice of strings, the characters to ban.

## Example:

```toml
[rule.banned-characters]
  arguments =["Ω","Σ","σ"]
```

## Further Reading

* [Revive - banned-characters](https://revive.run/r#banned-characters)
