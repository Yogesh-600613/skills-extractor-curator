# Knowledge Contract v1

A stable, versioned interchange contract for engineering knowledge extraction and skill curation.

- Both extractors use the same `manifest.json`, `summary.md`, `findings.json`, `evidence-index.md`, and `review.md` structure.
- JSON schema definitions are in `manifest-schema.json` and `findings-schema.json` (Draft 2020-12).
- Evidence is linked from `findings.json` by stable IDs into `evidence-index.md`.
- The `summary.md` template uses sixteen fixed headings; keep their spelling and order.
- Use `null` for unknown optional values, `[]` for known-empty collections, and describe `not-applicable` explicitly in prose.
- Approvals are separate from verification: a real implementation does not establish an approved standard.
- `schema_version` is exactly `1.0.0` for this contract. Change versions deliberately, not ad hoc.

For runtime portability, **distribute the contract with or alongside the extractor**. Reference paths relative to the deployed package, not an unrelated repository that the developer has not opened.
