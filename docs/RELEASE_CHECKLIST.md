# Release checklist

Go through this before every release, and especially before v1.0.

## Content

- [ ] The README states what the project does, a working quick start, examples, accuracy and
      limitations, and how it works.
- [ ] Every command and code sample in the README has been run on a clean machine.
- [ ] Every claim in the README (accuracy, performance, compatibility) is backed by a test or a
      measurement.
- [ ] The repository contains no third-party proprietary code, data, screenshots or customer
      names, and nothing that a previous employer or client owns.

## Code

- [ ] CI is green on `main`.
- [ ] Tests cover the public API, including edge cases and real reference data where it applies.
- [ ] No `TODO`, `FIXME`, commented-out code or unused files are left behind.
- [ ] No secrets, tokens or personal data are committed (GitHub secret scanning shows no alerts).
- [ ] Dependencies are current; Dependabot has no open security alerts.

## Release

- [ ] The version number follows semantic versioning and matches the package metadata.
- [ ] `CHANGELOG.md` has a section for the version with the release date.
- [ ] A tag `vX.Y.Z` and a GitHub release with notes are created.
- [ ] Packages (NuGet, PyPI) are published and install from a clean environment.
