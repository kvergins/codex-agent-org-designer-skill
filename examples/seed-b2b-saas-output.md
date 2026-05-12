# Example Output: Seed B2B SaaS Agent Portfolio

This is an example of the kind of output the skill should produce.

## Verdict

The first agents to build are a Customer Evidence Agent, an Outbound Prep Agent, and a Product Feedback Triage Agent.

Do not build a broad "chief of staff agent" yet. The company bottleneck is not general executive capacity; it is converting customer conversations into sharper sales follow-up and product decisions.

## Company Bottleneck Read

- Constraint: founder and product team attention is overloaded by scattered customer evidence.
- Slow loop: calls and support conversations take too long to become CRM updates, product decisions, and follow-up tasks.
- Highest-leverage human bottleneck: founder review and product prioritization.

## Agent Portfolio

| Priority | Agent | Job | Human Owner | Autonomy | Why Now | Success Metric |
|---:|---|---|---|---|---|---|
| 1 | Customer Evidence Agent | Extract buying signals, objections, feature requests, and proof points from calls and support | Founder/CEO | L1 Draft | Speeds learning and sales follow-up | 80% of call summaries accepted with minor edits |
| 2 | Product Feedback Triage Agent | Cluster feedback into product themes and route to Linear | Head of Product | L2 Recommend | Reduces lost customer insight | 10+ actionable product signals/week |
| 3 | Outbound Prep Agent | Research target accounts and draft personalized outreach | Founder/CEO | L1 Draft | Increases qualified conversations | 30%+ of surfaced accounts accepted for outreach |

## Top Role Charter

### Customer Evidence Agent

- Outcome: turn every customer conversation into structured evidence the team can act on.
- Trigger: new call transcript, support thread, or customer note.
- Inputs: call transcript, CRM account, support history, current ICP, product roadmap, pricing notes.
- Tools: Gong/Zoom transcript export, CRM, Notion, Linear, Slack.
- Allowed actions: summarize, tag, draft CRM notes, suggest follow-up, propose product feedback labels.
- Forbidden actions: send customer messages, change deal stage, promise roadmap commitments.
- Escalates when: customer asks for pricing exception, enterprise security commitment, roadmap promise, or evidence is ambiguous.
- Human owner: Founder/CEO for sales evidence, Head of Product for product evidence.
- Success metric: percentage of accepted summaries and follow-up tasks.
- Trace: source, extracted evidence, confidence, suggested owner, human edits, accepted outcome.

## Routing And Escalation

| Intent/Event | Primary Resolver | Backup | Escalation Rule |
|---|---|---|---|
| Security or procurement objection | Founder/CEO | Compliance Packet Agent later | Escalate immediately |
| Repeated feature request from ICP | Product Feedback Triage Agent | Head of Product | Escalate after 3 matching signals |
| High-fit account with unclear buyer | Outbound Prep Agent | Founder/CEO | Escalate if confidence below 0.7 |

## 14-Day Pilot

- Build: Customer Evidence Agent for call transcripts and support threads.
- Cut: automated customer replies, CRM stage changes, roadmap commitments.
- Baseline: current time from call to CRM/product update.
- Success bar: 80% accepted summaries, 50% faster follow-up, 10 labeled product signals.
- Stop condition: summaries require heavy edits or do not change follow-up behavior.
