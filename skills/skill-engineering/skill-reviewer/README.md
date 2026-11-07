# skill-reviewer: Review and fix a Claude skill

Turns an existing SKILL.md into a scored review, a frontmatter check, a prioritised fix list and a revised version.

| | |
|---|---|
| **You give it** | A SKILL.md you wrote or installed, and optionally examples of runs that went wrong |
| **You get back** | A scorecard on 9 criteria with quoted evidence, a YAML frontmatter check, a prioritised fix list and a revised SKILL.md |
| **Method** | Fixed review rubric based on the 4-part skill anatomy (trigger, steps with done-conditions, output template, rules) |
| **Search terms** | review Claude skill, SKILL.md checklist, skill not triggering, improve AI skill, skill frontmatter error |

It always starts by asking what you're trying to achieve and what you already have, then works through fixed steps. Every claim is traced to your material or labeled as an assumption.

- Skill instructions: [SKILL.md](SKILL.md)

Install the whole collection in Claude Code with `/plugin marketplace add lingegrace/claude-research-skills`, or upload [skill-reviewer.zip](../../../dist/skill-reviewer.zip) in Claude.ai under Settings → Capabilities → Skills. See the [main README](../../../README.md).
