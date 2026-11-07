---
name: competitor-analysis
description: Produces a source- and claim-traceable competitive / market research dossier from a natural-language prompt, built for B2B product, PMM, and strategy teams. Separates competitor fact from competitor claim from analyst spin, triangulates by source tier, runs an adversarial "mirror battlecard" pass, and holds a mandatory stakeholder checkpoint after scoping. Use when the user asks for a competitor profile, battlecard, market landscape, win-loss diagnostic, pricing / packaging teardown, or feature-parity analysis. Not for a quick opinion, a one-source summary, or consumer-brand sentiment work.
---

# Competitor Analysis

*A Skill for doing competitive intelligence, not for repeating vendor marketing.*

## 1. Contract

Three obligations, scored separately — a slick deck can still be a bad read of the market:

1. **CI behavior** — disclose assumptions and sponsor bias; separate observed fact / competitor's own claim / analyst interpretation / this report's inference / speculation; leave room for stakeholder judgment on strategic calls.
2. **Evidence reliability** — verify source identity *and* claim support as separate checks; record source tier, independence (one PR echoed by 12 outlets = 1 signal), access level, and date (prices and headcount move).
3. **Research quality** — frame a business-decision-useful question; treat the landscape as a set of competing bets, not vendor summaries; align evidence to the specific claim type; test alternative explanations before concluding "they won because X".

**Stage states**: `PASS` done to standard · `PARTIAL` progress with limits · `BLOCKED` unresolved issue stops progress · `NOT TESTED` check not performed. Every non-`PASS` needs one line of reason. Never silently upgrade.

**Never invent** pricing, headcount, ARR, logos, review counts, feature availability, roadmap, win-rate deltas, or quotes. "Audited for the checks listed" ≠ "the market works the way we said".

## 2. Workflow

```
   prompt (business question)
     │
     ▼
┌─── A: Brief ────────────────┐  Gate A: decision + stakeholder + competitor set explicit
│                             │
     ▼
┌─── B: Scan + landscape ─────┐  Gate B: source universe + tiering + search limits recorded
│                             │
     ▼
┌─── H: Stakeholder checkpoint ┐ Gate H: direction + depth + confidentiality rules confirmed
│   (300–500 word brief,      │
│    2–4 directions)          │
     ▼
┌─── C: Retrieval + ledger ───┐  sources.csv with tier + independence
│                             │
     ▼
┌─── D: Evidence / claims ────┐  Gate D: each central claim ↔ inspected, tier-appropriate evidence
│   (claims.csv,              │
│    evidence.csv)            │
     ▼
┌─── E: Arguments + mirror ───┐  Gate E: inference chain traced, alternatives tested,
│   (arguments.csv,           │        "mirror battlecard" adversarial pass done
│    adversarial pass)        │
     ▼
┌─── F: Synthesis + implications ┐ Insights graded: FACT / READ / BET;
│                                │ implications graded: ACT / WATCH / RESEARCH-MORE
     ▼
   Final deliverable (mode-shaped) + scorecard + gate dashboard
```

## 3. Modes and scaling

Pick a mode once; it decides the deliverable shape and which products are required.

| Mode | Trigger | Required products |
|------|---------|-------------------|
| `SCOUT` | 1-pager on a single competitor, ≤500 words | A, B, H, truncated F; `sources.csv` optional |
| `PROFILE` (default) | deep competitor profile / teardown | A–F all stages, all tables |
| `BATTLECARD` | sales-facing operational doc | A–E, then a 1–2 page battlecard section replaces F prose |
| `LANDSCAPE` | 5–12 player market map | A, B, H, condensed C–D per player, F with positioning map |
| `WIN-LOSS` | why we lose/win vs X | A, B, H, D + E only, built on supplied win-loss call notes |

Default `PROFILE`. Downshift to `SCOUT` for quick asks. Do not bulldoze a 1-pager request with a 12-section dossier.

## 4. Stage A — Brief

Produce `research_brief.md`: original prompt verbatim; mode; **decision this feeds** (roadmap, pricing move, GTM motion, M&A, battlecard update); stakeholder (PMM / Product / Sales / Strategy / CEO); competitor set (named, with reason each is in-scope); timeframe; definitions (what counts as "mid-market"? what counts as "parity"?); confidentiality rules (what can be sourced from internal win-loss, what cannot be re-shared); assumptions (labeled); **sponsor-bias risks** (does the ask presuppose the answer? e.g., "prove X is beatable on price").

A good CI question names a decision. "Tell me about Competitor X" is a topic, not a question. "Should we match Competitor X's seat-based pricing for the mid-market segment in H1?" is a question.

## 5. Stage B — Scan + landscape, with source tiering

Maintain `search_log.csv`: id, datetime, source/service, query or URL, filters, result count (only if observed), screening status. Unknown counts stay unknown.

**Source tiers** (independence decreases down the list):

| Tier | Examples | Use for |
|------|----------|---------|
| T1 Primary (competitor-authored, auditable) | SEC filings (10-K/Q, S-1), earnings transcripts, pricing pages (+ Wayback), product itself, changelogs, API docs, patents, DEF 14A | facts: pricing, revenue, product capability, officers, incentive design |
| T2 Direct observation | hands-on trial, customer interviews, internal win-loss call notes, discovery call recordings | user experience, deal dynamics, actual rather than claimed capability |
| T3 Structured secondary | G2/Capterra/TrustRadius aggregates (count + trend, not single reviews), LinkedIn headcount + title-mix, job postings, Crunchbase/PitchBook, SimilarWeb/Semrush (direction only), Gartner MQ / Forrester Wave | signal of momentum, hiring intent, analyst framing |
| T4 Analyst / press / community | trade press, analyst blogs, Reddit / HN / Blind / X, podcasts, conference talks | hypotheses, color, early signals — rarely sufficient alone |
| T5 Vendor marketing | competitor's own blog, webinars, case studies, sales decks | what they claim, not what is true |

Rule: a central competitive claim cannot stand on T4–T5 alone. Triangulate up to T1 or T2.

Map the landscape as competing bets, not vendor summaries: who is going upmarket, who is going PLG, who is bundling into a suite, who is cutting on price, who is building the AI story. Note silences — segments / regions / use cases nobody is pursuing may be opportunity or may be a trap.

## 6. Stage H — Stakeholder checkpoint (mandatory unless autonomy is explicitly authorized)

After Stage B, deliver a 300–500 word decision brief: TL;DR of what the scan tentatively suggests and does not establish; candidate decision-shaped question; landscape read; two or more competing reads worth testing (e.g., "they're winning on product" vs "they're winning on channel"); coverage gaps (any T1 sources inaccessible? private company → no filings?); confidentiality items to confirm; recommended direction with trade-offs; decision request.

Offer 2–4 real directions (narrow to one competitor / one segment / one motion; broaden to the landscape; prioritize pricing teardown; prioritize win-loss causal reads; exclude a competitor). Pause. Record choice in `human_decisions.csv` with options, choice, rationale, date, stakeholder.

Running autonomously: pick the recommended direction and log it; do not pretend the stakeholder answered.

## 7. Stage C — Retrieval + source ledger

For each included source, one row in `sources.csv`:

`source_id, title, publisher/author, date (both: publish + data-as-of), url, source_tier (T1–T5), access_level (FULL/PARTIAL/SNIPPET/PAYWALLED), identity_status, identity_verified_on, signal_cluster_id, independence_note, relevance, screening_decision, screening_reason`

Record what the source *actually* says — do not substitute vendor messaging for product capability, a single G2 review for a trend, a job posting title for a confirmed roadmap, LinkedIn headcount for revenue, press release count for market share.

**Identity states**: `VERIFIED` (reliable record confirms publisher + date + URL stable) · `PARTLY_VERIFIED` (record exists, access or date unresolved) · `UNVERIFIED` (not checked) · `CONTRADICTED_LIKELY_FABRICATED` (reliable conflicting records). One failed lookup is not enough to call fabrication.

**Signal clusters** (the CI equivalent of study clusters): one press release gets 12 trade-press pickups; three analysts cite the same 10-K line; a Reddit thread traces back to one X post. Assign a shared `signal_cluster_id` so "many sources" doesn't mean "many signals". Report source count *and* cluster count whenever the distinction matters.

## 8. Stage D — Evidence and claim verification

Two tables, linked by id.

`claims.csv`: `claim_id, text, type (fact / positioning / GTM-motion / segment-focus / feature-parity / momentum / causal / forward-looking), scope (competitor + segment + geo + time), importance (CENTRAL/MAJOR/MINOR), support_status, confidence, open_issues`

`evidence.csv`: `evidence_id, source_id, claim_id, role (SUPPORT/COUNTER/CONTEXT/COLOR), inspected_location (filing page, pricing page section, G2 filter, LinkedIn query, trial step), paraphrase_or_short_quote, what_it_supports, what_it_does_not_support, as-of_date, reviewer, review_date, signal_cluster_id, independence_note`

**Support states**: `DIRECT` (inspected material supports exact claim at stated scope) · `PARTIAL` (narrower version) · `CONTRADICTS` · `NO_SUPPORT` · `NOT_TESTED`. `VERIFIED` identity never implies `DIRECT` support — a real 10-K says what it says, not what you want.

**Claim type ↔ what can support it**:

| Claim type | What the evidence must show |
|------------|------------------------------|
| Fact (price, headcount, feature exists) | T1 or T2 inspection + date-stamped; cite the exact page/screen |
| Positioning | the competitor's own words from T1/T5 (homepage, keynote), separated from your reading of them |
| GTM motion | signals from ≥2 of: hiring (LinkedIn titles), buyer path (self-serve vs demo-gated), partner marketplace, pricing structure |
| Segment focus | logos on site + hiring geo/vertical + pricing tiers + case-study ICP, cross-checked for drift between claimed and actual |
| Feature parity | hands-on trial or docs with specific capability demonstrated; a marketing bullet is a claim, not a capability |
| Momentum | ≥2 independent signals *across different signal_clusters* (traffic trend + hiring + review velocity); any single metric is noise |
| Causal ("they won deal because X") | ruled-out alternatives (price, incumbent, timing, champion change); n=1 lost deal is color, not a cause |
| Forward-looking | a basis beyond vendor marketing: hiring + patent + changelog + partner moves; label uncertainty explicitly |

For every central claim answer both: "what is the strongest version this evidence supports?" and "what tempting stronger version is not supported?" (e.g., evidence supports "Competitor X is hiring 14 enterprise AEs in EMEA" — it does *not* support "Competitor X will beat us in EMEA next year").

Do not force every claim to have three sources. Sparse evidence narrows the claim; it does not justify padding with T4 commentary.

## 9. Stage E — Argument + mirror-battlecard adversarial pass

`arguments.csv`: `argument_id, claim_ids, conclusion, premises, evidence_ids, warrant, inference_type (fact/positioning/GTM/causal/forward), assumptions, alternatives, boundary_conditions, strongest_counterargument, likely_gap, falsifier, confidence`

Run on every major argument: premise support · inferential fit · **causal discipline** (did their price cut cause the churn drop, or did a product release / seasonal effect / support backlog resolve? did we lose on product, or did we lose on champion change?) · alternatives tested, not just named · scope drift (SMB evidence used for enterprise conclusion?) · recency (18-month-old pricing page?) · **sponsor-bias check** (would a differently-sponsored CI team draw the same inference from the same evidence?).

**Mirror battlecard pass** — write the competitor's CI team's battlecard *against your company* using the same evidence base. If their mirror finds obvious wins against you that your version does not acknowledge, your dossier is biased, not thorough. Record what the mirror reveals; let it update the main argument map.

## 10. Stage F — Synthesis + implications

Look for: patterns across tiers (does T2 trial match T5 marketing?); disagreements explained by segment / geo / time; momentum signals backed by independent clusters; evidence that challenges your sponsor's prior; boundary conditions; meaningful absences (segments nobody serves).

Grade every proposed finding:

- `FACT` — directly supported at stated scope by T1/T2 evidence
- `READ` — plausible interpretation consistent with the evidence, under-determined
- `BET` — a forward-looking call the evidence does not test

Grade every implication for the business:

- `ACT` — decision-ready: evidence supports moving now
- `WATCH` — set a tripwire (e.g., "if Competitor X headcount in EMEA passes 40, revisit")
- `RESEARCH-MORE` — the question matters but current evidence can't answer it

Reflexivity in CI: name the sponsor and the decision in flight; call out which read favors them and which does not. "Sales asked, so of course we found a Sales-friendly answer" is the failure mode to prevent.

## 11. Worked mini-example (PROFILE mode)

Topic: *"Should we match Competitor X's seat-based pricing for the mid-market HRIS segment in H1?"*

**A — brief (excerpt)**  
Decision: pricing move for H1 mid-market. Stakeholder: PMM + CRO. Competitor set: X (focus), Y + Z (reference). Definition: mid-market = 200–2,000 employees. Mode: `PROFILE`. Sponsor-bias flag: CRO already said "match them". Label as hypothesis, not conclusion.

**B — search_log row**  
`B07, 2026-10-30T10:04+08, Wayback Machine, pricing.competitorX.com snapshots 2023–2026, n=11 snapshots retrieved, screening=in_progress`

**H — direction chosen**  
"Narrow to pricing architecture + segment focus + win-loss evidence; defer product-parity teardown to a follow-up." (PMM authorized; rationale: pricing move needs pricing + GTM, not full product.)

**C — source row (one)**  
`S022, "Competitor X pricing page", competitorX.com/pricing, publish=2026-09-15, data-as-of=2026-09-15, T1, FULL, VERIFIED, 2026-10-30, cluster=P03, "page itself; 11 Wayback snapshots show tier structure moved from flat to seat-based 2024-11"`

**D — claim + evidence**  
`C004: "Competitor X moved to seat-based pricing in Nov 2024 and the mid-market tier starts at $18/seat/mo on an annual plan" — type=fact, importance=CENTRAL`  
`E031: source=S022, role=SUPPORT, location=pricing page "Growth" tier + Wayback diff 2024-10 vs 2024-11, supports: structure change + current list price; does_not_support: realized ASP (list ≠ sold); support_verdict=DIRECT for list, NOT_TESTED for realized`  
`C005: "Competitor X is winning mid-market deals on pricing" — type=causal, importance=CENTRAL`  
`E032: source=S019 (internal win-loss notes, 7 lost deals Q2–Q3 2026), role=PARTIAL, location=call notes field "primary reason", supports: "price mentioned in 5/7 lost deals"; does_not_support: price as *cause* (champion change in 3/7, incumbent HRIS switch cost in 4/7 — overlapping); support_verdict=PARTIAL`

**E — argument + mirror**  
`A08: premises=C004 + C005 + two momentum signals (hiring + G2 velocity); warrant=pricing move preceded win-rate shift by two quarters; alternatives=champion-change + incumbent-switch friction (both present in notes); confidence=moderate-for-pricing-fact, low-for-"pricing is why they won"`  
Mirror battlecard: competitor's CI team would note our mid-market retention is up 4pp, our ARPU is 2.3× theirs, our implementation is 40% faster — their "match them on price" might not be the move they'd fear.

**F — graded output**  
`FACT: Competitor X moved to seat-based pricing in Nov 2024; mid-market list price $18/seat/mo.`  
`READ: Price is a mentioned factor in lost deals but not the only one; champion stability and switching cost confound a clean causal read.`  
`BET: Competitor X will keep this structure through 2027.`  
Implication — `WATCH, not ACT`: do not match pricing in H1 on this evidence; instrument win-loss to isolate price-only losses from champion-loss and switching-cost losses; set tripwire = ≥60% of lost mid-market deals cite price as *sole* top-1 reason for two consecutive quarters.

Reuse this shape; do not copy its content.

## 12. Final deliverable

Shape by mode. Sections: TL;DR + decision call · brief + scope · landscape or competitor profile · evidence inventory (link `sources.csv`) · claim–evidence matrix (link `claims.csv`, `evidence.csv`) · argument map + mirror pass (link `arguments.csv`) · graded findings + implications · limitations + sponsor-bias note · source audit appendix. `BATTLECARD` mode replaces the synthesis section with a 1–2 page operational card (positioning, strengths vs us, weaknesses vs us, objection handlers, traps) explicitly tagged with claim IDs. `LANDSCAPE` mode replaces competitor profile with a positioning map + per-player one-liner.

Size the deliverable to the decision. A section that does not apply is marked `NOT APPLICABLE` with a reason, not silently dropped.

## 13. Scorecard + readiness gate

Score 1–5 with concrete evidence, not an average: (1) decision clarity + feasibility · (2) landscape read + gap identification · (3) source tiering + independence · (4) evidence coverage + signal-cluster accounting · (5) source identity + claim–source alignment · (6) causal discipline + alternative explanations · (7) mirror-battlecard engagement · (8) sponsor-bias disclosure · (9) argument coherence + traceability · (10) implication grading + tripwire quality.

**Critical fail → status `PROVISIONAL — NOT VALIDATED`** if any of: unresolved fabricated/contradicted central source (invented pricing, headcount, logo) · central claim marked verified while `NO_SUPPORT` or `NOT_TESTED` · causal "they won because X" without alternatives ruled out · mirror battlecard not run · counter-signal (your side's wins) suppressed to please sponsor · a source audit claimed as performed when it was not · implication marked `ACT` without the evidence to carry a reversible-cost decision · required stakeholder checkpoint skipped without authorization.

Otherwise use `AUDITED FOR THE CHECKS LISTED`, never "the full picture of the market".

## 14. Scripts (status: not shipped with this skill)

This skill does not currently include executable audit scripts. If a Python runtime is available, the agent may write minimal helpers (e.g., a Wayback-snapshot differ for pricing pages, a G2 review count fetcher, a LinkedIn title-mix bucketter) — treat their output as T3 evidence, never as T1. Do not report that a script ran if it did not. If the user wants the scripts bundled, build them as a follow-up.

## 15. Final response summary

Close with: what is supported now (findings graded FACT/READ/BET) · implications graded (ACT/WATCH/RESEARCH-MORE) + tripwires for WATCH items · what remains uncertain · gate dashboard · evidence audit (sources + claims checked, tier mix, signal-cluster count vs source count, access level, unresolved mismatches) · argument audit (chain, alternatives, mirror-pass findings) · scorecard profile and any critical fail · decision log · deliverable filenames.

The test: after the chat ends, the stakeholder can act on the dossier, trace every number back to its tier-stamped source, defend the call to a skeptical executive, and tell you exactly which later signal would change the recommendation.

## Changelog

- **v1 (2026-10-30)** — Initial release. Structure, discipline, and compression style derived from `sociology-deep-research` v2; retuned end-to-end for B2B competitive intelligence: source tiering (T1–T5), signal clusters, CI-specific claim types, mirror-battlecard adversarial pass, sponsor-bias check, FACT/READ/BET + ACT/WATCH/RESEARCH-MORE grading, worked pricing-move example.
