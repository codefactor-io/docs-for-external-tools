Pattern: Unsupported YAML merge key

Issue: -

## Description

The YAML merge key << is used, which GitHub Actions does not support.

The rules `unused-anchor`, `recursive-alias` and `merge-key` report mistakes with YAML anchors and aliases in a workflow, and `yaml-syntax` reports an alias whose anchor is not defined.

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    services:
      nginx:
        image: nginx:latest
        credentials: &credentials
          # ERROR: Credentials are embedded directly in workflow
          username: my-user-name
          password: P@ssw0rd
          # ERROR: Unexpected key 'email'
          email: me@example.com
      redis:
        image: redis:latest
        credentials: *credentials
    runs-on: ubuntu-latest
    steps:
      - run: ./do_something.sh
```

## Further Reading

* [jactionlint - YAML anchors](https://jactionlint.jdx.dev/checks#yaml-anchors)
* [jactionlint - merge-key](https://jactionlint.jdx.dev/rules#merge-key)
