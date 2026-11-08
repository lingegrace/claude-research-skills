# Claude Skills for Research, Writing & Everyday Work

[![Claude Skills](https://img.shields.io/badge/Claude-Agent%20Skills-D97757)](https://lingegrace.github.io/skills/)
[![Skills](https://img.shields.io/badge/free%20skills-67-blue)](#all-skills)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**67 free, open-source [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) (`SKILL.md`) for students and professionals:** deep research, literature reviews, market and competitor research, fact-checking, writing in your own voice, executive writing, meeting notes to action items, decision memos, SOPs, tutoring and exam practice (IELTS, interviews, CVs), customer research, positioning, SEO, landing pages, PRDs, product discovery, and tools to write and test your own skills.

> **AI is good at output. Input is the work.** These skills don't automate jobs. They package the work inside them: the questions to ask first, a named method to follow, and evidence for every claim.

🌐 **Browse the catalog, search in your own words, and learn to write skills: [Grace's Skill Library](https://lingegrace.github.io/skills/)**

Every skill works the same way:
1. **Starts from what you already have:** a PRD, transcripts, a draft, a dataset, reviews, lecture notes.
2. **Asks before it writes:** your goal, the output you need and your audience, each with a sensible default.
3. **Follows a named method in fixed steps:** for example Braun & Clarke, the Minto Pyramid, retrieval practice or the Opportunity Solution Tree. Each step says when it's done, and the output follows a fixed template.
4. **Never invents** numbers, quotes, citations or customers. Anything unproven is labeled.

They work in **Claude Code**, **Claude.ai**, the **Claude desktop app**, and any agent that loads Agent Skills.

[中文说明 ↓](#中文说明)

---

## Install

**Claude Code:** add the library once, then install everything or one folder:

```
/plugin marketplace add lingegrace/claude-research-skills
/plugin install research-skills@lingegrace-research-skills     # all 67 skills
```

Each section below shows the command for installing just that folder.

**Manual install:**

```bash
git clone https://github.com/lingegrace/claude-research-skills.git
mkdir -p ~/.claude/skills
cp -R claude-research-skills/skills/*/* ~/.claude/skills/
```

**Claude.ai or the desktop app:** download the skill's zip from [`dist/`](dist/), then go to **Settings → Capabilities → Skills → Upload skill**.

---

## All skills

### 🎓 Social Science Research

Research questions, literature reviews, interviews, thematic and quantitative analysis. · Install: `/plugin install social-science-research-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`interview-guide`](skills/social-science/interview-guide/) | Qualitative interview guide | A research question or brief, participant details, interview length | An interview guide with consent script, warm-up, themed questions and probes, closing, interviewer notes, and bias-check changes |
| [`literature-review`](skills/social-science/literature-review/) | Literature review and synthesis matrix | A research question plus PDFs, reading notes or a reading list, or permission to search | Screening log with inclusion and exclusion criteria, literature matrix, synthesis organised by debate, research gap and a draft literature review section with traceable citations |
| [`quantitative-analysis`](skills/social-science/quantitative-analysis/) | Survey & quantitative analysis | A dataset (CSV, Excel, SPSS, Stata) plus a research question | Cleaning log, descriptives, model results with CIs, assumption checks, plain-language interpretation, limitations and code |
| [`research-question-grill`](skills/social-science/research-question-grill/) | Research question interview | A topic or rough idea | A research question brief: main and sub-questions, scope, concepts, falsifier, method fit, ready for sociology-deep-research |
| [`sociology-deep-research`](skills/social-science/sociology-deep-research/) | Sociology deep research & literature review | A social science research question | A source-traceable research dossier: brief, search log, source/claim/evidence/argument ledgers, adversarial critique, graded insights, scorecard |
| [`survey-design`](skills/social-science/survey-design/) | Survey and questionnaire design | A research or business question, who you want to survey, and your constraints (length, channel) | A questionnaire with sections, exact wording, response scales and skip logic, a list of bias fixes, a pilot checklist and an analysis plan mapping every question to the research question |
| [`thematic-analysis`](skills/social-science/thematic-analysis/) | Thematic analysis (Braun & Clarke) | Interview transcripts, focus groups, open-ended survey answers, field notes | Codebook, thematic map, defined themes with exact quotes, methods paragraph, reflexivity note and audit trail |

### 📈 Market Research

Deep research, market sizing, competitors, trends and topics, with sources you can check. · Install: `/plugin install market-research-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`competitor-analysis`](skills/market-research/competitor-analysis/) | Competitor analysis & sales battlecards | A business question about competitors (pricing, positioning, win-loss) | A competitor profile or battlecard with tiered sources, a mirror battlecard, FACT/READ/BET findings and ACT/WATCH/RESEARCH-MORE implications |
| [`deep-research`](skills/market-research/deep-research/) | Cited research report on any question | A business, policy or general question, plus any starting sources you already have | A research report with a short answer up front, findings per sub-question, a claim–evidence table, confidence ratings, counterevidence, open questions, a source list and what couldn't be accessed |
| [`market-research`](skills/market-research/market-research/) | Market sizing and market analysis brief | A market or product category, the decision you face (enter, price, which segment), and any reports or data you have | Market definition and segments, top-down and bottom-up TAM/SAM/SOM with every assumption shown, PESTEL drivers, Five Forces, key players, implications and what to validate next |
| [`topic-discovery`](skills/market-research/topic-discovery/) | Content ideas and research topics, ranked | Your niche or field, your audience, and any newsletters, reports, competitor content, comments or search data you have | 10–20 ranked topics, each with the audience question, evidence of demand or gap, angle and difficulty, plus a question bank |
| [`trend-research`](skills/market-research/trend-research/) | Trend analysis and horizon scanning report | A domain, a time horizon, and any news, reports, data or observations you have | Trend report with signals, trends and drivers, each with evidence, maturity, Three Horizons placement and implications, plus a watch-list of tripwires and a signal log |

### ✍️ Writing, Editing & Social Media

Research briefs, fact-checks, your own voice, LinkedIn, newsletters and academic writing. · Install: `/plugin install writing-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`abstract-writer`](skills/writing/abstract-writer/) | Abstract writer for papers and theses | Paper draft, thesis or its sections, the word limit and the journal or university guidelines | Structured and unstructured abstract versions with word counts, move map, keywords, one-sentence plain-language summary, gaps |
| [`academic-editing`](skills/writing/academic-editing/) | Academic English editing for theses and papers | Thesis chapter, paper draft or essay paragraphs, plus the target journal or degree level and citation style | Edited text, change log by category (clarity, concision, hedging, signposting, grammar), recurring error patterns, argument flow comments |
| [`citation-formatter`](skills/writing/citation-formatter/) | Reference list formatter and citation checker | A messy reference list, in-text citations or the full manuscript, and the target style | Formatted reference list, in-text citation cross-check, list of entries with missing information, summary of changes |
| [`content-research-analyst`](skills/writing/content-research-analyst/) | Content research & fact-checking | Articles, industry reports, news, PDFs or pasted text you've collected | An 8-section research brief: source register, claim–evidence table, conflicts, creator insights, gaps and a content handoff |
| [`copy-editor`](skills/writing/copy-editor/) | Copy edit with a change log | A near-final draft and, optionally, a house style guide or AP, Chicago or APA | A clean copy, a change log (before, after, reason), a style sheet of decisions, and author queries |
| [`ethics-application`](skills/writing/ethics-application/) | Research ethics application and consent form drafts | Your study plan or proposal, and your institution's ethics form or guidance if you have it | Draft answers for each ethics section, risk and mitigation table, participant information sheet, consent form, open issues |
| [`executive-writing`](skills/writing/executive-writing/) | Executive summary and BLUF emails | Meeting notes, a long status update, an analysis, or an email thread | An executive email or update with the bottom line, explicit ask and three supporting points, plus one-paragraph and one-line versions |
| [`fact-check-draft`](skills/writing/fact-check-draft/) | Fact-check a draft | A finished draft (article, post, report, PRD, copy) plus its sources | Claim-by-claim verdicts with source locations, suggested fixes, and a corrected draft |
| [`human-writing`](skills/writing/human-writing/) | Make AI text sound human | A draft email, essay, post, report or bio that sounds generic or machine-written | A rewrite that sounds like a person, a change log with the pattern behind each edit, and claims flagged as needing a source |
| [`interview-to-article`](skills/writing/interview-to-article/) | Turn interview transcripts into articles | An interview transcript (expert, customer, founder) and what the article is for | A feature article or Q&A, headline options, a quote-approval list with transcript locations, and open questions for the interviewee |
| [`linkedin-writer`](skills/writing/linkedin-writer/) | Write LinkedIn posts from notes | An idea, meeting or reading notes, an article, a research brief, and your goal (reach, authority, leads) | Three post options with different hooks, a suggested first comment for each, a fact check, and questions for real stats or stories |
| [`long-form-editor`](skills/writing/long-form-editor/) | Edit essays, articles and reports | A long draft: essay, article, report, thesis chapter, white paper | A reverse outline, a prioritised change list by editing level, a style sheet and the edited version |
| [`methods-section-writer`](skills/writing/methods-section-writer/) | Methods section and methodology chapter writer | Notes on participants, sampling, instruments, procedure, analysis and ethics; your target journal or degree | Methods section draft by subsection, the reporting guideline that applies, a reporting checklist with missing items |
| [`my-writing-voice`](skills/writing/my-writing-voice/) | Write in your own voice | Your past emails, posts, essays or articles, or brand-voice samples your team owns, plus the text you need written | A saved voice guide (features, do and don't rules, examples), a draft in that voice, and a match check |
| [`newsletter-writer`](skills/writing/newsletter-writer/) | Write a newsletter issue from research | A research brief, notes or links, your audience, and past issues for voice | Subject line options, a complete issue (opening, sections, takeaway, sign-off), a teaser post and a source log |
| [`peer-review-response`](skills/writing/peer-review-response/) | Response to reviewers letter writer | Reviewer reports, editor's decision letter, examiner comments, your manuscript or revised draft | Point-by-point response letter, cover note to the editor, list of points needing your decision, revision checklist |
| [`thesis-chapter-review`](skills/writing/thesis-chapter-review/) | Thesis and dissertation chapter feedback | A thesis or dissertation chapter draft, and your marking criteria or rubric if you have it | Scores per criterion with evidence, strengths, top 5 priority fixes, paragraph-level comments, next-draft plan |

### 🗂 Meetings, Memos & Reports

Meeting actions, decision memos, weekly reports, document reviews and SOPs. · Install: `/plugin install work-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`decision-memo`](skills/work/decision-memo/) | Decision memo with options and recommendation | Research, analysis, meeting notes, a Slack debate, data on a decision | A decision memo: context, the decision needed, options with pros/cons/risks, recommendation, what would change it, next steps and an evidence log |
| [`document-review`](skills/work/document-review/) | Review a draft document before sending | A work document (proposal, report, plan, policy, deck text) plus what it's for and who reads it | Prioritised comments (blocking / important / nice-to-have) on purpose fit, structure, evidence, clarity, risks and missing pieces, a claims check and a suggested revised outline |
| [`meeting-to-actions`](skills/work/meeting-to-actions/) | Meeting notes to action items | Meeting transcript, recording notes, Teams/Slack/Zoom chat log, your own scribbled notes | A 5-minute summary: decisions, action items (owner, due date, done-definition), open questions, risks, and optionally a decision memo |
| [`sop-builder`](skills/work/sop-builder/) | Write an SOP from process notes | A description, screen-recording transcript, Loom notes, or rough notes of how a process is done | A standard operating procedure (purpose, scope, roles, SIPOC, steps with owners and checks, common mistakes, open questions) plus a one-page checklist |
| [`weekly-report`](skills/work/weekly-report/) | Weekly status report for your manager | Task lists, notes, tickets, commits, chat messages, calendar from the week | A weekly report (bottom line, progress, plans, problems and asks, metrics if provided) plus a 3-line version for chat |

### 📚 Learning & Exam Prep

Tutors, active recall, IELTS, study plans, interview practice and CV reviews. · Install: `/plugin install learning-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`active-recall`](skills/learning/active-recall/) | Flashcards and self-quiz from your notes | Lecture notes, slides, a textbook chapter, a syllabus section | Question sets across Bloom's levels, flashcards with sources, a graded quiz session, and a Leitner review schedule |
| [`book-tutor`](skills/learning/book-tutor/) | Chapter-by-chapter book study guide | Book chapters, excerpts or your reading notes, and your reading goal | Per chapter: key ideas, connections, check and discussion questions, application prompts, a one-page summary, and a review queue |
| [`ielts-speaking-partner`](skills/learning/ielts-speaking-partner/) | IELTS speaking mock test with feedback | Your target band, exam date and topic areas; your spoken (transcribed) or typed answers | A Part 1, 2 and 3 mock test with a cue card, estimated bands per criterion with evidence, useful language, a model answer outline, and next practice |
| [`ielts-writing-coach`](skills/learning/ielts-writing-coach/) | IELTS writing feedback and band estimate | Your IELTS Writing Task 1 or Task 2 response, the question, and your target band | Estimated band per criterion with quotes from your essay, task coverage check, top 3 fixes, an improved version, and targeted practice |
| [`interview-practice`](skills/learning/interview-practice/) | Mock interview with STAR feedback | Target role and company, the job description, your CV, and the interview type (behavioural, case, PM, group interview) | A competency map, a mock interview one question at a time, feedback per answer, model answer outlines from your real experience, and a prep list |
| [`knowledge-gap-detector`](skills/learning/knowledge-gap-detector/) | Find your weak spots before the exam | A topic, syllabus or exam spec, and your sense of what you've already studied | Sub-topic and prerequisite map, diagnostic results with evidence, a solid / shaky / missing gap map, and an ordered study list |
| [`mistake-analysis`](skills/learning/mistake-analysis/) | Mistake notebook and error analysis | Wrong answers from homework, tests or past papers (any subject), with correct answers and marks if you have them | An error log with each mistake's cause, the patterns that cost you most, targeted practice, and a retest set |
| [`paper-tutor`](skills/learning/paper-tutor/) | Understand an academic paper, step by step | An academic paper (PDF or text) and your background in the field | Argument map, section-by-section explanations, key terms, check questions, and reading notes (claim, method, findings, limits) with section or page references |
| [`resume-review`](skills/learning/resume-review/) | Resume review against a job description | Your CV or resume and the job description you're applying for | A JD keyword and skill match, impact rating for each bullet, structure and ATS readability fixes, rewritten bullets, and questions for missing metrics |
| [`socratic-tutor`](skills/learning/socratic-tutor/) | Learn any topic by Socratic questioning | A topic or concept you want to understand, and what you already know about it | A tutoring session, one question at a time, with misconceptions corrected through questions and a short summary at the end |
| [`study-plan-builder`](skills/learning/study-plan-builder/) | Exam revision plan and study timetable | Exam or goal, exam date, syllabus and materials, hours available per week, current level | A knowledge framework of the syllabus, a week-by-week plan with daily tasks, spaced review slots, mock-test checkpoints, and a progress tracker |
| [`transfer-practice`](skills/learning/transfer-practice/) | Apply what you learned to new problems | A concept, formula, framework or skill you've studied, and where you need to use it | A worked example, a faded practice sequence from near to far transfer, feedback on each attempt, and review problems |

### 📣 Marketing

Customer research, positioning, SEO, landing pages, launches and case studies. · Install: `/plugin install marketing-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`competitor-messaging`](skills/marketing/competitor-messaging/) | Competitor messaging analysis and white space | Competitor homepages, landing pages or ads (URLs or pasted copy) and your own homepage or positioning | Claims by company with exact quotes and sources, a messaging matrix, overlap and white space, and 3 differentiated messaging angles |
| [`content-repurposing`](skills/marketing/content-repurposing/) | Repurpose content across channels | One source piece (article, report, webinar transcript, newsletter, podcast notes) and the channels you post on | The key message, a version per channel, and a message integrity check table confirming each keeps the core claim, audience and CTA |
| [`customer-case-study`](skills/marketing/customer-case-study/) | Customer case study writer | Customer interview transcript, call notes, CSM or CRM notes, usage metrics | Publishable case study, sales slide and social versions, an approval list, and optional anonymization (it always asks whether to hide the company and identifying details) |
| [`customer-review-mining`](skills/marketing/customer-review-mining/) | Voice of customer from reviews | Review exports or pasted reviews, NPS comments, support tickets, survey open-ends | Ranked pain points with counts and quotes, outcomes, objections, alternatives named, and what it means for roadmap and messaging |
| [`feature-launch-kit`](skills/marketing/feature-launch-kit/) | Feature launch & GTM kit | PRD, spec, Jira epic, changelog, release notes | Fact sheet plus every launch piece for the launch tier: release notes, in-app message, announcement, sales one-pager, FAQ, internal email, social posts |
| [`landing-page-writer`](skills/marketing/landing-page-writer/) | Landing page copy that converts | Product info or brief, who the page is for, the offer, and any value proposition, positioning, reviews or case studies | Hero headline, subhead and CTA, problem, solution, benefits, proof, objections/FAQ, final CTA, and 3 headline variants with test hypotheses |
| [`positioning-messaging`](skills/marketing/positioning-messaging/) | Positioning & messaging framework | PRD, FAB analysis, personas, competitor research, win/loss notes, customer quotes | Positioning canvas and statement, messaging house with proof points, taglines, homepage heroes and pitches |
| [`seo-research`](skills/marketing/seo-research/) | SEO keyword research and keyword map | Your product or topic, the audience and market, and optionally Ahrefs, Semrush or Google Search Console exports and your existing URLs | Keyword clusters tagged by search intent and funnel stage (TOFU/MOFU/BOFU), priorities with reasons, a page plan and cannibalisation risks |
| [`value-proposition-writer`](skills/marketing/value-proposition-writer/) | Value proposition writer — features to benefits (FAB) | PRD, product spec, feature list, landing page, pitch deck | FAB matrix per audience, value proposition, gaps to fix, and optionally the finished PRD value section or one-pager |

### 🧭 Product Management

Discovery, PRDs, specs, critiques, personas and AI product audits. · Install: `/plugin install product-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`ai-product-audit`](skills/product/ai-product-audit/) | AI product trust & risk audit | Screenshots, user flows, demo access, spec, system prompt or policies | Ranked risk table with evidence and fixes, area-by-area ratings, quick wins, and items for legal review |
| [`feature-spec`](skills/product/feature-spec/) | User stories and acceptance criteria | An approved PRD, a feature description, design notes | User stories with Given/When/Then acceptance criteria, edge cases, empty/loading/error states, analytics events, dependencies, rollout plan and open questions |
| [`prd-writer`](skills/product/prd-writer/) | Product requirements document (PRD) writer | A feature idea, user feedback, interview notes, research notes, support tickets | A PRD: problem statement, target users and JTBD, goals and non-goals, success metrics, must/should/could requirements, user flow, risks and open questions |
| [`product-critique`](skills/product/product-critique/) | Product teardown and UX heuristic review | A product, feature, prototype, screen recording or screenshots, plus the target user and goal | A structured critique: JTBD fit, usability issues by Nielsen's 10 heuristics, value clarity, friction points ranked by severity, and the top 3 concrete fixes |
| [`product-discovery`](skills/product/product-discovery/) | Opportunity solution tree and assumption tests | A desired outcome (e.g. increase activation) plus data, interview notes, feedback, support tickets | An opportunity solution tree (outcome → opportunities → solutions → assumption tests), an assumption map (desirability, viability, feasibility, usability) and the next 3 cheapest experiments |
| [`user-persona-builder`](skills/product/user-persona-builder/) | Personas & Jobs-to-be-Done | Interview notes, survey data, reviews, CRM or sales notes, support tickets | 2–4 persona cards with JTBD, pains, triggers and buying criteria, a comparison table, and what to validate next |

### 🛠 Build Your Own Skills

Write, review, test and orchestrate your own skills. · Install: `/plugin install skill-engineering-skills@lingegrace-research-skills`

| Skill | What it is | Input | Output |
|---|---|---|---|
| [`agent-orchestrator`](skills/skill-engineering/agent-orchestrator/) | Plan a multi-agent AI workflow | A multi-step goal, the files or data you have, and where it will run (Claude Code sub-agents, a workflow tool, by hand) | Sub-tasks with a parallel run order, handoff contracts, human review checkpoints, failure handling and a ready-to-paste brief per sub-agent |
| [`prompt-to-skill`](skills/skill-engineering/prompt-to-skill/) | Turn a saved prompt into a skill | A prompt you reuse (from a notes app, a prompt library, custom instructions), and optionally an output you liked | A SKILL.md with trigger, steps, output template and rules, one-off details turned into clarifying questions, a before/after and a change log |
| [`skill-creator`](skills/skill-engineering/skill-creator/) | Write your own Claude skill | A description of a job you repeat, plus real examples of what you start from and what you hand in | A complete SKILL.md draft (name, description, steps with done-conditions, output template, rules), a README and a test plan |
| [`skill-eval`](skills/skill-engineering/skill-eval/) | Test and evaluate a Claude skill | A SKILL.md and 2–5 real tasks it should handle, with what good output looks like | Normal, edge and adversarial test cases (including prompt injection), frozen criteria, a run log, graded results and fixes to try |
| [`skill-reviewer`](skills/skill-engineering/skill-reviewer/) | Review and fix a Claude skill | A SKILL.md you wrote or installed, and optionally examples of runs that went wrong | A scorecard on 9 criteria with quoted evidence, a YAML frontmatter check, a prioritised fix list and a revised SKILL.md |
| [`workflow-decomposer`](skills/skill-engineering/workflow-decomposer/) | Find where AI fits in your work | A role or a recurring task (e.g. monthly marketing report, customer interview programme), plus any templates, past examples or checklists | A task hierarchy, each stage's input, output and done-condition, AI fit per stage (AI skill, AI + review, human) and a skill map with a build order |

---

## Pro workflows

The free skills each do one job. **Pro skills** run a whole workflow end to end, with checkpoints for your approval: research → article, a LinkedIn content system, content strategy, marketing research, PM research, an SEO content system, a knowledge base builder, and a skill eval system. Custom skills built around your team's process are also available. See **[Pro](https://lingegrace.github.io/skills/pro/)**.

## FAQ

**Who are these skills for?** Students (especially in social science, media and education) and people at work in marketing, product, content, research, consulting and operations.

**Do they browse the web?** A skill doesn't add web access. If your Claude setup has web search, the skills use it and cite what they read. Otherwise, give them your files.

**What does the MIT license mean?** Anyone can use, copy, change and share these skills, including commercially, as long as the copyright notice stays in the files.

**Do they work with other agents?** `SKILL.md` is plain Markdown. Any agent that supports the Agent Skills format can load it.

## Contributing

Issues and PRs are welcome, especially worked examples and new test cases. If you edit a `SKILL.md`, rebuild its zip: `cd skills/<section> && zip -r ../../dist/<skill>.zip <skill> -x '*/README.md'`.

⭐ **If these skills help you, please star the repo** so other people can find them.

## Author

Built by **Linge (Grace) Guo**, a sociologist (UCL, Oxford MSc) working on AI, work and society. [Skill Library](https://lingegrace.github.io/skills/) · [Personal site](https://lingegrace.github.io/work-from-home-/) · [Newsletter: Signals Across Markets](https://www.linkedin.com/newsletters/7422191016994217984/)

License: [MIT](LICENSE)

---

## 中文说明

**67 个免费开源的 Claude Skill，给学生和职场人用**：深度研究、文献综述、市场和竞品研究、事实核查、用你自己的文风写作、给领导写汇报、会议纪要和行动项、决策备忘录、SOP、学习辅导和备考（雅思、面试、简历）、用户研究、定位、SEO、落地页、PRD、产品探索，还有帮你自己写 skill、测 skill 的工具。

> **AI 擅长产出，但真正的工作在输入。** 这些 skill 不是替你自动化工作，而是把工作里的方法打包好：先问哪些问题、按哪种成熟的方法做、每个结论都要有证据。

**安装（Claude Code）：**

```
/plugin marketplace add lingegrace/claude-research-skills
/plugin install research-skills@lingegrace-research-skills
```

可以用中文搜索、按分类浏览：**[Grace's Skill Library](https://lingegrace.github.io/skills/)**。觉得好用的话，欢迎点个 ⭐ Star。
