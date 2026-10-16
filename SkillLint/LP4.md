Pattern: Overdeclared permission

Issue: -

## Description

The skill manifest declares a permission (shell, network, file read or write, environment, MCP) but none of the skill's executable files show a matching capability. Unused permissions may be leftovers or pre-staging for later abuse.


Example of **insecure** code:

```yaml
---
name: formatter
permissions:
  - network   # no network code in the skill
---
```

Example of **secure** code:

```yaml
---
name: formatter
permissions:
  - file_read
  - file_write
---
```
