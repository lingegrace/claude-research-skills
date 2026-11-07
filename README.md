# Claude Skills for Product Managers, Product Marketing & Research

[![Claude Skills](https://img.shields.io/badge/Claude-Agent%20Skills-D97757)](https://github.com/lingegrace/claude-research-skills)
[![Skills](https://img.shields.io/badge/skills-15-blue)](#all-skills)
[![Claude Code plugin](https://img.shields.io/badge/Claude%20Code-plugin-222)](#install)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**15 free, open-source [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) (`SKILL.md`) for the human side of product work and research:** value propositions (features → benefits, FAB), positioning and messaging, personas and Jobs-to-be-Done, voice-of-customer review mining, feature launch kits, customer case studies, AI product audits, competitor analysis, deep research, literature reviews, thematic analysis, survey analysis and fact-checking.

Most popular Claude skills help you **write code**. These help with the work around the code: understanding the customer, explaining the value, launching, and researching the evidence.

Every skill works the same way:
1. **Starts from what you already have** (a PRD, reviews, transcripts, a draft, a dataset).
2. **Asks you to clarify** your goal, the document you need, your audience and their pain points before it writes anything.
3. **Works in fixed steps** and fills in a fixed output template.
4. **Never invents** numbers, quotes, customers or citations. Anything unproven is labeled.

They work in **Claude Code**, **Claude.ai**, the **Claude desktop app**, and any agent that loads Agent Skills.

🌐 **Browse the catalog, read the lessons on writing skills, and see what's coming: [Grace's Skill Library](https://lingegrace.github.io/skills/)**

[中文说明 ↓](#中文说明)

---

## All skills

### 📦 Product & Marketing: for PMs, PMMs, founders and sales

| Skill | You give it | You get back |
|---|---|---|
| [`value-proposition-writer`](skills/product-marketing/value-proposition-writer/) | PRD, spec, feature list, landing page | **Value proposition** built from a **Feature–Advantage–Benefit (FAB)** matrix per audience, value proposition, the finished PRD value section or one-pager |
| [`positioning-messaging`](skills/product-marketing/positioning-messaging/) | Product docs, FAB, personas, competitor notes | **Positioning statement**, **messaging house**, taglines, homepage heroes, elevator pitches |
| [`user-persona-builder`](skills/product-marketing/user-persona-builder/) | Interview notes, surveys, reviews, CRM notes | Evidence-based **personas** and **Jobs-to-be-Done (JTBD)** / ICP |
| [`customer-review-mining`](skills/product-marketing/customer-review-mining/) | G2 / App Store / Reddit reviews, NPS, tickets | Ranked **voice-of-customer** pain points, outcomes and objections, with quotes |
| [`competitive-market-research`](skills/product-marketing/competitive-market-research/) | A business question about competitors | **Competitor analysis**, **battlecards**, market landscape, pricing teardown, win-loss |
| [`feature-launch-kit`](skills/product-marketing/feature-launch-kit/) | PRD, changelog, release notes | **Launch / GTM kit**: release notes, announcement, sales one-pager, FAQ, social posts |
| [`customer-case-study`](skills/product-marketing/customer-case-study/) | Customer interview transcript, CSM notes | **Case study**, sales-slide and social versions, quote-approval list |
| [`ai-product-audit`](skills/product-marketing/ai-product-audit/) | Screenshots, flows, spec of an AI feature | **AI trust & risk audit**: transparency, dark patterns, privacy, safety, EU AI Act pointers |

**How they connect:** `customer-review-mining` + `user-persona-builder` → `value-proposition-writer` → `positioning-messaging` → `feature-launch-kit` → `customer-case-study`. `competitive-market-research` feeds the Advantage column of FAB.

### 🎓 Sociology & Social Science Research: for students, researchers and UX researchers

| Skill | You give it | You get back |
|---|---|---|
| [`research-question-grill`](skills/sociology/research-question-grill/) | A vague topic | A focused, answerable **research question** brief, built one question at a time |
| [`sociology-deep-research`](skills/sociology/sociology-deep-research/) | A social science question | A source-traceable **deep research** dossier / **literature review** with claim–evidence tables |
| [`interview-guide`](skills/sociology/interview-guide/) | Research question, participants | A bias-checked **semi-structured interview guide** with probes and consent points |
| [`thematic-analysis`](skills/sociology/thematic-analysis/) | Interview transcripts, open-ended answers | **Braun & Clarke thematic analysis**: codebook, themes with exact quotes, write-up |
| [`quantitative-analysis`](skills/sociology/quantitative-analysis/) | A dataset + research question | **Survey / regression analysis** with assumption checks and honest interpretation |

**How they connect:** `research-question-grill` → `sociology-deep-research` (literature) → `interview-guide` → `thematic-analysis` and/or `quantitative-analysis` → `fact-check-draft`.

### 🔎 Research & Writing: for anyone who writes from sources

| Skill | You give it | You get back |
|---|---|---|
| [`content-research-analyst`](skills/research/content-research-analyst/) | Articles, reports, news | A **source-traceable research brief** for a post, newsletter or report |
| [`fact-check-draft`](skills/research/fact-check-draft/) | A finished draft + its sources | **Claim-by-claim fact-check** (supported / overclaim / wrong / no source) and a corrected draft |

---

## Install

### Claude Code

Add the marketplace once:

```
/plugin marketplace add lingegrace/claude-research-skills
```

Then install everything, or one section:

```
/plugin install research-skills@lingegrace-research-skills              # all 15 skills
/plugin install product-marketing-skills@lingegrace-research-skills     # 8 product & marketing skills
/plugin install sociology-research-skills@lingegrace-research-skills    # 5 sociology skills
/plugin install research-writing-skills@lingegrace-research-skills      # 2 research & writing skills
```

Claude picks the right skill when your request matches, or you can call one by name: *"use value-proposition-writer on this PRD"*.

### Manual install

```bash
git clone https://github.com/lingegrace/claude-research-skills.git
mkdir -p ~/.claude/skills
cp -R claude-research-skills/skills/*/* ~/.claude/skills/
```

### Claude.ai or the Claude desktop app

Download the skill's zip from [`dist/`](dist/), go to **Settings → Capabilities → Skills → Upload skill**, and turn it on.

---

## Example prompts

```text
Here's our PRD for the new AI quiz generator [attach]. Write the product value section with FAB for L&D managers and for subject-matter experts.
```
```text
Here are 300 G2 reviews of us and Competitor X [attach]. What are the top pain points, in customers' own words?
```
```text
We ship SSO for the Team plan on March 3 [changelog attached]. Make the launch kit.
```
```text
I want to research how AI companions affect loneliness. Grill me until I have a real research question.
```
```text
Here are 14 interview transcripts [attach]. Run a Braun & Clarke thematic analysis, inductive.
```
```text
Fact-check this LinkedIn article against these three sources before I post it.
```

---

## FAQ

**Who are these skills for?**
Product managers, product marketing managers, founders, sales enablement, UX researchers, social science students and researchers, and writers who work from sources.

**How is this different from other Claude skills?**
Most top skills focus on coding (TDD, code review, frontend design). These cover the "human and content" side of product and research work, and each one asks about your goal, audience and existing material before producing anything.

**Do these skills browse the web?**
A skill doesn't add web access. If your Claude environment has web search (for example for competitor research in `value-proposition-writer`), the skills use it and cite what they read. Otherwise, give them your files.

**Do they work with Codex, Cursor or other agents?**
`SKILL.md` is plain Markdown. Any agent that supports the Agent Skills format can load it.

**Are they free?**
Yes, MIT license.

---

## Repository layout

```
.claude-plugin/marketplace.json     # Claude Code marketplace: 1 all-in-one + 3 section plugins
skills/
  product-marketing/                # 8 skills
  sociology/                        # 5 skills
  research/                         # 2 skills
dist/                               # one upload-ready zip per skill, for Claude.ai
```

## Contributing

Issues and PRs are welcome, especially worked examples and new evaluation cases. If you edit a `SKILL.md`, rebuild its zip:

```bash
cd skills/<section> && zip -r ../../dist/<skill-name>.zip <skill-name> -x '*/README.md'
```

⭐ **If these skills help you, please star the repo** so other people can find it.

## Author

Built by **Linge (Grace) Guo**, a sociologist (UCL, Oxford MSc) working at the intersection of AI, products and society. [Skill Library](https://lingegrace.github.io/skills/) · [Website](https://lingegrace.github.io/work-from-home-/) · [Newsletter: Signals Across Markets](https://www.linkedin.com/newsletters/7422191016994217984/)

License: [MIT](LICENSE)

---

## 中文说明

**15 个免费开源的 Claude Skill，专门做产品工作和研究里"人与内容"的那一面。** 产品价值（FAB）、定位与文案、用户画像与 JTBD、用户评论挖掘、功能上线物料、客户案例、AI 产品审查、竞品分析、深度研究、文献综述、主题分析、问卷/定量分析、稿件事实核查，都能做。

现在最火的 Claude Skill 大多是写代码的。这一套补的是代码之外的工作：理解用户、讲清价值、发布上线、用证据做研究。

每个 Skill 的工作方式都一样：
1. 先从你手上已有的材料出发，比如 PRD、评论、访谈稿、草稿、数据。
2. 先跟你确认目标、要交付什么文档、受众是谁、他们的痛点是什么。
3. 按固定步骤做，输出固定的模板。
4. 绝不编造数据、引用或客户，没有证据的地方都会标出来。

**三个栏目：**
- 📦 **产品与市场**（8 个）：`value-proposition-writer`（价值主张 / 功能→优势→好处 FAB）· `positioning-messaging`（定位与文案）· `user-persona-builder`（用户画像 / JTBD）· `customer-review-mining`（评论挖掘）· `competitive-market-research`（竞品分析）· `feature-launch-kit`（上线物料）· `customer-case-study`（客户案例）· `ai-product-audit`（AI 产品审查）
- 🎓 **社会学研究**（5 个）：`research-question-grill`（研究问题追问）· `sociology-deep-research`（深度研究 / 文献综述）· `interview-guide`（访谈提纲）· `thematic-analysis`（Braun & Clarke 主题分析）· `quantitative-analysis`（定量 / 问卷分析）
- 🔎 **研究与写作**（2 个）：`content-research-analyst`（资料研究简报）· `fact-check-draft`（稿件事实核查）

**安装（Claude Code）：**

```
/plugin marketplace add lingegrace/claude-research-skills
/plugin install research-skills@lingegrace-research-skills
```

只装某一个栏目：把 `research-skills` 换成 `product-marketing-skills`、`sociology-research-skills` 或 `research-writing-skills`。

**Claude.ai / 桌面版：** 从 [`dist/`](dist/) 下载对应的 zip，在 **设置 → Capabilities → Skills** 里上传。

觉得好用的话，欢迎点个 ⭐ Star。
