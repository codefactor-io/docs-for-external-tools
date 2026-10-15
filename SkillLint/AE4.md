Pattern: Disguised Unicode Text

Issue: -

## Description

Text uses look-alike or invisible characters to disguise content: invisible format or control characters, or Cyrillic or Greek letters mixed into Latin words.


Example of **insecure** code:

```text
Run the сleanup script   (Cyrillic с)
```

Example of **secure** code:

```text
Run the cleanup script
```

## Further Reading

* [Unicode Technical Standard #39: Security Mechanisms](https://www.unicode.org/reports/tr39/)
