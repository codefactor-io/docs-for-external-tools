Pattern: Unicode deception

Issue: -

## Description

Skill metadata uses deceptive Unicode: right-to-left override characters in any field, or Cyrillic/Greek homoglyphs, invisible formatting characters or mixed scripts in the name, triggers and parameter names. These make a malicious skill look identical to a trusted one.


Example of **insecure** code:

```yaml
---
name: gіthub-helper   # Cyrillic і
---
```

Example of **secure** code:

```yaml
---
name: github-helper
---
```

## Further Reading

* [Unicode Technical Standard #39: Security Mechanisms](https://www.unicode.org/reports/tr39/)
