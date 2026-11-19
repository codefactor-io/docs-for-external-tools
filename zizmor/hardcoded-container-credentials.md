Pattern: Hardcoded container registry password

Issue: -

## Description

A container registry password is written directly in the workflow. Anyone who can read the file or its Git history can obtain the password.

Store the password as a GitHub Actions secret and reference it through the `secrets` context.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    container:
      image: registry.example.com/app
      credentials:
        username: user
        password: hackme
    steps:
      - run: echo 'Running in a container'
```

Example of **correct** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    container:
      image: registry.example.com/app
      credentials:
        username: user
        password: ${{ secrets.REGISTRY_PASSWORD }}
    steps:
      - run: echo 'Running in a container'
```

## Further Reading

* [zizmor - hardcoded-container-credentials](https://docs.zizmor.sh/audits/#hardcoded-container-credentials)
