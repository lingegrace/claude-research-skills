# sociology-deep-research: Sociology deep research & literature review

Builds a citation-checked literature review and research dossier on a social question, with claim–evidence tables and an adversarial critique.

A Claude Skill for **doing sociology, not just summarizing it**. It produces a source- and claim-traceable research dossier: a scoping brief, a human checkpoint, a search log, source / claim / evidence / argument ledgers (CSV), an adversarial critique, graded insights, a 10-point scorecard and a readiness gate.

**Good for:** literature reviews, evidence synthesis, and research on social phenomena such as inequality, platforms and the gig economy, gender, digital media, and AI and society. Also good for auditing an existing report for unsupported claims.

**What makes it different:** source identity and claim support are verified separately. Causal claims need an identification strategy. Overlapping studies are clustered so they aren't double-counted. It never claims to be "hallucination-free".

**Modes:** `SCOPING` · `SYNTHESIS` (default) · `PROTOCOL` · `AUDIT`

- Skill instructions: [SKILL.md](SKILL.md)

Install all three: `/plugin marketplace add lingegrace/claude-research-skills` then `/plugin install research-skills@lingegrace-research-skills` in Claude Code, or upload [sociology-deep-research.zip](../../dist/sociology-deep-research.zip) in Claude.ai under Settings → Capabilities → Skills. See the [main README](../../README.md).
