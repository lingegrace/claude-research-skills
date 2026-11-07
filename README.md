# Claude Research Skills: Deep Research, Literature Review & Competitor Analysis for Claude Code

[![Claude Skills](https://img.shields.io/badge/Claude-Agent%20Skills-D97757)](https://github.com/lingegrace/claude-research-skills)
[![Claude Code plugin](https://img.shields.io/badge/Claude%20Code-plugin-222)](#install)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**Three free, open-source [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) (`SKILL.md`) for evidence-based research.** Every claim is linked to a source, facts are kept apart from interpretation, and the skills never make up statistics or citations. They work in **Claude Code**, **Claude.ai**, the **Claude desktop app**, and any agent that loads Agent Skills.

> Looking for a **deep research skill**, a **literature review skill**, or a **market research / competitor analysis skill** for Claude? This repo has one of each, each built for a different job.

[中文说明 ↓](#中文说明)

---

## Which skill do I need?

| If you want to… | Use | In one line |
|---|---|---|
| **Research and fact-check sources before writing** a post, newsletter, blog or report | 🔎 [`research-analyst`](skills/research-analyst/) | General-purpose **AI research assistant**: articles, reports and news in, a **citation-backed research brief** out |
| **Do a literature review on a social question** (sociology, social science, AI & society, policy) | 🎓 [`sociology-deep-research`](skills/sociology-deep-research/) | **Academic deep research** for the social sciences: a **systematic-style literature review** with claim–evidence tables and an argument map |
| **Analyze competitors or a market** (B2B, SaaS, product marketing, sales) | 📊 [`competitive-market-research`](skills/competitive-market-research/) | **Competitive intelligence**: competitor profiles, **battlecards**, market landscape maps, pricing teardowns and **win-loss analysis** |

**How they differ:**

- **`research-analyst` is the general one.** It is fast and works with whatever sources you paste in or upload. It is made for creators and analysts who need to know what the sources actually say.
- **`sociology-deep-research` is the academic one.** It builds a full dossier, stops for your approval of the research direction, separates descriptive, associational and causal claims, and runs an adversarial critique of its own argument. It is made for students, researchers and policy analysts.
- **`competitive-market-research` is the business one.** It grades every source by trust tier (T1 SEC filings and pricing pages → T5 vendor marketing) and writes a "mirror battlecard" (your competitor's view of *you*) to catch wishful thinking. Every recommendation is labeled ACT, WATCH or RESEARCH-MORE. It is made for PMM, product, sales and strategy teams.

---

## Why not just ask an AI to "do deep research"?

Generic deep-research prompts often return confident reports with **hallucinated citations**, invented numbers, and correlation presented as causation. These skills add checks at every step:

| Common problem | What these skills do |
|---|---|
| Fake sources, DOIs, quotes and statistics | **Never invent**: a missing field is marked `Not provided` / `Not verified` |
| "The source exists" taken to mean "the source proves it" | **Two separate checks**: is the source real (`VERIFIED`), and does it actually support the claim (`DIRECT` / `PARTIAL` / `NO_SUPPORT`)? |
| Correlation reported as causation | Each claim type (descriptive, associational, causal, mechanism) needs matching evidence |
| One press release copied by 12 outlets counted as 12 sources | **Study / signal clusters** count independent evidence, not URLs |
| The AI researches the wrong question | **Human-in-the-loop checkpoint** after scoping, before the deep dive |
| Confirmation bias, or telling the boss what they want to hear | **Adversarial critique** and a **mirror battlecard** pass |
| An old article treated as current news | Publication date, event date and data period are recorded separately |

---

## The skills in detail

### 🔎 `research-analyst`: AI research assistant and research brief generator

**Best for:** content creators, newsletter writers, analysts and consultants. Use it for summarizing and **fact-checking** web articles, industry reports, market research and news, and for turning several sources into one **source-traceable research brief**.

**Output (8 sections):** executive summary · source register · claim–evidence table with claim IDs and source locators · cross-source synthesis and conflicts · creator-ready insights, each with the "overclaim to avoid" · research gaps · content handoff · source notes.

**Extras:** English-first with an optional Chinese or bilingual summary; ignores **prompt injection** hidden in source documents; says plainly when a URL couldn't be opened instead of pretending it read it.

→ [SKILL.md](skills/research-analyst/SKILL.md) · [input template](skills/research-analyst/references/input-template.md) · [eval cases](skills/research-analyst/references/evaluation-cases.md)

### 🎓 `sociology-deep-research`: literature review and social science deep research

**Best for:** sociology and social science students, academic researchers, policy analysts and journalists. Use it for **literature reviews**, **research synthesis**, evidence maps and **auditing a report** for unsupported claims, on topics such as inequality, platforms and the gig economy, gender, digital media, and AI and society.

**Output:** research brief · search log · `sources.csv` · `claims.csv` · `evidence.csv` · `arguments.csv` · adversarial critique · insights graded *evidence-supported synthesis / plausible interpretation / new hypothesis* · 10-point scorecard · readiness gate.

**Modes:** `SCOPING` (quick brief) · `SYNTHESIS` (full deep-research dossier, the default) · `PROTOCOL` (a research plan) · `AUDIT` (check an existing report).

→ [SKILL.md](skills/sociology-deep-research/SKILL.md)

### 📊 `competitive-market-research`: competitor analysis, battlecards and market research

**Best for:** product marketing managers (PMM), product managers, sales enablement, strategy and founders. Use it for **competitor analysis**, **sales battlecards**, **competitive landscape** maps, **SaaS pricing and packaging teardowns**, **feature-parity analysis** and **win-loss analysis**.

**Output:** a decision-focused brief · sources graded **T1–T5** · signal-cluster accounting · claim–evidence tables · **mirror battlecard** · findings graded **FACT / READ / BET** · implications graded **ACT / WATCH / RESEARCH-MORE**, with tripwires.

**Modes:** `SCOUT` (one-pager) · `PROFILE` (deep competitor profile, the default) · `BATTLECARD` · `LANDSCAPE` (5–12 player market map) · `WIN-LOSS`.

→ [SKILL.md](skills/competitive-market-research/SKILL.md)

---

## Install

### Claude Code (one command)

```
/plugin marketplace add lingegrace/claude-research-skills
/plugin install research-skills@lingegrace-research-skills
```

Claude picks the right skill automatically when your request matches, or you can call one by name: *"use competitive-market-research to build a battlecard for …"*.

### Manual install (Claude Code)

```bash
git clone https://github.com/lingegrace/claude-research-skills.git
mkdir -p ~/.claude/skills
cp -R claude-research-skills/skills/* ~/.claude/skills/
```

Restart Claude Code. To install one skill, copy only its folder. To share skills with a team, copy them into the project's `.claude/skills/` instead.

### Claude.ai or the Claude desktop app

1. Download a zip: [research-analyst.zip](dist/research-analyst.zip) · [sociology-deep-research.zip](dist/sociology-deep-research.zip) · [competitive-market-research.zip](dist/competitive-market-research.zip)
2. Go to **Settings → Capabilities → Skills → Upload skill** and pick the zip.
3. Turn the skill on and try an example prompt below.

---

## Example prompts

**Content research** (`research-analyst`)
```text
Here are three articles on AI adoption in UK marketing teams [paste or attach].
Build a research brief I can use for a LinkedIn post. English, plus a Chinese summary.
```

**Literature review** (`sociology-deep-research`)
```text
Does platform gig work reshape class identity among young urban workers in China?
I want a source-traceable literature review.
```
```text
Audit this report on social media and teen anxiety [attach]. Which central claims are actually supported?
```

**Competitor analysis** (`competitive-market-research`)
```text
Should we match Competitor X's seat-based pricing for the mid-market segment in H1?
```
```text
Build a sales battlecard for us vs. Competitor Y in enterprise HR software.
```
```text
Map the AI meeting-notes market: 8 players, who is going upmarket, who is going PLG.
```

---

## Compare at a glance

| | research-analyst | sociology-deep-research | competitive-market-research |
|---|---|---|---|
| Category | General research / fact-checking | Academic deep research / literature review | Market research / competitive intelligence |
| Best for | Creators, writers, analysts | Students, researchers, policy analysts | PMM, product, sales, strategy |
| Checks in with you | Only if something is unclear | Yes, after scoping | Yes, stakeholder checkpoint |
| Output | Research brief (Markdown) | Dossier + CSV ledgers | Dossier or battlecard + CSV ledgers |
| Bias check | Claim classification | Adversarial critique | Mirror battlecard + sponsor-bias check |
| Grading | Strong / Moderate / Limited | Synthesis / Interpretation / Hypothesis | FACT / READ / BET · ACT / WATCH / RESEARCH-MORE |

---

## FAQ

**What is a Claude Skill?**
A folder with a `SKILL.md` file. Claude loads its instructions when a task matches its description. Skills work in Claude Code, Claude.ai, the desktop app and the Claude API. See Anthropic's [Agent Skills docs](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview).

**Is this a deep research skill?**
Yes. `sociology-deep-research` is a full deep-research workflow (scope, check in, retrieve, verify, critique, synthesize) for social science questions. `competitive-market-research` applies the same discipline to markets and competitors.

**Can I use it for a systematic literature review?**
`sociology-deep-research` follows a systematic-review-style protocol: a logged search, inclusion rules, screening decisions, and study-cluster deduplication. It is not a substitute for a registered PRISMA systematic review.

**Do these skills browse the web?**
A skill doesn't add web access. If your Claude environment has web search, the skills use it. If not, paste the text or upload the PDFs, and the skill will say which sources it could not open.

**Do they work with Codex, Cursor or other agents?**
`SKILL.md` is plain Markdown. Any agent that supports the Agent Skills format can load it, and you can paste the instructions into any LLM as a system prompt.

**Are they free?**
Yes, under the MIT license.

---

## Repository layout

```
.claude-plugin/marketplace.json     # Claude Code plugin marketplace manifest
skills/
  research-analyst/                 # SKILL.md + references/ (input template, output contract, eval cases)
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

Built by **Linge (Grace) Guo**, a sociologist (UCL, Oxford MSc) working on AI companions, AI deception and platform governance. [Website](https://lingegrace.github.io/work-from-home-/) · [Newsletter: Signals Across Markets](https://www.linkedin.com/newsletters/7422191016994217984/)

License: [MIT](LICENSE)

---

## 中文说明

**三个免费开源的 Claude Skill（`SKILL.md`），用来做有据可查的研究：每条结论都标出处，事实和观点分开写，不编造数据或引用。** 支持 Claude Code、Claude.ai、Claude 桌面版，以及其他支持 Agent Skills 的 AI agent。

**我该用哪个？**

| 你想做什么 | 用哪个 | 一句话 |
|---|---|---|
| 写文章、公众号、Newsletter 之前，先**整理资料、核对事实** | 🔎 `research-analyst` | 通用 **AI 研究助理**：输入文章、报告、新闻，输出每条都带出处的研究简报 |
| 围绕一个社会议题写**文献综述** | 🎓 `sociology-deep-research` | 社会科学方向的**学术 deep research**：系统性文献综述、论点-证据表、论证图、反方挑战 |
| 做**竞品分析 / 市场调研**（B2B、SaaS、产品市场） | 📊 `competitive-market-research` | **竞品情报**：竞品画像、销售 battlecard、市场格局、定价拆解、输赢单复盘 |

**三者的区别：** `research-analyst` 最通用、最快，你给什么资料就整理什么；`sociology-deep-research` 是学术型的，会先请你确认研究方向，严格区分描述、相关和因果；`competitive-market-research` 是商业型的，来源分 T1–T5 五级可信度，还会用"镜像 battlecard"从竞争对手的角度反查自己有没有一厢情愿。

### 安装

**Claude Code（一行命令）：**

```
/plugin marketplace add lingegrace/claude-research-skills
/plugin install research-skills@lingegrace-research-skills
```

**手动安装：** `git clone` 本仓库后，把 `skills/` 下的文件夹复制到 `~/.claude/skills/`，再重启 Claude Code。

**Claude.ai / 桌面版：** 从 [`dist/`](dist/) 下载对应的 zip，在 **设置 → Capabilities → Skills** 里上传。

### 常见问题

- **会联网吗？** Skill 本身不提供联网能力。打不开的链接，请直接粘贴原文或上传 PDF。
- **能用来写论文、做文献综述吗？** 可以，但发布前请把关键引用再和原文核对一遍。
- **免费吗？** 免费，MIT 开源协议。

觉得好用的话，欢迎点个 ⭐ Star，让更多人看到。
