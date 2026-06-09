# glab-groups-hashicorp

Thin GitHub Actions wrapper for the HashiCorp GitHub organization mirror.

## Scope

- Loads `gh-actions-cfg/glab-groups-hashicorp`
- Calls the reusable workflow in `glab-groups-shared@mcr/main`
- Uses the BWS target PAT secret `GL_PAT_GROUP_HASHICORP_SVC`
- Uses the shared GitHub App secrets `GH_ORG_READ_APP_ID`,
  `GH_ORG_READ_APP_INSTALL_ID`, and `GH_ORG_READ_APP_PEM` for GitHub
  organization discovery and clone auth
- Mirrors the current public `github.com/hashicorp` repositories into
  `hashicorp/*` beneath `glab-forks`
- Runs deterministic mirror batch shards with five jobs max in parallel
- Schedules at minute 5 of hours 5 and 17 UTC
- Publishes discovery, plan, report, CSV, JSON, and Parquet artifacts for each run

## Validation

```sh
python3 -m unittest discover -s tests
```
