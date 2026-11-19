Pattern: Unknown workflow in `workflow_run`

Issue: -

## Description

The `on.workflow_run.workflows` list names a workflow that does not exist in the repository. It must match the workflow's `name`, not its filename.

Correct the workflow name so the trigger can run.

## Examples

Workflow to trigger from:

```yaml
# file: .github/workflows/build.yml
name: Build
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo build
```

Example of **incorrect** code:

```yaml
# file: .github/workflows/ci.yml
on:
  workflow_run:
    workflows: [Biuld]
    types: [completed]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on:
  workflow_run:
    workflows: [Build]
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
