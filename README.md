# Research Skills for Claude

**Evidence-first research skills for Claude.** Each one produces work you can trace back to its sources, keeps "what the source says" apart from "what we infer", and stops to check in with you before going deep.

[中文说明 ↓](#中文说明)

| Skill | What it does | Use it when you want… |
|---|---|---|
| [`research-analyst`](skills/research-analyst/SKILL.md) | Turns articles, reports and news into a traceable **Research Brief**: source register, claim table, conflicts, creator-ready insights and a content handoff. | to research sources before writing a post, newsletter or article |
| [`sociology-deep-research`](skills/sociology-deep-research/SKILL.md) | Builds a **sociological research dossier**: scoping, a human checkpoint, source and claim ledgers, an argument map, an adversarial critique and graded insights. | a literature review or deep, source-traceable analysis of a social phenomenon |
| [`competitive-market-research`](skills/competitive-market-research/SKILL.md) | Builds **B2B competitive intelligence**: source tiers T1–T5, signal clusters, a "mirror battlecard" bias check and FACT / READ / BET grading. | a competitor profile, battlecard, market landscape, pricing teardown or win-loss read |

All three share the same rules: **never invent sources, numbers or quotes**, check that a source exists separately from checking that it supports the claim, and say plainly what the evidence does *not* establish.

---

## Install

### Option A — Claude Code (recommended)

Inside Claude Code, add this repo as a plugin marketplace and install:

```
/plugin marketplace add lingegrace/research-skills
/plugin install research-skills@lingegrace-research-skills
```

All three skills are then available. Claude picks one automatically when your request matches, or you can ask for it by name (e.g. *"use sociology-deep-research on …"*).

### Option B — Copy into your skills folder (Claude Code)

```bash
git clone https://github.com/lingegrace/research-skills.git
mkdir -p ~/.claude/skills
cp -R research-skills/skills/* ~/.claude/skills/
```

Restart Claude Code. To install only one skill, copy only that folder.

### Option C — Claude.ai or the Claude desktop app

1. Download the zip for the skill you want from [`dist/`](dist/):
   [`research-analyst.zip`](dist/research-analyst.zip) ·
   [`sociology-deep-research.zip`](dist/sociology-deep-research.zip) ·
   [`competitive-market-research.zip`](dist/competitive-market-research.zip)
2. In Claude, open **Settings → Capabilities → Skills** (wording may vary), click **Upload skill**, and pick the zip.
3. Turn the skill on and try one of the example prompts below.

Custom skills need a plan where Skills are enabled.

---

## Example prompts

**research-analyst**
> Here are three articles on AI adoption in UK marketing teams [paste or attach]. Build me a research brief I can use for a LinkedIn post. English, plus a Chinese summary.

**sociology-deep-research**
> Does platform gig work weaken or reshape class identity among young urban workers in China? I want a source-traceable literature synthesis.

**competitive-market-research**
> Should we match Competitor X's seat-based pricing for the mid-market segment in H1? Build a PROFILE-mode dossier.

---

## What you get

| | research-analyst | sociology-deep-research | competitive-market-research |
|---|---|---|---|
| Stops to check in with you | Only if something is unclear | Yes, after scoping (Stage H) | Yes, stakeholder checkpoint (Stage H) |
| Modes | — | `SCOPING` · `SYNTHESIS` · `PROTOCOL` · `AUDIT` | `SCOUT` · `PROFILE` · `BATTLECARD` · `LANDSCAPE` · `WIN-LOSS` |
| Main output | Markdown Research Brief (8 sections) | Dossier + `sources/claims/evidence/arguments.csv` | Dossier or battlecard + the same CSV ledgers |
| Bias check | Claim classification | Adversarial critique pass | Mirror battlecard + sponsor-bias check |
| Insight grading | Strong / Moderate / Limited | SYNTHESIS / INTERPRETATION / HYPOTHESIS | FACT / READ / BET + ACT / WATCH / RESEARCH-MORE |

## Limitations

- A skill does not give Claude web access. If a URL can't be opened in your environment, paste the text or upload the PDF.
- "Audited for the checks listed" is not the same as "error-free". Check important claims against the original sources before you publish.
- No executable audit scripts are bundled yet (see section 14 of each deep-research skill).

## Repository layout

```
.claude-plugin/marketplace.json   # Claude Code plugin marketplace manifest
skills/
  research-analyst/
    SKILL.md
    references/                   # input template, output contract, eval cases
  sociology-deep-research/SKILL.md
  competitive-market-research/SKILL.md
dist/                             # upload-ready zips for Claude.ai
```

## Contributing

Issues and pull requests are welcome, especially new evaluation cases or worked examples. If you change a `SKILL.md`, rebuild its zip:

```bash
cd skills && zip -r ../dist/<skill-name>.zip <skill-name>
```

## License

[MIT](LICENSE) © 2026 Linge (Grace) Guo · [Website](https://lingegrace.github.io/work-from-home-/)

---

## 中文说明

**为 Claude 打造的「证据优先」研究类 Skill。** 每个结论都能追溯到来源；"来源说了什么"和"我们推断了什么"分开写；深入研究之前，会先停下来跟你确认方向。

| Skill | 作用 | 适用场景 |
|---|---|---|
| `research-analyst` | 把文章、报告、新闻整理成可追溯的研究简报（来源登记、论点表、冲突对比、创作者洞察、内容交接）。 | 写帖子、Newsletter、文章之前先把资料研究清楚 |
| `sociology-deep-research` | 社会学研究档案：先划定范围，再请你确认方向，之后建来源和论点台账、画论证图，做一轮反方挑战，最后给洞察分级。 | 社会议题的文献综述，或需要每条结论都有出处的深度分析 |
| `competitive-market-research` | B2B 竞品情报：来源分 T1–T5 五级，同源信号归为一簇，用"镜像 battlecard"检查偏见，结论按 FACT / READ / BET 分级。 | 竞品画像、battlecard、市场格局、定价拆解、输赢单复盘 |

### 安装

**Claude Code（推荐）：**

```
/plugin marketplace add lingegrace/research-skills
/plugin install research-skills@lingegrace-research-skills
```

**手动复制：** `git clone` 本仓库后，把 `skills/` 里的文件夹复制到 `~/.claude/skills/`，然后重启 Claude Code。

**Claude.ai / 桌面版：** 从 [`dist/`](dist/) 下载对应的 zip，在 **设置 → Capabilities → Skills** 里上传，再打开开关即可。

### 注意

- Skill 本身不提供联网能力。打不开的链接，请直接粘贴原文或上传 PDF。
- 发布前，请把重要论点再和原始来源核对一遍。
