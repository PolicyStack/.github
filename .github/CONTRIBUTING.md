# Contributing

Full guide: [policystk.io/contributing](https://policystk.io/contributing/).

## Setup

```sh
mise install                 # pinned toolchain from mise.toml
prek install                 # git hooks; prek run -a checks every file
make -C tools/validator ci   # PolicyStack: what CI runs
```

In `PolicyStack-chart`, bump `version:` in `Chart.yaml` on every chart change. CI fails without it.

## Pull requests

- Title is a Conventional Commit: `<type>(<scope>)!: <subject>`, type one of `feat fix docs chore ci refactor test perf build revert`. Scope and `!` are optional; `!` marks a breaking change.
- PRs are squash-merged. The title becomes the commit on `main`, the description is dropped.
- Update docs in the same PR.

## Chart releases

Chart first, then PolicyStack:

1. Merge the `PolicyStack-chart` PR. Its CI renders every PolicyStack element against the new chart.
2. The release workflow publishes the chart.
3. Renovate opens one PR in PolicyStack bumping every `policy-library` pin. Its `ci` gates the bump.

> [!IMPORTANT]
> Don't bump `policy-library` pins by hand. The pin must point at a published release.
