---
name: agent-org-designer
description: Design useful AI agent roles, responsibilities, autonomy boundaries, handoffs, and rollout plans for a company or team. Use when the user asks what agents to build, how to design autonomous agents for internal employees, how to create an agent org chart or agent operating model, how to assign agent roles and responsibilities, how to evaluate agent opportunities, or how to audit an existing agent setup against company needs.
---

# Agent Org Designer

## Overview

Use this skill to decide which AI agents a company should build and how those agents should work alongside humans. The core lens: do not design "digital employees"; design owned operational loops with triggers, inputs, tools, outputs, autonomy limits, metrics, and escalation paths.

## First Move

If the company context is missing, ask for the minimum useful context:

```text
Send the company type, stage, top 3 goals, biggest bottlenecks, current tools/workflows, and where humans lose the most time or momentum.
```

If enough context exists, start immediately and make assumptions explicit.

## Core Principles

- Design agents from company bottlenecks, not from trendy job titles.
- Model each agent as a loop: `trigger -> inspect context -> decide/act -> produce output -> trace outcome -> escalate when needed`.
- Give agents throughput ownership, not final accountability.
- Humans own irreversible commitments, pricing, hiring, legal/reputation risk, strategy, and customer promises.
- Every agent needs a human owner, success metric, allowed tools, forbidden actions, and escalation rule.
- Prefer narrow agents that create measurable learning or revenue speed before broad "chief of staff" agents.
- Do not recommend building an agent if the process, data, tools, owner, or eval path is missing.

## Modes

Choose the mode from the request. If unclear, use `full`.

- `diagnosis`: identify where agents could accelerate the company.
- `portfolio`: design the agent portfolio and priority order.
- `charter`: write detailed role charters for one or more agents.
- `routing-map`: define handoffs between agents, humans, teams, and escalation paths.
- `rollout`: create a 14-30 day pilot plan with success criteria.
- `audit`: review existing internal agents and find gaps, risks, overlap, or missing owners.
- `full`: compact diagnosis, portfolio, top charters, routing, and rollout.

Read `references/playbooks.md` when the user asks for deep mode, a detailed artifact, templates, scoring, or a specific mode.

## Workflow

1. **Map the operating system.** Identify goals, recurring workflows, decision points, handoffs, blocked queues, and current tools.
2. **Find agentable loops.** Score opportunities by pain frequency, context availability, tool readiness, reversibility, human bottleneck, eval clarity, escalation clarity, and strategic leverage.
3. **Prioritize.** Choose agents that shorten the highest-value loop first, usually revenue, customer learning, product feedback, support, operations, or founder leverage.
4. **Write role charters.** Define outcome, trigger, inputs, tools, allowed actions, forbidden actions, escalation, owner, metrics, and trace.
5. **Set autonomy level.** Use the lowest autonomy level that creates useful throughput.
6. **Design routing.** Specify when the agent answers, drafts, recommends, executes, asks a human, or routes to another resolver.
7. **Plan rollout.** Start with one or two narrow pilots, instrument outcomes, compare to baseline, and expand only after acceptance.

## Default Output

Use this compact structure unless the user asks for a longer plan:

```markdown
**Verdict**
The first agents to build are ...
Do not build ... yet because ...

**Company Bottleneck Read**
- Constraint:
- Slow loop:
- Highest-leverage human bottleneck:

**Agent Portfolio**
| Priority | Agent | Job | Human Owner | Autonomy | Why Now | Success Metric |
|---:|---|---|---|---|---|---|
| 1 | ... | ... | ... | ... | ... | ... |

**Top Role Charters**
### 1. Agent Name
- Outcome:
- Trigger:
- Inputs:
- Tools:
- Allowed actions:
- Forbidden actions:
- Escalates when:
- Human owner:
- Success metric:
- Trace:

**Routing And Escalation**
| Intent/Event | Primary Resolver | Backup | Escalation Rule |
|---|---|---|---|

**14-Day Pilot**
- Build:
- Cut:
- Baseline:
- Success bar:
- Stop condition:
```

## Agent Fit Scoring

Score each candidate from 1-5 only when it improves the decision.

| Area | What 5 Means |
|---|---|
| Pain frequency | Happens often enough to matter every week |
| Context availability | Required context is accessible and structured enough |
| Tool readiness | Agent can use the needed systems safely |
| Reversibility | Mistakes are cheap or reviewable |
| Human bottleneck | Frees scarce founder/operator/technical time |
| Eval clarity | Output quality can be judged consistently |
| Escalation clarity | It is obvious when and where the agent should route |
| Strategic leverage | Accelerates revenue, learning, retention, or delivery |

## Autonomy Ladder

- `L0 Observe`: summarize, classify, extract, monitor.
- `L1 Draft`: prepare artifacts for human approval.
- `L2 Recommend`: choose an option with rationale, human decides.
- `L3 Execute reversible`: take bounded actions that can be undone.
- `L4 Execute bounded irreversible`: act inside strict policy and approval thresholds.
- `L5 Own loop by exception`: run the loop and escalate exceptions only. Rare for early deployments.

Default early internal agents to `L1-L3`.

## Rules

- Do not create generic roles like "CEO agent", "strategy agent", or "AI employee" without narrowing the loop.
- Do not optimize for the biggest automation surface; optimize for the highest-leverage constraint.
- If the user wants many agents, force prioritization into now / next / later.
- If two agents share the same trigger, inputs, and owner, merge them or define the routing difference.
- If an agent needs high trust but has no eval, recommend a draft/recommendation role first.
- Include human ownership even when the user asks for full autonomy.
- Include explicit anti-goals and forbidden actions for every high-risk agent.
- For startups, bias toward agents that increase customer conversations, ship/learn cycles, support quality, or founder leverage.
- For larger companies, bias toward clear workflow ownership, compliance, auditability, and change management.
