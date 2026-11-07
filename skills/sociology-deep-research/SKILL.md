---
name: sociology-deep-research
description: Produces a source- and claim-traceable sociological research dossier from a natural-language prompt. Verifies source identity separately from claim support, runs an adversarial critique pass, and holds a mandatory human-direction checkpoint after scoping. Use when the user asks for a sociological research dossier, literature review on a social topic, or a source-traceable analysis of a social phenomenon. Not for a quick opinion, a non-empirical essay, or a single-source summary.
---

# Sociology Deep Research

*A Skill for doing sociology, not for summarizing it.*

## 1. Contract

Three obligations, scored separately — a formally complete report can still be a bad argument:

1. **Research behavior** — disclose assumptions; separate observation / source-author interpretation / this report's inference / speculation; leave room for human judgment.
2. **Evidence reliability** — verify source identity and claim support as separate checks; record overlap, access level, dates, methods.
3. **Research quality** — frame a sociologically meaningful, feasible question; treat literature as a debate; align method to question; test mechanisms, alternatives, counterevidence.

**Stage states** (used everywhere): `PASS` done to standard · `PARTIAL` progress with limits · `BLOCKED` unresolved issue stops progress · `NOT TESTED` check not performed. Every non-`PASS` needs one line of reason. Never silently upgrade.

**Never invent** sources, DOIs, quotations, page numbers, sample/effect sizes, methods, search counts, access, human decisions, or audit outcomes. "Audited for the checks listed" ≠ "hallucination-free".

## 2. Workflow

```
   prompt
     │
     ▼
┌─── A: Brief ──────────────┐  Gate A: scope explicit
│                           │
     ▼
┌─── B: Scoping scan ───────┐  Gate B: search universe + limits documented
│  (first-pass search +     │
│   candidate questions)    │
     ▼
┌─── H: Human checkpoint ───┐  Gate H: direction approved OR autonomy authorized
│   (300–600 word brief,    │
│    2–4 directions)        │
     ▼
┌─── C: Full retrieval ─────┐  sources.csv built
│                           │
     ▼
┌─── D: Evidence / claims ──┐  Gate D: each central claim ↔ inspected evidence
│   (claims.csv,            │
│    evidence.csv)          │
     ▼
┌─── E: Arguments + critique ┐ Gate E: premises → warrant → conclusion traced,
│   (arguments.csv,          │        alternatives tested, adversarial pass done
│    adversarial pass)       │
     ▼
┌─── F: Synthesis + grading ─┐ Insights graded: SYNTHESIS / INTERPRETATION / HYPOTHESIS
│                            │
     ▼
   Final dossier + scorecard + gate dashboard
```

## 3. Modes and scaling

Pick a mode once; it decides which products are required.

| Mode | Trigger | Required products |
|------|---------|-------------------|
| `SCOPING` | brief map of a topic, ≤500-word brief requested | A, B, H, truncated F; `sources.csv` optional; no `evidence.csv` |
| `SYNTHESIS` (default) | literature synthesis, dossier, "deep research" | A–F all stages, all tables |
| `PROTOCOL` | user wants a plan to execute later | A, B, H, plus a written protocol doc; no C–F |
| `AUDIT` | user supplies an existing report to check | D + E only, run against the given document |

Default `SYNTHESIS`. Downshift to `SCOPING` if the user asks for something quick, a summary, or a short brief — do not bulldoze a small request with 13 artifacts. Upshift only on explicit ask.

## 4. Stage A — Brief

Produce `research_brief.md`: original prompt verbatim; mode; main question + 2–4 subquestions; population/case/geography/period/unit of analysis/core concepts; inclusion rules; constraints; assumptions (labeled); risks of a predetermined answer.

Question must be empirically answerable, sociologically meaningful, and open to findings that could weaken the user's initial view. A topic is not a question. Structural issues reduced to individual psychology without justification is a question-bias flag.

## 5. Stage B — Search protocol + literature map

Maintain `search_log.csv`: id, datetime, service, exact query, filters, period, language, result count (only if observed), screening status. Unknown counts stay unknown — don't estimate.

Sociology source tiers, preferred order: Scopus / Web of Science / Sociological Abstracts / JSTOR / SocArXiv for peer-reviewed; OpenAlex / Semantic Scholar / Crossref for metadata and OA; government and administrative data for descriptive claims; quality journalism only for recency and provenance, never as the sole support for a causal claim.

Map literature as a conversation — traditions, convergences, genuine disagreements, silences — not author-by-author summaries. Do not infer "no one has studied this" from a narrow search; say "sources identified by this search leave X underexplored".

## 6. Stage H — Human checkpoint (mandatory unless autonomy is explicitly authorized)

After Stage B, deliver a 300–600 word decision brief: TL;DR of what the scan tentatively suggests and does not establish; candidate question; landscape; two or more competing explanations; coverage gaps; uncertainties that could materially change the result; recommended direction with trade-offs; decision request.

Offer 2–4 real directions (keep / narrow / broaden / prioritize a theory / prioritize a mechanism / exclude a source type). Pause. Record the user's choice (or the authorized autonomous default) in `human_decisions.csv` with options shown, choice, rationale, date.

If running autonomously and in doubt, pick the recommended direction and log it; do not pretend the user answered.

## 7. Stage C — Retrieval + source ledger

For each included source, one row in `sources.csv`:

`source_id, title, author(s), year, venue, DOI, URL, source_type, data_period, population/case, design/method, sample/data, key_measures, main_finding, limitations, relevance, access_level, identity_status, identity_verified_on, study_cluster_id, screening_decision, screening_reason`

Record what the study *actually* studied — do not substitute "social media" for TikTok-specific, adults for adolescents, exposure proxy for platform use, symptoms for diagnoses, cross-sectional association for change-over-time.

**Identity states**: `VERIFIED` (reliable record confirms metadata) · `PARTLY_VERIFIED` (record exists, material details unresolved) · `UNVERIFIED` (not checked) · `CONTRADICTED_LIKELY_FABRICATED` (reliable conflicting records). One failed search is not enough to call fabrication.

**Study clusters**: multiple reviews often summarize the same underlying study; multiple URLs often repeat one press release. Assign a shared `study_cluster_id` when records likely reuse the same data. Report both source count and cluster count whenever that distinction matters.

## 8. Stage D — Evidence and claim verification

Two tables, linked by id.

`claims.csv`: `claim_id, text, type (descriptive/associational/causal/mechanism/historical/theoretical), scope, importance (CENTRAL/MAJOR/MINOR), support_status, confidence, open_issues`

`evidence.csv`: `evidence_id, source_id, claim_id, role (SUPPORT/COUNTER/CONTEXT/THEORY/METHOD_QUALITY), inspected_location (page/section/table/figure/dataset variable), paraphrase_or_short_quote, what_it_supports, what_it_does_not_support, population/time/method/measure, support_verdict, reviewer, review_date, study_cluster_id, overlap_note`

**Support states**: `DIRECT` (inspected material supports exact claim at stated scope/strength) · `PARTIAL` (supports a narrower version) · `CONTRADICTS` · `NO_SUPPORT` · `NOT_TESTED`. `VERIFIED` identity never implies `DIRECT` support.

**Claim type ↔ what can support it**:

| Claim type | What the evidence must show |
|------------|------------------------------|
| Descriptive | accurate measure + clearly defined population, period, denominator |
| Associational | estimate + uncertainty + measurement/population caveats |
| Causal | identification strategy addressing temporality, confounding, selection, reverse causality; cross-sectional r alone is not enough |
| Mechanism | evidence of the process itself, not just an association; mark observed vs inferred |
| Historical | provenance, source criticism, competing accounts |
| Theoretical | accurate attribution; separate the theorist's proposition from this report's application |

For every central claim, answer both: "what is the strongest version this evidence supports?" and "what tempting stronger version is not supported?"

Do not force every finding to have three sources. Sparse evidence narrows the conclusion; it does not justify padding.

## 9. Stage E — Argument map + adversarial pass

`arguments.csv`: `argument_id, claim_ids, conclusion, premises, evidence_ids, warrant, inference_type (desc/assoc/temporal/causal/mech/analogy/normative), assumptions, alternatives, boundary_conditions, strongest_counterargument, likely_gap, falsifier, confidence`

Run on every major argument: premise support · inferential fit · causal discipline (temporality, reverse causality, selection, confounding, measurement) · alternatives tested not just named · counterevidence engaged not strawmanned · scope drift · concept discipline · normative drift (fact → value jump).

Write a short adversarial critique per central finding: strongest skeptic's objection, whether it is decisive, what would answer it. A mechanism you cannot explain in plain language is not yet an adequate mechanism.

## 10. Stage F — Synthesis

Look for patterns across methods and contexts; disagreements explained by population / measurement / design / period; mechanisms backed by multiple evidence kinds; evidence that challenges your initial frame; boundary conditions; meaningful absences.

Grade every proposed insight:

- `EVIDENCE-SUPPORTED SYNTHESIS` — follows from the comparisons recorded
- `PLAUSIBLE INTERPRETATION` — consistent with evidence but under-determined
- `NEW HYPOTHESIS` — a conjecture the dossier does not test

Reflexivity: how positionality, institutional setting, theoretical commitments, access, or funding shape question and interpretation. Not boilerplate confession.

## 11. Worked mini-example (SYNTHESIS mode)

Topic: *"Does TikTok use raise adolescent anxiety?"*

**A — brief (excerpt)**  
Question: Is adolescent TikTok use (daily minutes, 2020–2025) causally associated with increased clinical anxiety symptoms vs other short-video platforms? Mode: `SYNTHESIS`. Population: 13–18, US + East Asia. Assumption (labeled): "anxiety" = GAD-7 or clinical dx, not self-reported "feeling anxious".

**B — search_log row**  
`B04, 2026-10-30T09:11+08, Scopus, "TikTok" AND ("anxiety" OR "GAD") AND adolescen*, 2019–2025, EN, n=146, screening=in_progress`

**H — direction chosen**  
"Narrow to longitudinal + quasi-experimental designs; keep East Asia comparison" (user authorized autonomy; rationale: cross-sectional literature already saturated; causal question demands temporality).

**C — source row (one)**  
`S014, "Short-video use and adolescent anxiety: a 2-wave panel", Chen et al., 2024, J Adolesc Health, 10.xxxx, ..., FULL_TEXT, VERIFIED, 2026-10-30, cluster=K03, included, "longitudinal, GAD-7, n=2,418"`

**D — claim + evidence**  
`C002: "Daily TikTok use >90 min at T1 predicts clinically meaningful GAD-7 increase at T2 among East-Asian adolescents" — type=associational-temporal, importance=CENTRAL`  
`E017: source=S014, role=SUPPORT, location=Table 3, β=0.14 (95% CI 0.06–0.22), supports: association + temporal order; does_not_support: causal claim (no exogenous shock, residual confounding by baseline depression), support_verdict=PARTIAL`

**E — argument**  
`A05: premises=C002 + two convergent panel studies in cluster K03; warrant=temporal order + replication across two national samples narrows reverse-causality but does not eliminate confounding; alternative=unmeasured family stress; falsifier=an IV / natural-experiment study showing null effect; confidence=moderate-for-association, low-for-causation`

**F — graded insight**  
`EVIDENCE-SUPPORTED SYNTHESIS: TikTok use at high intensity is prospectively associated with modest anxiety increases in East-Asian adolescents.`  
`PLAUSIBLE INTERPRETATION: the association is mediated by sleep displacement rather than content per se.`  
`NEW HYPOTHESIS: platform-switching (TikTok ↔ Douyin) exposure changes mediate cross-national differences.`

Reuse this shape; do not copy its content.

## 12. Final dossier

One document plus the companion CSVs. Sections: TL;DR · question + scope + search protocol · literature synthesis · evidence inventory (link to `sources.csv`) · claim–evidence matrix (link to `claims.csv`, `evidence.csv`) · argument map + critique (link to `arguments.csv`) · synthesis + graded insights · limitations + reflexivity · source audit + reproducibility appendix.

Size the dossier to the question. A section that does not apply is marked `NOT APPLICABLE` with a reason, not silently dropped.

## 13. Scorecard + readiness gate

Score 1–5 with concrete evidence, not an average: (1) question significance + feasibility · (2) literature synthesis + gap · (3) method/question fit · (4) evidence coverage + independence · (5) source identity + claim–source alignment · (6) causal inference + claim calibration · (7) mechanisms, alternatives, counterarguments · (8) reflexivity · (9) argument coherence + traceability · (10) synthesis + insight quality.

**Critical fail → status `PROVISIONAL — NOT VALIDATED`** if any of: unresolved fabricated/contradicted central citation · central claim marked verified while `NO_SUPPORT` or `NOT_TESTED` · causal claim without a defensible identification review · counterevidence suppressed · an audit claimed as performed when it was not · conclusion untraceable through evidence + argument records · required human checkpoint skipped without authorization.

Otherwise use `AUDITED FOR THE CHECKS LISTED`, never "hallucination-free".

## 14. Scripts (status: not shipped with this skill)

This skill does not currently include executable audit scripts. If a Python runtime is available, the agent may write a minimal `verify_citations.py` that resolves DOIs via Crossref and flags unresolved entries — treat its result as an identity check only, never as claim support. Do not report that a script ran if it did not. If the user wants the scripts bundled, say so and build them as a follow-up.

## 15. Final response summary

Close with: what is supported now (with inference strength) · what remains uncertain · gate dashboard · evidence audit (sources + claims checked, access level, unresolved mismatches, cluster overlap) · argument audit (chain, alternatives, weaknesses) · scorecard profile and any critical fail · decision log · deliverable filenames.

The test: after the chat ends, the researcher can explain what the evidence does and does not establish, and can trace how this report arrived at its conclusions.

## Changelog

- **v2 (2026-10-30)** — Compressed from v1 (~360 → ~230 lines). Added: ASCII workflow, mode-scaling table, claim-type × support table, worked TikTok mini-example, source-tier guidance for sociology, honest "scripts not shipped" status, pushier description with Use-when / Not-for. Removed: duplicated final-dossier spec, redundant state redefinitions, promise of unshipped `scripts/` folder.
- **v1** — Initial release.
