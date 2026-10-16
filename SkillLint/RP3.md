Pattern: Floating skill version

Issue: -

## Description

The skill version in `SKILL.md` floats: `*`, `latest`, `any`, a `>=` floor or a `^` range. An unpinned version lets an update silently replace the reviewed skill (a rug pull).


Example of **insecure** code:

```yaml
---
name: helper
version: latest
---
```

Example of **secure** code:

```yaml
---
name: helper
version: 1.4.2
---
```
