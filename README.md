# Engineering Knowledge Skills — Bootstrap Files

Generic, organization-neutral source material for creating three Agent Skills in one approved development workspace.

## Setup

1. Copy `knowledge-contract/v1/` into the repository where the three skills will be authored.
2. Run `prompts/session-knowledge-extractor.txt` to generate the historical-session extractor. This version has been adjusted to **reuse the existing contract** without overwriting it.
3. Run `prompts/codebase-knowledge-extractor.txt` to generate the codebase extractor against the same contract.
4. Run `prompts/team-skills-curator.txt` to generate the curator and initial empty catalog.
5. Validate that both extractors can create reports with exactly the five specified files, and that JSON validates against the contract.

**Do not** run these creation prompts on an empty repository expecting actual company implementation discoveries. They construct skill instructions and templates. Actual extraction occurs later in an application or session workspace where the skill and contract are available.

Samples under `examples/` are purely fictional and must never be adopted as evidence of actual engineering practices. Keep real reports restricted and subject to review.
