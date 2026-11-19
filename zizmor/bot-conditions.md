Pattern: Spoofable bot actor check

Issue: -

## Description

A condition trusts a bot by its actor name, which an attacker can spoof.

However, this condition is spoofable: `github.actor` refers to the last actor to perform an "action" on the triggering context, and not necessarily the actor actually causing the trigger. An attacker can take advantage of this discrepancy to create a PR where the `HEAD` commit has `github.actor == 'dependabot[bot]'` but the rest of the branch history contains attacker-controlled code, bypassing the actor check.

Example of **incorrect** code:

```yaml
if: github.actor == 'dependabot[bot]'
```

Example of **correct** code:

```yaml
if: github.event.pull_request.user.login == 'dependabot[bot]'
```

## Further Reading

* [zizmor - bot-conditions](https://docs.zizmor.sh/audits/#bot-conditions)
