# Engineering Knowledge Skills

**Less guesswork. More reusable engineering knowledge.**

This repository is the starting point for three GitHub Copilot Agent Skills that help turn existing development work into practical, evidence-backed guidance. The goal is straightforward: make it easier to reuse proven approaches without losing the context, trade-offs, and decisions behind them.

The workflow is designed for the **GitHub Copilot chat sidebar in VS Code or IntelliJ**, using Agent Mode. No Copilot CLI is required.

## The three skills

| Skill | What it does | When to use it |
| --- | --- | --- |
| `team-knowledge-extractor` | Reconstructs engineering decisions and implementation lessons from accessible historical Copilot sessions, then verifies them against available code. | A relevant Copilot development session exists. |
| `codebase-knowledge-extractor` | Discovers architecture, implementation patterns, quality practices, and relevant Git history directly from a repository. | The codebase is available, with or without AI chat history. |
| `team-skills-curator` | Compares approved findings across projects and proposes reusable skills, instructions, reference materials, or automated checks. | Multiple reviewed knowledge reports are ready for consolidation. |

**Same report format. Different evidence sources. One shared knowledge base.**

## What's in this repository?

```text
.
├── README.md
├── prompts/
│   ├── team-knowledge-extractor.txt
│   ├── codebase-knowledge-extractor.txt
│   └── team-skills-curator.txt
├── knowledge-contract/
│   └── v1/
│       ├── README.md
│       ├── report-specification.md
│       ├── manifest-schema.json
│       ├── findings-schema.json
│       ├── evidence-policy.md
│       ├── approval-policy.md
│       └── report-templates/
└── examples/
    ├── session-report/
    └── codebase-report/
```

This is a **bootstrap package**, not a completed skills library. The `.github/skills/` directories are created after the prompts are run. The example reports are fictional and exist only for validation; they are not engineering evidence.

## Quick start: VS Code + Copilot Agent Mode

1. Open this repository in **VS Code**.
2. Open the **GitHub Copilot chat sidebar** and select **Agent** mode.
3. Select an available approved model. **Claude Sonnet 5** is a suitable option where enabled.
4. Open or attach `prompts/team-knowledge-extractor.txt` to the chat. Ask Copilot to **read the full prompt and implement it in this repository**, reusing `knowledge-contract/v1/` without modifying the contract.
5. Review the generated files. Start a **new Agent chat**, attach `prompts/codebase-knowledge-extractor.txt`, and repeat.
6. Start another new Agent chat with `prompts/team-skills-curator.txt`.
7. Verify the three generated `SKILL.md` files, supporting references, schema compatibility, and review/approval safeguards before committing changes.

**Creation order matters:** the first prompt uses the shared report contract; the second must produce the same report format; the third is built to consume those reports. All three creation tasks run in this repository. Actual extraction happens later in workspaces containing the relevant application code or accessible Copilot sessions.

> **Heads-up:** The prompts build the skills; they do not analyze real applications during setup. Don't expect findings about shared libraries, authentication flows, or coverage from an empty bootstrap repository.

## What does an extraction produce?

Both extractors use `knowledge-contract/v1/` and produce the same five-file report package:

```text
reports/<source-id>/
├── manifest.json        # Source, revision, scope, and analysis status
├── summary.md           # Architect-readable engineering summary
├── findings.json        # Structured findings for comparison and curation
├── evidence-index.md    # Traceable code, Git, test, or session evidence
└── review.md            # Open questions, decisions, and approval status
```

Key areas include shared libraries and their **exact usage**, authentication and exception-handling flows, SonarQube practices, testing and coverage evidence, architecture, delivery practices, and lessons from prior changes.

**An observed pattern is not automatically an approved standard.** A different implementation may be a justified exception, a compatibility solution, or even an improvement. Record the evidence and rationale first; make the standards decision through review.

## Keep the quality bar high

- **Evidence over assumptions:** link findings to code, commits, tests, documentation, or session turns. If the evidence is missing, say so.
- **Context over copy-paste:** document *why* an approach applies, including constraints and alternatives.
- **Verification over confidence:** report actual Sonar and test results. A coverage target is not proof that the target was met.
- **Review before reuse:** proposed skills and standards require appropriate approval; the curator does not self-approve.
- **Keep sensitive data in approved environments:** never publish raw sessions, credentials, confidential application details, or unreviewed reports.
- **No surprise changes:** extraction is read-only for application source and infrastructure. Do not deploy or modify production resources.

## Using the skills beyond this repository

The skills can later be made available in approved VS Code or IntelliJ workspaces. **Distribute the required reporting contract with each extractor, or make the same contract version accessible through an approved shared location.** Copying only `SKILL.md` may leave it without its report templates and schemas.

Knowledge reports should remain local or in approved restricted storage until reviewed. The `examples/` folder must never be counted as real project evidence.

## Done means done

The bootstrap setup is ready for a pilot when:

- All three skills have valid `SKILL.md` metadata and usable supporting references.
- Both extractors target the **same version** of the reporting contract.
- Sample report data validates against the included JSON schemas.
- The curator distinguishes verified facts, proposed standards, justified deviations, and unresolved questions.
- Review, approval, and handling of sensitive information are explicit.

**Build once. Validate properly. Reuse with context.**
