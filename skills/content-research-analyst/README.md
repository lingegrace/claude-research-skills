# content-research-analyst: Content research & fact-checking

Turns articles, reports and news into a source-traceable research brief before you write a post, newsletter or report.

A Claude Skill that turns web articles, industry reports, market research and news into a **source-traceable research brief**. Every claim gets a source ID and locator, publication dates are kept apart from event dates, and conflicts between sources are flagged. It never invents statistics, quotes or citations.

**Good for:** researching and fact-checking sources before you write a LinkedIn post, newsletter, X thread or blog article. Produces an English brief, with an optional Chinese or bilingual summary.

**Output:** Executive Summary · Source Register · Key Claims and Evidence · Cross-source Synthesis · Creator-useful Insights · Gaps and Follow-up Research · Content Handoff · Source Notes.

- Skill instructions: [SKILL.md](SKILL.md)
- Optional input brief: [references/input-template.md](references/input-template.md)
- Output contract: [references/output-contract.md](references/output-contract.md)
- Acceptance tests: [references/evaluation-cases.md](references/evaluation-cases.md)

Install all three: `/plugin marketplace add lingegrace/claude-research-skills` then `/plugin install research-skills@lingegrace-research-skills` in Claude Code, or upload [content-research-analyst.zip](../../dist/content-research-analyst.zip) in Claude.ai under Settings → Capabilities → Skills. See the [main README](../../README.md).
