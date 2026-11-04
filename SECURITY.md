# Security policy

UniFormat parses files that may come from untrusted sources. Please report security problems privately.

- Use GitHub's **private vulnerability reporting** ("Security" tab of the affected repository → "Report a vulnerability").
- Do not open a public issue for a vulnerability.
- Include the affected version or commit, a minimal reproducing file if possible, and the observed impact (crash,
  out-of-memory, wrong output…).

Supported versions: the latest 0.x release of each repository (pre-release, no long-term support yet).

Design goals relevant to reports: no panic on invalid input, bounded allocation derived from file fields, no `unsafe`
code in the parsers (FFI boundaries of the Python and R bindings excepted).
