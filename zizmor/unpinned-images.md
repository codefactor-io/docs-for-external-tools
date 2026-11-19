Pattern: Unpinned container image

Issue: -

## Description

A container image is not pinned by a tag other than latest or by a SHA-256 digest.

When image references are unpinned or are pinned to a mutable tag, the workflow is at risk because the image used will be unpredictable over time. Changes made to the OCI registry used to source the image may result in untrusted images gaining access to your workflow.

Example of **incorrect** code:

```yaml
container:
  image: node:latest
```

Example of **correct** code:

```yaml
container:
  image: node:24.11.0
```

## Further Reading

* [zizmor - unpinned-images](https://docs.zizmor.sh/audits/#unpinned-images)
