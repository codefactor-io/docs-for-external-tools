Pattern: Unknown reusable workflow secret

Issue: -

## Description

A reusable workflow receives a named secret that it does not declare under `on.workflow_call.secrets`.

Correct or remove the secret name in the calling job's `secrets` setting.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
    secrets:
      deploy_token:
        required: false
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
    secrets:
      deployment_token: ${{ secrets.DEPLOY_TOKEN }}
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
* [jactionlint - unknown-workflow-secret](https://jactionlint.jdx.dev/rules#unknown-workflow-secret)
