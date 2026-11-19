Pattern: Conflicting action inputs

Issue: -

## Description

Two inputs of a well-known action exclude each other.

The rule `conflicting-action-inputs` reports two inputs of a well-known action that exclude each other, and the rule `missing-action-input` reports an input that works only with another input. Both rules are in the `correctness` profile.

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: run-id and repository are ignored without github-token
      - uses: actions/download-artifact@v4
        with:
          name: build
          run-id: ${{ github.event.workflow_run.id }}
          repository: octo/other
      # ERROR: one of the timeouts is required
      - uses: nick-fields/retry@v3
        with:
          max_attempts: 3
          command: make
      # ERROR: only one of the two identities may be given
      - uses: google-github-actions/auth@v2
        with:
          workload_identity_provider: projects/1/locations/global/workloadIdentityPools/p/providers/g
          credentials_json: '{"type": "service_account"}'
```

## Further Reading

* [jactionlint - Inputs which only work together](https://jactionlint.jdx.dev/checks#check-action-input-dependencies)
* [jactionlint - conflicting-action-inputs](https://jactionlint.jdx.dev/rules#conflicting-action-inputs)
