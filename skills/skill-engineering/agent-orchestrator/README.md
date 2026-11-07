# agent-orchestrator: Plan a multi-agent AI workflow

Turns a goal too big for one prompt into an orchestration plan with sub-tasks, handoffs, human checkpoints and a brief for every sub-agent.

| | |
|---|---|
| **You give it** | A multi-step goal, the files or data you have, and where it will run (Claude Code sub-agents, a workflow tool, by hand) |
| **You get back** | Sub-tasks with a parallel run order, handoff contracts, human review checkpoints, failure handling and a ready-to-paste brief per sub-agent |
| **Method** | Task decomposition, explicit handoff contracts, human-in-the-loop checkpoints |
| **Search terms** | multi-agent workflow, AI agent orchestration, sub-agent prompts, split a big AI task, human in the loop AI |

It always starts by asking what you're trying to achieve and what you already have, then works through fixed steps. Every claim is traced to your material or labeled as an assumption.

- Skill instructions: [SKILL.md](SKILL.md)

Install the whole collection in Claude Code with `/plugin marketplace add lingegrace/claude-research-skills`, or upload [agent-orchestrator.zip](../../../dist/agent-orchestrator.zip) in Claude.ai under Settings → Capabilities → Skills. See the [main README](../../../README.md).
