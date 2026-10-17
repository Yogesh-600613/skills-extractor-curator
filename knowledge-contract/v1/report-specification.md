# Engineering Knowledge Report Specification — v1.0.0

## Principle

A report identifies what an implementation does, what evidence supports it, what requirements or trade-offs explain it, and whether the practice is suitable for wider reuse. **A deviation is not automatically incorrect.** Absence of a report does not mean a quality gate failed.

## Output files

| File | Audience | Contents |
|---|---|---|
| `manifest.json` | Tools / curator | Report metadata, source, repository revision, extraction coverage, method, validation and sharing status |
| `summary.md` | Developer / architect | Readable 16-section overview with references to finding IDs |
| `findings.json` | Curator / tools | One evidence-backed record per relevant implementation pattern, defect, exception or proposed skill |
| `evidence-index.md` | Both | Stable evidence IDs referencing session turns, file and line ranges, commits, tests and documents |
| `review.md` | Approver | Decisions, redactions, unresolved questions, approval and sharing controls |

## Mandatory `summary.md` headings (exact order)

1. Executive Summary
2. Application / Project Profile
3. Architecture and Execution Flow
4. Shared Libraries and Central Dependencies
5. Authentication and Security
6. Exception Handling and Resilience
7. SonarQube and Code Quality
8. Testing and Coverage
9. CI/CD, Packaging, Infrastructure and Operations
10. Historical Decisions and Architectural Evolution
11. Deviations, Exceptions and Alternatives
12. Known Defects, Risks and Technical Debt
13. Golden Implementation Candidates
14. Reusable Skills and Standards Candidates
15. Open Questions and Required Architect Decisions
16. Evidence Coverage and Approval Status

Use heading `## 1. Executive Summary`, etc. Cite `FND-*` within summary, and use corresponding `EVD-*` entries in the evidence index.

## Deep-priority reporting areas

- **Shared library exact usage:** dependency coordinates, resolved/pinned version source, entry classes/methods, initialization and configuration, ordering of calls, and alternatives. Dependencies alone do not establish correct usage.
- **Authentication:** distinguish different flows and environments; trace secrets/token request/cache/expiry/downstream invocation/errors by API and code evidence, without reporting credentials or sensitive values.
- **Exception handling:** central exception classes, translation, propagation, logging, retries, operation idempotency and compensation.
- **Sonar/code quality:** rule identifiers, quality-profile and gate evidence, actual issues and fixes, and whether behavior was preserved. A missing Sonar report is **unknown**, not failed.
- **Testing:** types, meaningful positive/negative cases, commands and test results; for a 90% target distinguish line, branch, overall/new-code, configured target, measured result and exclusions. Never assert actual coverage from an aspirational target.
- **Architecture:** runtime execution flow, integration boundaries, failure paths, packaging, CI/CD, Terraform infrastructure or Databricks data pipelines when present.
- **Historical changes:** requirements, alternatives, rejected approaches, root causes and final behavior when supported by session turns or commit/document evidence.

## Independent classification dimensions

**Evidence confidence:** `verified`, `corroborated`, `inferred`, `unknown`.

**Verification status:** `verified`, `partially-verified`, `unverified`, `unknown`.

**Normative status:** `approved-standard`, `observed-practice`, `approved-exception`, `candidate`, `confirmed-noncompliance`, `known-defect`, `historical-only`, `unresolved`.

**Deviation classification:** `approved-exception`, `justified-alternative-pending-approval`, `unexplained-variation`, `potential-improvement`, `confirmed-noncompliance`, `known-defect`, `historical-workaround`, `superseded-design`, `not-applicable`, `unknown`.

**Reuse scope:** `team-wide`, `technology-specific`, `project-specific`, `not-recommended`, `unknown`.

**Recommendation:** `create-skill`, `update-skill`, `merge-skill`, `keep-existing`, `retire-skill`, `permanent-instruction`, `reference-document`, `automated-check`, `no-action`, `needs-review`.

**Approval status:** `pending`, `approved`, `rejected`, `approved-with-conditions`.

**Sharing status:** `restricted`, `approved-for-internal-sharing`.

These dimensions must not be collapsed: `verified` behavior can still be `known-defect`, and an `approved-exception` may differ from the dominant pattern without being noncompliant.

## Deviation analysis

Before classifying a departure from a baseline, locate the baseline's authority, compare actual behavior, examine functional limitations, compatibility, security, performance or operational needs, search for recorded approvals and compensating controls, and evaluate tests and lifecycle. If those facts are unknown, report an `unexplained-variation` or `justified-alternative-pending-approval` where supported. Never infer noncompliance from frequency alone.

## Evidence and provenance

Each finding links to evidence IDs in `evidence-index.md`. Evidence should contain source type, locator, repository revision / session turn ID, what it directly establishes, collection status and limitations. If lines/commits/turns are inaccessible, indicate unknown rather than inventing an identifier. Reference approved internal source locations without copying secrets.

## Extractor differences

| Field | Historical-session extractor | Codebase extractor |
|---|---|---|
| Source type | `session` | `codebase` |
| Sessions | Actual accessible IDs and turn-coverage | `[]` |
| Git/code evidence | Where relevant/available | Primary evidence |
| Recorded developer intent | From verified historical statements | Only when Git/docs support it; otherwise unknown |
| Report shape | Identical | Identical |

## Approval and publication

Reports are restricted by default, stored locally or in approved restricted storage, and excluded from version control until a reviewer authorizes sanitized sharing. The curator may **propose** standards from pending evidence but must not mark them as approved or publish skills without approval. Maintain an approval and redaction record in `review.md`.

## JSON validation

Both schemas use JSON Schema Draft 2020-12. Validate JSON syntax, required properties, enumerations and evidence cross-links. Structural validation is necessary but not sufficient: a human or an evidence-checking agent must still evaluate factual accuracy.
