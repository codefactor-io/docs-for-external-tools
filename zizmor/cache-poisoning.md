Pattern: Cache poisoning risk

Issue: -

## Description

A release workflow restores a cache that an attacker may have poisoned.

Potentially compromised writes to caches, via privileged triggers (see [dangerous-triggers](https://docs.zizmor.sh/audits/#dangerous-triggers)) with jobs that explicitly enable cache-mode: write or cache-mode: write-only.

Example of **incorrect** code:

```yaml
on:
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/setup-node@v5
        with:
          cache: npm
      - run: npm publish
```

Example of **correct** code:

```yaml
on:
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/setup-node@v5
        with:
          package-manager-cache: false
      - run: npm publish
```

## Further Reading

* [zizmor - cache-poisoning](https://docs.zizmor.sh/audits/#cache-poisoning)
