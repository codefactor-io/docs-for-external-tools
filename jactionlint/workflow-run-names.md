Pattern: Unknown workflow in workflow_run

Issue: -

## Description

A workflow_run event refers to a workflow which does not exist in the repository.

The rule `workflow-run-names` reports a name in `on.workflow_run.workflows` that no workflow of the repository has.

Example of **incorrect** code:

```yaml
on:
  workflow_run:
    # ERROR: No workflow named "Biuld" exists in the repository
    workflows: [Biuld]
    types: [completed]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Workflow names of workflow_run event](https://jactionlint.jdx.dev/checks#check-workflow-run-names)
* [jactionlint - workflow-run-names](https://jactionlint.jdx.dev/rules#workflow-run-names)
