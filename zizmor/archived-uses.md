Pattern: Action from archived repository

Issue: -

## Description

An action or reusable workflow comes from an archived repository. Its code and dependencies no longer receive maintenance, so security issues may remain unfixed.

Replace it with a maintained alternative, or use a supported tool directly.

## Examples

Example of **incorrect** code:

```yaml
on:
  push:
    tags: ["v*"]

jobs:
  release:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/create-release@v1
        env:
          GITHUB_TOKEN: ${{ github.token }}
```

Example of **correct** code:

```yaml
on:
  push:
    tags: ["v*"]

jobs:
  release:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - run: gh release create "$GITHUB_REF_NAME"
        env:
          GH_TOKEN: ${{ github.token }}
```

## Further Reading

* [zizmor - archived-uses](https://docs.zizmor.sh/audits/#archived-uses)
