Pattern: Use of `secrets: inherit`

Issue: -

## Description

A reusable workflow is called with `secrets: inherit`, giving it access to all secrets available to the caller. This makes it harder to see which secrets are needed and exposes more credentials if the called workflow is compromised.

Pass the required secrets explicitly instead.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  deploy:
    uses: ./.github/workflows/deploy.yml
    secrets: inherit
```

Example of **correct** code:

```yaml
on: push

jobs:
  deploy:
    uses: ./.github/workflows/deploy.yml
    secrets:
      DEPLOY_TOKEN: ${{ secrets.DEPLOY_TOKEN }}
```

## Further Reading

* [zizmor - secrets-inherit](https://docs.zizmor.sh/audits/#secrets-inherit)
