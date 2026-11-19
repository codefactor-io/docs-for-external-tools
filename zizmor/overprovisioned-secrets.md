Pattern: Whole secrets context exposed

Issue: -

## Description

The entire secrets context is passed into the runner instead of the secrets the step needs.

This allows the Actions runner to only expose the secrets actually used by the workflow to the job environment.

Example of **incorrect** code:

```yaml
env:
  SECRETS: ${{ toJSON(secrets) }}
```

Example of **correct** code:

```yaml
env:
  SECRET_ONE: ${{ secrets.SECRET_ONE }}
  SECRET_TWO: ${{ secrets.SECRET_TWO }}
```

## Further Reading

* [zizmor - overprovisioned-secrets](https://docs.zizmor.sh/audits/#overprovisioned-secrets)
