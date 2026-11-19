Pattern: Unsafe GitHub App token configuration

Issue: -

## Description

An `actions/create-github-app-token` step requests excessive access or disables token revocation. Setting `owner` without `repositories` grants access to every repository available to the installation. Omitting explicit `permission-*` inputs requests all available installation permissions.

Limit the token to the repositories and permissions the job needs, and leave automatic revocation enabled.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/create-github-app-token@v2
        with:
          app-id: ${{ vars.APP_ID }}
          private-key: ${{ secrets.APP_PRIVATE_KEY }}
          owner: my-org
```

Example of **correct** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/create-github-app-token@v2
        with:
          app-id: ${{ vars.APP_ID }}
          private-key: ${{ secrets.APP_PRIVATE_KEY }}
          owner: my-org
          repositories: my-repo
          permission-contents: read
```

## Further Reading

* [zizmor - github-app](https://docs.zizmor.sh/audits/#github-app)
