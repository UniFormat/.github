# Contributing to UniFormat

Thank you for helping. These rules apply to every repository of the organisation unless a repository has its own
`CONTRIBUTING.md`.

## Before you start

- Open an issue (or comment on an existing one) before a large change.
- Keep a change focused: one topic per pull request.

## Architecture rules

- A format repository depends **only** on `uniformat-core`. Never import or depend on another format.
- Data moves between formats through the Arrow data model of `uniformat-core`.
- Format-specific metadata goes in the Arrow schema under the prefix `<format>.` (for example `sas.label`).
- Public APIs must not panic on invalid input: return a typed error.

## Commits and pull requests

- Conventional commits: `feat:`, `fix:`, `docs:`, `chore:`, `refactor:`, `test:`, `ci:`.
- Rust: `cargo fmt --all`, `cargo clippy --workspace --all-targets -- -D warnings`, `cargo test --workspace`.
- Python: `pytest`; R: `testthat`.
- New behaviour needs a test. Bug fixes need a test that fails before the fix.

## Clean-room rule for file-format work

Only use sources whose license allows reading them for this purpose, and never copy code from sources that do not.
The list for each format is in that format's repository. When in doubt, ask in the issue before reading.

## Licensing

Contributions are licensed under the repository license (currently `MIT OR Apache-2.0`, provisional).
