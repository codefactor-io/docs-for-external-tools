Pattern: Unpinned container image

Issue: -

## Description

A container image has no version tag or uses `latest`, so the image can change between workflow runs. Other tags can also be reassigned; zizmor reports those in pedantic mode.

Pin the image to its SHA-256 digest for a stable reference to the intended image.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    container:
      image: registry.example.com/app:latest
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
      image: registry.example.com/app@sha256:01ba4719c80b6fe911b091a7c05124b64eeece964e09c058ef8f9805daca546b
    steps:
      - run: echo 'Running in a container'
```

## Further Reading

* [zizmor - unpinned-images](https://docs.zizmor.sh/audits/#unpinned-images)
