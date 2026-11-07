---
name: positioning-messaging
description: Write product positioning and a messaging framework (a messaging house) from existing product docs, FAB analysis, personas and competitor research. Use when a PMM, founder or PM needs a positioning statement, value proposition, messaging pillars, a tagline or homepage hero options, elevator pitches, or messaging for a new product, a rebrand or a new market. Based on April Dunford-style positioning: alternatives first, then unique value.
---

# Positioning & Messaging

Input: what the team knows about the product, customers and competitors (PRD, FAB analysis, personas, competitor notes, sales feedback). Output: one positioning statement and a messaging house that copy, sales decks and launch posts can all draw from.

## How to work

1. **Clarify in one message.** Ask:
   - **Goal and scope:** a new product, repositioning, a new segment, or a new market? Where will the messaging be used first? (website, sales deck, launch)
   - **Materials:** PRD, FAB analysis, personas, competitor research, win/loss notes, customer quotes
   - **Target customer:** who it's best for. Push for a narrow answer; "everyone" is not a target.
   - **Constraints:** brand voice, words to avoid, legal limits on claims, language and market

   Done when you know the target customer and have at least one named alternative. If `product-value-fab` or `customer-review-mining` output exists, use it.

2. **Map the positioning, in this order** (each step builds on the one before):
   1. **Competitive alternatives:** what customers would use if this product didn't exist, including spreadsheets, agencies and doing nothing.
   2. **Unique attributes:** what the product has that those alternatives don't.
   3. **Value:** what those attributes let customers do (from the FAB benefits).
   4. **Best-fit customers:** who cares most about that value.
   5. **Market category:** the frame that makes the value obvious. Choose an existing category, a sub-category, or (rarely) a new one, and say why.

   Done when each step cites the material it came from, or is marked as an assumption.

3. **Write the positioning statement:** *For <target> who <pain/need>, <product> is a <category> that <key value>. Unlike <main alternative>, it <key difference>.*

4. **Build the messaging house:** one umbrella message, 3 pillars (each with proof points), and the objection each pillar answers. Every proof point must be real: a feature, data, a customer quote, or an award.

5. **Draft usable copy:** 3 tagline options, 3 homepage hero options (headline + subhead), a 1-sentence, 30-second and 2-minute pitch, plus a short list of words to use and words to avoid.

## Output template

```markdown
# Positioning & messaging: <product>

## Positioning canvas
| Competitive alternatives | Unique attributes | Value | Best-fit customers | Market category |
|---|---|---|---|---|

## Positioning statement
For ... who ..., <product> is a ... that .... Unlike ..., it ....

## Messaging house
**Umbrella message:** ...
| Pillar | Message | Proof points | Objection it answers |
|---|---|---|---|

## Copy starters
- **Taglines:** 1. … 2. … 3. …
- **Homepage hero:** headline / subhead × 3
- **Pitches:** 1 sentence · 30 seconds · 2 minutes
- **Use / avoid:** ...

## Open risks
- <claims needing proof, segments not yet validated>
```

## Rules

- Don't write copy before the positioning canvas is done; copy without positioning is guessing.
- Never invent proof points, customer logos, statistics or awards. Missing proof is listed under Open risks.
- Prefer the customer's words (from reviews and interviews) over marketing language. Avoid empty words like "seamless", "revolutionary" and "all-in-one" unless they're true and specific.
