Pattern: Cache poisoning risk

Issue: -

## Description

A release workflow restores cached files that an attacker may have modified in another workflow. Using those files can compromise the release. Privileged workflows that process untrusted code can also poison caches when cache writes are enabled.

Disable caching in release jobs with `cache-mode: none`, or disable cache restoration in each cache-aware action. Avoid cache writes from jobs that run untrusted code.

## Examples

Example of **incorrect** code:

```yaml
on:
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
        with:
          persist-credentials: false
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
    cache-mode: none
    steps:
      - uses: actions/checkout@v5
        with:
          persist-credentials: false
      - uses: actions/setup-node@v5
        with:
          cache: npm
      - run: npm publish
```

## Further Reading

* [zizmor - cache-poisoning](https://docs.zizmor.sh/audits/#cache-poisoning)
