# UniFormat organisation defaults

This repository holds the organisation-wide community files (contributing guide, code of conduct, security policy,
issue and pull request templates), the profile README shown on the organisation page (`profile/`), and the **reusable
GitHub Actions workflows** (`.github/workflows/`) called by every other repository:

- `rust-ci.yml` — format, clippy (`-D warnings`), tests, `cargo deny`;
- `python-ci.yml` — wheel build with maturin (or pure Python install) and `pytest`, on Linux and macOS;
- `r-ci.yml` — `R CMD INSTALL` and `testthat`.

Repositories with path dependencies on a sibling (for example `uniformat-sas` → `uniformat-core`) pass the sibling names in
`siblings`; private siblings need a `CI_TOKEN` secret able to read them. Not yet exercised on GitHub Actions.
