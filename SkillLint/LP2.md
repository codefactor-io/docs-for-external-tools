Pattern: Wildcard Permission

Issue: -

## Description

The skill manifest declares a wildcard permission (`*`, `all`, `full` or `any`) while the skill ships executable code. A wildcard removes any least-privilege boundary.


Example of **insecure** code:

```yaml
---
name: deploy
permissions:
  - "*"
---
```

Example of **secure** code:

```yaml
---
name: deploy
permissions:
  - network
  - file_read
---
```
