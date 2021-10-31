# “Fortune” for Git Things Done

Adds a fortune comment to your [Git Things Done](https://github.com/git-things-done/gtd).

```yaml
jobs:
  git-things-done:
    # [snip]…
    - uses: git-things-done/fortune@v1
      continue-on-error: true  # HTTP can be flakey
```

Examples in our [CI Ticket](../../issues/1).
