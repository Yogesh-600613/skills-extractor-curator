# Review and Approval Policy

## Distinct decisions

**Finding accuracy review:** Is the finding faithful to available evidence?

**Internal sharing approval:** May this sanitized report be copied into the approved shared analysis location?

**Standards approval:** Is this pattern actually authorized as an engineering standard or exception?

**Skill publication approval:** May a curator create or change a reusable skill using this evidence?

These are separate gates. Approving report sharing does not approve every suggested engineering standard.

## Workflow

1. All new findings start with `approval_status: pending`; manifests start with `sharing_status: restricted`.
2. Produce `review.md` with deviations, missing evidence, sensitive fields to redact, and clear decisions needed.
3. The responsible developer/architect verifies the report; authorized reviewers decide sharing scope and whether any finding represents an approved pattern.
4. For any skill proposal, the curator gives a separate approval request and a validation plan.
5. Record reviewer role, decision, date, scope, conditions and links to approval evidence without fabricating signatures.
6. Do not publish automatically. If approval is unavailable, retain local/restricted status.
