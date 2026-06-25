# Example Output: Seed B2B SaaS Customer-Evidence Workflow

This is an example of the kind of output the skill should produce. Note the unit of work is a **workflow made of loops**, not a portfolio of standalone agents. Runners are named per loop and are swappable; verifiers gate autonomy; corrections feed back.

## Verdict

The first workflow to build is **Customer Evidence → Product/Sales Action**: turning every customer conversation into structured evidence, then routing it to sales follow-up and product decisions.

The first loops to automate are call/support synthesis (L1 Draft) and feedback triage (L2 Recommend).

Do not automate customer replies, deal-stage changes, or roadmap commitments yet — they are irreversible and have no verifier. Keep them human-owned.

## Goal And Bottleneck Read

- Business goal: shorten the time from customer conversation to sales follow-up and product decision (learning speed).
- Constraint: founder and product attention is overloaded by scattered customer evidence (Gong, Slack, Linear, Notion).
- Slow, repeated, valuable process: calls/support → CRM updates, product decisions, follow-up tasks.
- Highest-leverage human bottleneck: founder review and product prioritization.

## Workflow Graph

Goal: customer conversation → action, faster.

```text
new call/support thread
-> Loop 1: synthesize evidence (Claude, L1)
-> Loop 2: tag + draft CRM note + follow-up (Claude, L1)
-> [human review: Founder approves follow-up]
-> Loop 3: feedback triage into product themes (Codex/Claude, L2)
-> [human review: Head of Product prioritizes]
-> update CRM + Linear
        ^
        |__ corrections (accepted/edited summaries, missed signals) update Loops 1-3
```

## Loop Summary Table

| # | Loop | Trigger | Runner | Verifier | Human Input When | Owner | Metric |
|---:|---|---|---|---|---|---|---|
| 1 | Synthesize evidence | New transcript/support thread | Claude (alt: Codex, human) | Cites sources, fills required fields, confidence ≥ 0.7 | Confidence low or evidence ambiguous | Founder | 80% summaries accepted w/ minor edits |
| 2 | Tag + draft CRM note/follow-up | Loop 1 output passes | Claude (alt: human) | Schema check on CRM fields; follow-up matches ICP | Pricing/security/roadmap ask | Founder | 50% faster call→follow-up |
| 3 | Feedback triage | Loop 1 output tagged "product" | Codex/Claude (alt: human) | ≥3 matching signals before a theme is raised | New theme or conflicting signals | Head of Product | 10+ actionable signals/week |

## Top Loop Card (detailed)

### Loop 1: Synthesize Evidence

- Goal served: faster learning from every conversation.
- Trigger: new call transcript, support thread, or customer note.
- Context: transcript, CRM account, support history, current ICP, roadmap, pricing notes, prior corrections.
- Runner (and why): Claude for strong summarization over messy transcripts. Swappable to Codex or a human analyst without changing the loop.
- Output: structured evidence (buying signals, objections, feature requests, proof points).
- Verifier (definition of done): cites sources, all required fields present, flags missing data, confidence ≥ 0.7.
- Autonomy level: L1 Draft — output is reviewed before it drives action.
- Allowed actions: summarize, tag, draft CRM note, suggest follow-up, propose feedback labels.
- Forbidden actions: send customer messages, change deal stage, promise roadmap.
- Human input when: confidence below threshold, ambiguous evidence, or a pricing/security/roadmap ask appears.
- Human owner: Founder/CEO (sales evidence), Head of Product (product evidence).
- Escalation: stop on irreversible/risky asks; send source + extracted evidence + confidence to the owner.
- Success + quality metric: % accepted summaries (throughput) and edit distance on accepted summaries (quality).
- Trace: source, extracted evidence, runner, confidence, suggested owner, verifier result, human edits, accepted outcome.
- Correction sink: edits become golden examples; recurring misses become new required context fields or verifier rules.

## Routing And Escalation

| Event | Primary Resolver | Verifier | Backup | Escalation Rule |
|---|---|---|---|---|
| Security/procurement objection | Founder/CEO | human | Compliance-packet workflow (later) | Escalate immediately |
| Repeated feature request from ICP | Loop 3 (feedback triage) | ≥3 matching signals | Head of Product | Raise theme after 3 signals |
| High-fit account, unclear buyer | Loop 2 (outbound draft) | ICP match check | Founder/CEO | Escalate if confidence < 0.7 |

## 14-Day Pilot

- Workflow: Customer Evidence → Product/Sales Action.
- Build: Loops 1 and 2 on call transcripts and support threads.
- Cut: automated replies, CRM stage changes, roadmap commitments.
- Baseline: current time from conversation to CRM/product update.
- Success bar (speed AND quality): 80% accepted summaries, 50% faster follow-up, 10 labeled product signals/week — with edit distance trending down.
- Reverse gear: if accepted-summary rate drops below 70% for a week, Loop 1 returns to full human review.
- Stop condition: summaries need heavy edits or do not change follow-up behavior.

## Corrections After Week 1 (example)

| Date | Loop | Root cause | Correction type | Change applied |
|---|---|---|---|---|
| Day 4 | Loop 1 | Missing renewal date in summaries | required context field | Add "renewal date" to context + verifier |
| Day 6 | Loop 3 | Theme raised on 1 signal | weak verifier | Raise threshold to 3 matching signals |
| Day 9 | Loop 2 | Generic follow-ups | accepted example | Add 5 golden follow-ups as few-shot |
