# Evidence and Attribution Policy

## Evidence precedence

1. Source code and configuration at a recorded revision establish what is present in that revision.
2. Tests and quality reports establish only what they actually measure or exercised at recorded time.
3. Session turns establish what participants requested, proposed, rejected and discussed—not that the code was deployed.
4. Commit messages, design documents and approved standards can establish intent, but must be attributed and may be obsolete.
5. Inferring a rationale solely from a code pattern must be explicitly labelled inferred.

## Evidence record convention

Use stable IDs `EVD-0001`, `EVD-0002`, etc. Each entry in `evidence-index.md` must record:
- Type: `source`, `git`, `test`, `quality`, `session`, `document`, or `other`.
- Exact locator as available: repository-relative path + line numbers, revision and commit, session ID + turn number, test path and timestamp, or approved document section.
- Fact supported and any interpretation that goes beyond it.
- Access limits, stale date, applicable revision and redaction status.

Every `findings.json` reference must have a corresponding evidence entry. Do not invent commit IDs, line numbers, turn counts, test outcomes or approvals. In multi-repository work, identify which repository the evidence belongs to.

## Standardization

An implementation's popularity does not establish an engineering standard. Obtain policy, reference code ownership or architect approval evidence. Distinguish observed pattern, approved exception and confirmed noncompliance. Preserve meaningful alternatives and their constraints.

## Data minimization

Exclude raw secrets, tokens, employee/customer data, private document contents and sensitive runtime logs. Avoid pasting lengthy proprietary source code when precise references suffice. Keep raw history restricted and circulate only reviewed outputs.
