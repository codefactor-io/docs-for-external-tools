Pattern: Untrusted input in script

Issue: -

## Description

An attacker-controllable value is expanded with ${{ }} into a script or another place where it runs as code.

GitHub Actions allows workflows to define template expansions, which occur within special `${{ ... }}` delimiters. These expansions happen before workflow and job execution, meaning the expansion of a given expression appears verbatim in whatever context it was performed in.

Example of **incorrect** code:

```yaml
- name: Check title
  run: echo "${{ github.event.issue.title }}"
```

Example of **correct** code:

```yaml
- name: Check title
  run: echo "$ISSUE_TITLE"
  env:
    ISSUE_TITLE: ${{ github.event.issue.title }}
```

## Further Reading

* [zizmor - template-injection](https://docs.zizmor.sh/audits/#template-injection)
