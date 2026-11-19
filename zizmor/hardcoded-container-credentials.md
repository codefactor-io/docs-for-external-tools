Pattern: Hardcoded container password

Issue: -

## Description

A password for a container registry is written directly in the workflow.

Use [encrypted secrets](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) instead of hardcoded credentials.

Example of **incorrect** code:

```yaml
container:
  image: registry.example.com/app
  credentials:
    username: user
    password: hackme
```

Example of **correct** code:

```yaml
container:
  image: registry.example.com/app
  credentials:
    username: user
    password: ${{ secrets.REGISTRY_PASSWORD }}
```

## Further Reading

* [zizmor - hardcoded-container-credentials](https://docs.zizmor.sh/audits/#hardcoded-container-credentials)
