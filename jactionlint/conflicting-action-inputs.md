Pattern: Conflicting action inputs

Issue: -

## Description

An action receives inputs that cannot be used together. For example, an authentication action may accept either a credentials file or a workload identity provider, but not both.

Choose one of the supported input combinations.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: google-github-actions/auth@v2
        with:
          workload_identity_provider: projects/1/locations/global/workloadIdentityPools/p/providers/g
          credentials_json: '{"type": "service_account"}'
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: google-github-actions/auth@v2
        with:
          credentials_json: '${{ secrets.GCP_CREDENTIALS }}'
```

## Further Reading

* [jactionlint - Inputs which only work together](https://jactionlint.jdx.dev/checks#check-action-input-dependencies)
* [jactionlint - conflicting-action-inputs](https://jactionlint.jdx.dev/rules#conflicting-action-inputs)
