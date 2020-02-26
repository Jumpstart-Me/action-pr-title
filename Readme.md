# Branch naming rules

Github action to enforce Pull Request title conventions

## Usage

See [action.yml](./action.yml)

```yaml
name: PR Title

on:
  pull_request:
    types: [review_requested, edited, opened, assigned]

jobs:
  pr_title:
    runs-on: ubuntu-latest
    steps:
    - uses: cschubiner/action-pr-title@master
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        allowed_prefixes: 'BREAKING CHANGE:,chore:,docs:,feat:,fix:,perf:,refactor:,style:,test:'
        prefix_case_sensitive: true
        min_length: 7 # Min length of the title
        max_length: 200 # Max length of the title

```

Unlike the [main branch](https://github.com/deepakputhraya/action-pr-title), this PR requests changes instead of failing the check. This is because Github doesn't dedupe checks, resulting in the errors encountered here:
https://github.community/t5/GitHub-Actions/duplicate-checks-on-pull-request-event/td-p/33157



## License
The scripts and documentation in this project are released under the [MIT License](./LICENSE)
