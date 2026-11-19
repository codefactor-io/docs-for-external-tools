Pattern: Missing reusable workflow secret

Issue: -

## Description

A reusable workflow is called without a secret that it declares as required under `on.workflow_call.secrets`.

Pass the secret under the calling job's `secrets` setting, or use `secrets: inherit` where supported.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
    secrets:
      deploy_token:
        required: true
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **incorrect** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  build:
    uses: ./.github/workflows/build.yml
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  build:
    uses: ./.github/workflows/build.yml
    secrets:
      deploy_token: ${{ secrets.DEPLOY_TOKEN }}
```

## Further Reading

* [jactionlint - Reusable workflows](https://jactionlint.jdx.dev/checks#check-reusable-workflows)
* [jactionlint - missing-workflow-secret](https://jactionlint.jdx.dev/rules#missing-workflow-secret)
