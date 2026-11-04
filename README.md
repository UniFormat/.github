# UniFormat organisation defaults

This repository holds the organisation-wide community files (contributing guide, code of conduct, security policy,
issue and pull request templates), the profile README shown on the organisation page (`profile/`), and the **reusable
GitHub Actions workflows** (`.github/workflows/`) called by every other repository:

- `rust-ci.yml` — format, clippy (`-D warnings`), tests, `cargo deny`;
- `python-ci.yml` — wheel build with maturin (or pure Python install) and `pytest`, on Linux and macOS;
- `r-ci.yml` — `R CMD INSTALL` and `testthat`.

Repositories with path dependencies on a sibling (for example `uniformat-sas` → `uniformat-core`) pass the sibling names in
`siblings`; private siblings need a `CI_TOKEN` secret able to read them. Not yet exercised on GitHub Actions.

## Security controls

Reusable workflows run with `contents: read`, use actions pinned to full commit SHAs, and never persist checkout credentials. `CI_TOKEN`, when needed for private siblings, must have read-only access to those repositories. Callers pass `sibling-refs` as a JSON mapping of each sibling to a full commit SHA; missing or mutable revisions fail validation. The audit job checks out the same siblings as the build job and scans development dependencies as well as production dependencies.

Keep each caller pinned to the reviewed commit of these workflows. Python jobs install the caller's `ci/requirements-python.txt` with hashes and audit that resolution. Update pins and lockfiles through reviewed changes, then rerun the security tests. Rust corpus tests are explicitly ignored by default; synthetic security tests must run in normal CI. The private SAS conformance corpus is an additional validation step, not a prerequisite for security checks.
