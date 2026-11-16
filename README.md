# repo-template

A starting point for small, well-kept public repositories in C#/.NET or Python. It contains the
parts that every project needs and that are tedious to redo: licence, CI, formatting rules,
issue and PR templates, a README skeleton and a release checklist.

## What you get

| Area | Files |
|---|---|
| CI | [`.github/workflows/ci.yml`](.github/workflows/ci.yml) runs .NET and/or Python checks, depending on which code the repository contains. An empty repository passes. |
| .NET defaults | [`global.json`](global.json) pins the .NET 10 LTS SDK. [`Directory.Build.props`](Directory.Build.props) turns on nullable reference types, the recommended analysers, code-style checks in the build and warnings as errors. |
| Python defaults | [`templates/python/pyproject.toml`](templates/python/pyproject.toml): `uv`, `ruff` (lint and format), `pyright` (strict) and `pytest`. |
| Formatting | [`.editorconfig`](.editorconfig), [`.gitattributes`](.gitattributes) (LF line endings), [`.gitignore`](.gitignore) for .NET, Python and common editors |
| Collaboration | issue forms, a PR template, [`CONTRIBUTING.md`](CONTRIBUTING.md), [`SECURITY.md`](SECURITY.md) |
| Dependencies | [`.github/dependabot.yml`](.github/dependabot.yml) keeps the GitHub Actions current; NuGet and uv entries are ready to enable |
| Documentation | [`docs/PROJECT_README.md`](docs/PROJECT_README.md) (README skeleton), [`docs/RELEASE_CHECKLIST.md`](docs/RELEASE_CHECKLIST.md), [`CHANGELOG.md`](CHANGELOG.md) |

## How CI decides what to run

The `detect` job looks for `*.sln`, `*.slnx` or `*.csproj` files and for a `pyproject.toml` at the
repository root.

| Found | Job | Steps |
|---|---|---|
| .NET project | `dotnet` | restore, build (Release, warnings as errors), test, `dotnet format --verify-no-changes` |
| `pyproject.toml` | `python` | `uv sync`, `ruff check`, `ruff format --check`, `pyright`, `pytest` |

A final `ci` job succeeds only if every job that ran succeeded. Use it as the single required
status check in branch protection.

## Using the template

1. On GitHub choose **Use this template → Create a new repository**.
2. Replace this `README.md` with [`docs/PROJECT_README.md`](docs/PROJECT_README.md) and fill it in.
3. For Python, move [`templates/python/pyproject.toml`](templates/python/pyproject.toml) to the
   root and rename the package. Delete the `templates/` folder.
4. For .NET, keep `global.json` and `Directory.Build.props`; add the solution and projects.
5. Enable the matching Dependabot entries in `.github/dependabot.yml`.
6. Update the copyright line in `LICENSE` if needed, and start `CHANGELOG.md`.

## Licence

[MIT](LICENSE)
