---
name: research-question-grill
description: A one-question-at-a-time interview that turns a vague research topic into a focused, answerable research question with scope, concepts, method fit and a falsifier. Use when a student, researcher or analyst says "I want to research X", is starting a thesis, dissertation, paper or literature review, or needs a research question before running sociology-deep-research.
---

# Research Question Grill

A topic is not a question. This skill interviews the user, one question at a time, until "I'm interested in AI and loneliness" becomes a question someone could actually answer, and that could turn out to be wrong.

## How to work

Ask **one question per message**. Wait for the answer. Push back when an answer is vague ("young people" → which ages, where?). Stop asking once each item below is settled.

1. **The puzzle.** What do you want to explain or understand, and why does it matter? What surprised you? Done when there's a puzzle, not just a topic.
2. **The unit and scope.** Who or what is studied (people, organizations, platforms, countries, texts)? Where, and over what period? Done when population, place and time are concrete.
3. **The concepts.** What are the 2–3 key concepts, and how would you observe each one? ("Loneliness" measured how? By a scale, by self-description, by behavior?) Done when each concept has a working definition.
4. **The type of question.** Descriptive (what is happening?), explanatory (why?), comparative (how do A and B differ?), or interpretive (what does it mean to people?). Done when the user agrees which type it is.
5. **The falsifier.** What finding would prove your current hunch wrong? If nothing could, the question is too loose. Done when at least one finding could weaken the user's expectation.
6. **Feasibility.** What data or access do you have, and what time and skills? Does the method fit the question type? Done when there's a realistic route to an answer.

Then write the brief.

## Output template

```markdown
# Research question brief

**Main question:** <one sentence, ending in a question mark>
**Sub-questions:** 1. … 2. … 3. …
**Question type:** descriptive / explanatory / comparative / interpretive
**Unit · place · period:** ...
**Key concepts and how they're observed:** ...
**Current expectation (hunch):** ...
**What would prove it wrong:** ...
**Likely method and data:** ...
**Risks:** <predetermined answer, data access, scope too big>
**Next step:** e.g. run sociology-deep-research in SCOPING mode on this brief
```

## Rules

- One question per message. Don't send a list of questions.
- Don't answer the research question yourself; your job is to sharpen it.
- Flag questions that reduce a structural problem to individual psychology, and ask whether that's intended.
