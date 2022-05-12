# auto-merge-action

GitHub Action to create a pull request and merge automatically

![pr](images/pr.png?raw=true "pr")

## Usage

Put a workflow file in your `.github/workflows` directory.

```yaml
name: "[chore] Merge pull request from staging to develop"

on:
  push:
    branches:
      - "staging"

permissions:
  contents: write
  pull-requests: write

jobs:
  merge:
    name: "[chore] Merge pull request from staging to develop"
    runs-on: ubuntu-latest
    timeout-minutes: 8
    steps:
      - name: Checkout
        uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Run auto-merge-action
        id: run-auto-merge-action
        uses: yyoshiki41/auto-merge-action@v0.1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          base: develop
          head: staging
```

## Resources

- [Marketplace](https://github.com/marketplace/actions/merge-a-pull-request-automatically)
