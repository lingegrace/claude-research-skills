# Claude Research Skills: Deep Research, Literature Review & Competitive Analysis

[![Claude Skills](https://img.shields.io/badge/Claude-Agent%20Skills-D97757)](https://github.com/lingegrace/claude-research-skills)
[![Claude Code plugin](https://img.shields.io/badge/Claude%20Code-plugin%20marketplace-222)](#install-in-claude-code-one-command)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**Three free, open-source [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) (`SKILL.md`) for research you can trust. They turn Claude into a research analyst that cites its sources, separates fact from interpretation, and never invents numbers or citations.** They work in **Claude Code**, **Claude.ai**, the **Claude desktop app**, and anything that loads Agent Skills.

- 🔎 **[research-analyst](skills/research-analyst/)**: an AI research assistant for creators. Turns articles, industry reports and news into a source-traceable research brief before you write a LinkedIn post, newsletter or blog.
- 🎓 **[sociology-deep-research](skills/sociology-deep-research/)**: an AI literature review tool for social science. Produces a citation-checked research dossier with claim–evidence tables, an argument map and an adversarial critique.
- 📊 **[competitive-market-research](skills/competitive-market-research/)**: an AI competitive intelligence analyst for B2B product marketing (PMM) and strategy teams. Builds competitor profiles, sales battlecards, market landscapes, pricing teardowns and win-loss analysis.

[中文说明 ↓](#中文说明)

---

## Why these skills? (fixing AI research hallucinations)

Most "deep research" prompts give you fluent text with invented statistics, fake citations, and causal claims the evidence never supported. These skills build guardrails into every run:

| Problem with ordinary AI research | What these skills do instead |
|---|---|
| Hallucinated sources, DOIs, quotes and numbers | **Never invent**: a missing field is marked `Not provided` / `Not verified` |
| "The source exists" treated as "the source supports the claim" | **Two separate checks**: source identity (`VERIFIED`…) and claim support (`DIRECT` / `PARTIAL` / `NO_SUPPORT`) |
| Correlation written up as causation | Each **claim type** (descriptive, associational, causal, mechanism…) needs matching evidence |
| One press release echoed by 12 outlets counted as 12 confirmations | **Study / signal clusters** count independent evidence, not URLs |
| AI runs off in the wrong direction | **Human-in-the-loop checkpoint** after scoping, before deep research |
| Confirmation bias, or telling the sponsor what they want to hear | **Adversarial critique** and a **mirror battlecard** pass |

---

## The skills

### 1. `research-analyst`: source-traceable research brief for content creators

**Use it for:** summarizing and fact-checking articles, reports and news before you write.
**You get:** an 8-section Markdown Research Brief: executive summary, source register, claim–evidence table (claim IDs + source locators), cross-source synthesis and conflicts, creator-ready insights with the "overclaim to avoid", research gaps, and a content handoff.
**Also:** English-first with an optional Chinese or bilingual summary; ignores prompt injection hidden inside source documents; keeps publication date, event date and data period apart.
→ [Read the skill](skills/research-analyst/SKILL.md)

### 2. `sociology-deep-research`: AI literature review and research dossier

**Use it for:** literature reviews, a systematic-style synthesis, or an evidence map of a social phenomenon (inequality, platforms, labor, gender, AI and society…).
**You get:** a research brief, a search log, `sources.csv`, `claims.csv`, `evidence.csv`, `arguments.csv`, an adversarial critique, insights graded as *Evidence-supported synthesis / Plausible interpretation / New hypothesis*, a 10-point scorecard, and a readiness gate.
**Modes:** `SCOPING` (quick brief) · `SYNTHESIS` (full dossier) · `PROTOCOL` (research plan) · `AUDIT` (check an existing report).
→ [Read the skill](skills/sociology-deep-research/SKILL.md)

### 3. `competitive-market-research`: competitive intelligence and battlecards

**Use it for:** competitor analysis, sales battlecards, market maps, SaaS pricing and packaging teardowns, feature-parity checks, and win-loss diagnostics.
**You get:** sources graded in **tiers T1–T5** (SEC filings and pricing pages down to vendor marketing), signal-cluster accounting, a **mirror battlecard** (the competitor's view of *you*), findings graded **FACT / READ / BET**, and implications graded **ACT / WATCH / RESEARCH-MORE** with tripwires.
**Modes:** `SCOUT` · `PROFILE` · `BATTLECARD` · `LANDSCAPE` · `WIN-LOSS`.
→ [Read the skill](skills/competitive-market-research/SKILL.md)

---

## Install

### Install in Claude Code (one command)

```
/plugin marketplace add lingegrace/claude-research-skills
/plugin install research-skills@lingegrace-research-skills
```

That's it. Claude picks the right skill automatically when your request matches, or you can call one by name: *"use competitive-market-research to build a battlecard for …"*.

### Manual install (Claude Code)

```bash
git clone https://github.com/lingegrace/claude-research-skills.git
mkdir -p ~/.claude/skills
cp -R claude-research-skills/skills/* ~/.claude/skills/
```

Restart Claude Code. To install only one skill, copy just that folder. To share skills with your team, copy them into the project's `.claude/skills/` instead.

### Install in Claude.ai or the Claude desktop app

1. Download a zip: [research-analyst.zip](dist/research-analyst.zip) · [sociology-deep-research.zip](dist/sociology-deep-research.zip) · [competitive-market-research.zip](dist/competitive-market-research.zip)
2. Open **Settings → Capabilities → Skills**, click **Upload skill**, and pick the zip.
3. Turn the skill on and try an example prompt below.

Custom skills need a Claude plan with Skills enabled.

---

## Example prompts

```text
Here are three articles on AI adoption in UK marketing teams [paste or attach].
Build a research brief I can use for a LinkedIn post. English, plus a Chinese summary.
```

```text
Does platform gig work reshape class identity among young urban workers in China?
I want a source-traceable literature synthesis.
```

```text
Should we match Competitor X's seat-based pricing for the mid-market segment in H1?
Build a PROFILE-mode competitive dossier.
```

```text
Make a sales battlecard for us vs. Competitor Y in enterprise HR software.
```

---

## Compare the three skills

| | research-analyst | sociology-deep-research | competitive-market-research |
|---|---|---|---|
| Best for | Creators, writers, analysts | Students, researchers, policy analysts | PMM, product, sales, strategy |
| Checks in with you | Only if something is unclear | Yes, after scoping | Yes, stakeholder checkpoint |
| Output | Research Brief (Markdown) | Dossier + CSV ledgers | Dossier or battlecard + CSV ledgers |
| Bias check | Claim classification | Adversarial critique | Mirror battlecard + sponsor-bias check |
| Grading | Strong / Moderate / Limited | Synthesis / Interpretation / Hypothesis | FACT / READ / BET · ACT / WATCH / RESEARCH-MORE |

---

## FAQ

**What is a Claude Skill?**
A folder with a `SKILL.md` file. Claude loads its instructions when a task matches its description. Skills work in Claude Code, Claude.ai, the desktop app and the Claude API. See Anthropic's [Agent Skills docs](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview).

**Do these skills browse the web?**
No. A skill doesn't add web access. If your Claude environment has web search, the skills use it. If not, paste the text or upload the PDFs, and the skill will say clearly which sources it could not open.

**Can I use them for academic work?**
Yes. `sociology-deep-research` is built for literature reviews and source-traceable analysis. Still check key citations against the originals: the skill reports "audited for the checks listed", never "hallucination-free".

**Do they work with other models or agents?**
`SKILL.md` is plain Markdown. Any agent that supports the Agent Skills format can load it, and you can paste the instructions into any LLM as a system prompt.

**Are they free?**
Yes, under the MIT license.

---

## Repository layout

```
.claude-plugin/marketplace.json     # Claude Code plugin marketplace manifest
skills/
  research-analyst/                 # SKILL.md + references/ (template, output contract, evals)
  sociology-deep-research/          # SKILL.md
  competitive-market-research/      # SKILL.md
dist/                               # upload-ready zips for Claude.ai
```

## Contributing

Issues and PRs are welcome, especially new evaluation cases, worked examples and translations. If you edit a `SKILL.md`, rebuild its zip:

```bash
cd skills && zip -r ../dist/<skill-name>.zip <skill-name> -x '*/README.md'
```

⭐ **If these skills help you, please star the repo** so other people can find it.

## Author

Built by **Linge (Grace) Guo**, a sociologist (UCL, Oxford MSc) working on AI companions, AI deception and platform governance. [Website](https://lingegrace.github.io/work-from-home-/) · [LinkedIn newsletter](https://www.linkedin.com/build-relation/newsletter-follow?entityUrn=7422191016994217984)

License: [MIT](LICENSE)

---

## 中文说明

**三个免费开源的 Claude Skill（`SKILL.md`），让 Claude 变成一个靠谱的研究助理：结论都有出处，事实和观点分开写，绝不编造数据或引用。** 支持 Claude Code、Claude.ai 和 Claude 桌面版。

- 🔎 **research-analyst**（AI 研究助理 / 资料整理）：把文章、行业报告、新闻整理成可追溯的研究简报，写 LinkedIn、公众号、Newsletter 之前先把事实核对清楚。
- 🎓 **sociology-deep-research**（AI 文献综述 / 社会学研究）：产出带引用核查的研究档案，包括论点-证据表、论证图和反方挑战，适合写论文、做文献综述和政策分析。
- 📊 **competitive-market-research**（AI 竞品分析 / 市场调研）：为 B2B 产品市场（PMM）和战略团队做竞品画像、销售 battlecard、市场格局、定价拆解和输赢单分析。

### 安装

**Claude Code（一行命令）：**

```
/plugin marketplace add lingegrace/claude-research-skills
/plugin install research-skills@lingegrace-research-skills
```

**手动安装：** `git clone` 本仓库后，把 `skills/` 下的文件夹复制到 `~/.claude/skills/`，再重启 Claude Code。

**Claude.ai / 桌面版：** 从 [`dist/`](dist/) 下载对应的 zip，在 **设置 → Capabilities → Skills** 里上传，再打开开关。

### 常见问题

- **会联网吗？** Skill 本身不提供联网能力。打不开的链接，请直接粘贴原文或上传 PDF。
- **能用来写论文吗？** 可以，但发布前请把关键引用再和原文核对一遍。
- **免费吗？** 免费，MIT 开源协议。

觉得好用的话，欢迎点个 ⭐ Star，让更多人看到。
