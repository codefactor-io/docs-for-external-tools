Pattern: Bypassable contains() check

Issue: -

## Description

A contains() condition can be bypassed when an attacker controls the context it searches.

However, this condition will not only evaluate to `true` if either `refs/heads/main` or `refs/heads/develop` is passed, but also for substrings of those values. For example, if someone pushes to a branch named `mai`, then `github.ref` would contain the string `refs/heads/mai` and the job would also execute.

Example of **incorrect** code:

```yaml
if: contains('refs/heads/main refs/heads/develop', github.ref)
```

Example of **correct** code:

```yaml
if: contains(fromJSON('["refs/heads/main", "refs/heads/develop"]'), github.ref)
```

## Further Reading

* [zizmor - unsound-contains](https://docs.zizmor.sh/audits/#unsound-contains)
