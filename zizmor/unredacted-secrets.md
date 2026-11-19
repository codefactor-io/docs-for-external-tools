Pattern: Secret bypasses redaction

Issue: -

## Description

A secret is used in a way that GitHub Actions cannot redact from the logs.

This allows the Actions runner to redact the secret values from the job logs, as it knows the exact string value of each secret.

Example of **incorrect** code:

```yaml
env:
  PASSWORD: ${{ fromJSON(secrets.CREDENTIALS).password }}
```

Example of **correct** code:

```yaml
env:
  PASSWORD: ${{ secrets.PASSWORD }}
```

## Further Reading

* [zizmor - unredacted-secrets](https://docs.zizmor.sh/audits/#unredacted-secrets)
