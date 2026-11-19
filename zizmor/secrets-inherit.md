Pattern: All secrets inherited

Issue: -

## Description

A reusable workflow is called with secrets: inherit, so it receives every secret of the caller.

[Reusable workflows](https://docs.github.com/en/actions/sharing-automations/reusing-workflows) can be given secrets by their calling workflow either explicitly, or in a blanket fashion with secrets: inherit. The latter should almost never be used, as it makes it violates the [Principle of Least Authority](https://en.wikipedia.org/wiki/Principle_of_least_privilege) and makes it impossible to determine which exact secrets a reusable workflow was executed with.

Example of **incorrect** code:

```yaml
jobs:
  deploy:
    uses: ./.github/workflows/deploy.yml
    secrets: inherit
```

Example of **correct** code:

```yaml
jobs:
  deploy:
    uses: ./.github/workflows/deploy.yml
    secrets:
      DEPLOY_TOKEN: ${{ secrets.DEPLOY_TOKEN }}
```

## Further Reading

* [zizmor - secrets-inherit](https://docs.zizmor.sh/audits/#secrets-inherit)
