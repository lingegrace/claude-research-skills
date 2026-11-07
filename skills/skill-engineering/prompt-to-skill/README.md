# prompt-to-skill: Turn a saved prompt into a skill

Turns a long prompt you keep reusing into a structured Claude skill, with a before/after and a log of what changed.

| | |
|---|---|
| **You give it** | A prompt you reuse (from a notes app, a prompt library, custom instructions), and optionally an output you liked |
| **You get back** | A SKILL.md with trigger, steps, output template and rules, one-off details turned into clarifying questions, a before/after and a change log |
| **Method** | 4-part skill anatomy: trigger (description), method (steps with done-conditions), output (template), rules |
| **Search terms** | convert prompt to skill, reusable prompt template, prompt library to Claude skill, structure a long prompt, prompt engineering template |

It always starts by asking what you're trying to achieve and what you already have, then works through fixed steps. Every claim is traced to your material or labeled as an assumption.

- Skill instructions: [SKILL.md](SKILL.md)

Install the whole collection in Claude Code with `/plugin marketplace add lingegrace/claude-research-skills`, or upload [prompt-to-skill.zip](../../../dist/prompt-to-skill.zip) in Claude.ai under Settings → Capabilities → Skills. See the [main README](../../../README.md).
