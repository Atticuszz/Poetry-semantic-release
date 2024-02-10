# Poetry-semantic-release
> it's ci action of conbining the `python-semantic-release` and `Poetry` publish to pypi

1. make sure change `ATTICUS_PAT` as your personal full permission github token
2. make sure the `PYPI_API_TOKEN` as your pypi token 
```main.yml
name: CI/CD

on:
  push:
    branches:
      - main
  pull_request:
  workflow_dispatch:
jobs:
  publish:
    #    needs: test
    runs-on: ubuntu-latest
    name: "Bump version, create changelog and publish"
    steps:
      - name: Clone Repository
        uses: actions/checkout@v3
        with:
          ref: ${{ github.ref }}
          fetch-depth: 0
          token: ${{ secrets.ATTICUS_PAT }}

      - name: Python Package Release
        uses: Atticuszz/Poetry-semantic-release@main
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          pypi_token: ${{ secrets.PYPI_API_TOKEN }}

```
