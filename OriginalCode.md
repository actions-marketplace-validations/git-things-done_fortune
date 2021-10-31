# Original Code

Here is the original code before it was adapted into a standalone GitHub Action:

```yaml
jobs:
  fortune:
    runs-on: ubuntu-latest
    steps:
      - run: |
          set -euxo pipefail
          FORTUNE=$(curl http://yerkee.com/api/fortune -s | jq -r .fortune)
          FORTUNE="${FORTUNE//'%'/'%25'}"
          FORTUNE="${FORTUNE//$'\n'/'%0A'}"
          FORTUNE="${FORTUNE//$'\r'/'%0D'}"
          echo "::set-output name=value::$FORTUNE"
        id: fortune
      - uses: peter-evans/create-or-update-comment@v1
        with:
          issue-number: ${{ needs.daily.outputs.issue }}
          body: |
            # Fortune
            ${{ steps.fortune.outputs.value }}
```

It’s unfortunate actions cannot call other actions.
