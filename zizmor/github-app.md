Pattern: Dangerous GitHub App token

Issue: -

## Description

A GitHub App installation token is requested with broader access than the workflow needs.

GitHub Apps provide an alternative authentication mechanism to GitHub Actions' built-in `secrets.GITHUB_TOKEN`. Typically, users request an installation token for a GitHub App via [actions/create-github-app-token](https://github.com/actions/create-github-app-token) and then use that token where the default `secrets.GITHUB_TOKEN` would have been used.

Example of **incorrect** code:

```yaml
- uses: actions/create-github-app-token@v2
  with:
    app-id: ${{ vars.APP_ID }}
    private-key: ${{ secrets.APP_PRIVATE_KEY }}
    owner: my-org
```

Example of **correct** code:

```yaml
- uses: actions/create-github-app-token@v2
  with:
    app-id: ${{ vars.APP_ID }}
    private-key: ${{ secrets.APP_PRIVATE_KEY }}
    repositories: my-repo
    permission-contents: read
```

## Further Reading

* [zizmor - github-app](https://docs.zizmor.sh/audits/#github-app)
