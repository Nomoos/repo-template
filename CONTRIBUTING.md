# Contributing

Thanks for taking the time to help. Issues and pull requests are welcome.

## Before you start

For anything larger than a small fix, please open an issue first so we can agree on the approach.

## Build and test

**.NET** (SDK version from `global.json`):

```bash
dotnet restore
dotnet build --configuration Release
dotnet test --configuration Release
dotnet format          # apply the formatting rules from .editorconfig
```

**Python** (with [uv](https://docs.astral.sh/uv/)):

```bash
uv sync
uv run ruff check .
uv run ruff format .
uv run pyright
uv run pytest
```

## Pull requests

- Keep each pull request focused on one change.
- Add or update tests for the behaviour you change.
- Add a line to `CHANGELOG.md` under "Unreleased".
- CI must be green before merge.

## Commit messages

Short imperative subject line (for example "Add GPX reader"), with details in the body when
they help a reviewer.
