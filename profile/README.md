# UniFormat

Modular readers and writers for tabular data formats, built on one shared data model: **Apache Arrow**.

| Repository | Role |
|---|---|
| [`uniformat-core`](https://github.com/UniFormat/uniformat-core) | Common interfaces (`Format`, registry), byte sources, transactional files, errors. Depends on no format. |
| [`uniformat-sas`](https://github.com/UniFormat/uniformat-sas) | SAS `.sas7bdat`: read and write, plain and compressed (RLE, RDC); Arrow, DataFusion, Flight; Python and R bindings. |
| [`uniformat-cli`](https://github.com/UniFormat/uniformat-cli) | `uniformat` command line: inspect, count, export, convert. |
| [`uniformat-conformance`](https://github.com/UniFormat/uniformat-conformance) | Reference data, validation tools and cross-format round-trip tests. |

Rules of the family:

- every format module depends **only** on `uniformat-core`, never on another format;
- conversions between formats go through the Arrow data model;
- semantic versioning; dependencies between repositories use compatible ranges (`>=0.1,<0.2` while 0.x);
- Python imports live in the `uniformat_io` namespace (`uniformat_io.core`, `uniformat_io.sas`, …).

Status: pre-release (0.1). Source repositories are public; packages are not yet published to registries.
