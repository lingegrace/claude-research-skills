# skill-eval: Test and evaluate a Claude skill

Turns a skill and a few real example tasks into test cases, pass/fail criteria written up front, a run log and findings.

| | |
|---|---|
| **You give it** | A SKILL.md and 2–5 real tasks it should handle, with what good output looks like |
| **You get back** | Normal, edge and adversarial test cases (including prompt injection), frozen criteria, a run log, graded results and fixes to try |
| **Method** | Criteria-first evaluation: explicit pass/fail criteria set before running, outputs graded against them with quoted evidence |
| **Search terms** | evaluate AI skill, test Claude skill, LLM evaluation test cases, prompt injection test, AI output evaluation criteria |

It always starts by asking what you're trying to achieve and what you already have, then works through fixed steps. Every claim is traced to your material or labeled as an assumption.

- Skill instructions: [SKILL.md](SKILL.md)

Install the whole collection in Claude Code with `/plugin marketplace add lingegrace/claude-research-skills`, or upload [skill-eval.zip](../../../dist/skill-eval.zip) in Claude.ai under Settings → Capabilities → Skills. See the [main README](../../../README.md).
