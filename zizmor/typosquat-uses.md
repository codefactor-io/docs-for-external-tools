Pattern: Typosquatted action

Issue: -

## Description

An action reference closely resembles a popular action but is owned by a different account.

Typosquatting attacks rely on a developer mistyping or copy-pasting a slightly wrong name (`action/checkout` instead of `actions/checkout`, `dokcer/login-action` instead of `docker/login-action`). If an attacker registers the misspelled namespace, the workflow or pre-commit hook will fetch and execute their code.

Example of **incorrect** code:

```yaml
- uses: action/checkout@v5
```

Example of **correct** code:

```yaml
- uses: actions/checkout@v5
```

## Further Reading

* [zizmor - typosquat-uses](https://docs.zizmor.sh/audits/#typosquat-uses)
