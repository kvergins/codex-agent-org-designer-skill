---
name: agent-org-designer
description: Design and run the hybrid-workforce operating model for a company or team. Map business goals into workflows made of loops, assign swappable runners (Claude, Codex, Cowork, OpenClaw, Copilot, internal agents, or humans), define verifiers, route human input, and capture corrections that improve every run. Use when the user asks how to plan or execute AI-heavy work: what workflows to build, what agents or humans should run each step, how to design loops, verifiers, escalation, and corrections, how to create an agent or workflow operating model, or how to audit an existing agent/workflow setup.
---

# Agent Org Designer

## Overview

Use this skill to plan and execute the operating model for a company where humans work alongside AI agents.

The core shift: do not manage prompts or individual agents. Manage **workflows made of loops**, run by agents and humans, improved by corrections.

```text
business goal
-> workflow
-> loop cards
-> agent or human runners
-> verifier
-> done or human input
-> correction
-> improved workflow
```

The old model ("an agent fleet is a company") was directionally right but static. The missing idea is the **workflow graph**: a company process made of many loops, where some steps are agent-owned, some human-owned, and some hybrid. This skill designs that graph and gives the user the templates to run it.

## The Operating Model In One Line

> Agents run the loops. Humans resolve the judgment. The workflow improves after every run.

## First Move

If the company context is missing, ask for the minimum useful context:

```text
Send the company type, stage, top 3 business goals, the slowest/most repeated valuable processes, current tools, which agents (Claude, Codex, Cowork, OpenClaw, Copilot, internal) are already in use, and where humans lose the most time or momentum.
```

If enough context exists, start immediately and make assumptions explicit. Always start from a **goal and a workflow**, never from a job title or a model.

## Core Elements

These eight elements are the vocabulary for everything this skill produces.

1. **Goal** — the business outcome (throughput, quality, speed, cost, learning). Never "use agents."
2. **Workflow** — the full company process connecting multiple loops, agents, humans, approvals, and handoffs. The map of how work moves.
3. **Loop** — a reusable job description for one part of the workflow: trigger, context, runner, output, verifier, human input. Loops are durable; runners are replaceable.
4. **Runner** — what executes a loop: Claude, Codex, Claude Code, Cowork, OpenClaw, Copilot, an internal agent, or a human. The runner is not the product.
5. **Work packet / run** — one instance of a loop doing work. Carries goal, context, runner, output, status, owner, verifier, human input needed, correction, history.
6. **Verifier** — the definition of done: a test, rule, source check, schema check, second agent, or human reviewer. No verifier, no autonomy.
7. **Human input** — the normal management chain, not a failure. Triggered when the verifier fails, the runner is blocked, context is missing, or the decision is risky/irreversible/judgment-heavy.
8. **Correction** — the learning captured from human judgment. Becomes a better instruction, a required context field, a new verifier, an accepted example, a policy/escalation rule, or a "this runner is wrong for this loop" note. This is the compounding moat.

## How The Pieces Collaborate

```text
1. A workflow starts because a business event happens.
2. The first loop receives a work packet.
3. The assigned runner produces an output.
4. A verifier checks whether the output is good enough.
5. If it passes, the next loop starts.
6. If it fails or gets stuck, a human input item is created.
7. The human resolves, corrects, rejects, or reroutes.
8. The correction updates the loop.
9. The workflow runs better next time.
```

## Load-Bearing Rules

1. **Design workflows first, agents second.** Start from a slow, repeated, valuable process — not "we need a research agent." Ask: which steps can an agent run, which need a human, what proves each step is done?
2. **Loops outlive runners.** The company should be able to swap Claude for Codex, OpenClaw, Copilot, an internal model, or a human without losing the process. The loop definition and correction history persist; the runner is interchangeable.
3. **No verifier, no autonomy.** Strong verifier → more autonomous loop. Weak verifier → human review. No verifier → human-owned step. Autonomy is earned by evidence.
4. **Human attention is the scarce resource.** AI makes execution cheap, not judgment. Do not maximize agent usage; allocate human attention where judgment changes the outcome.
5. **Escalation is part of the process.** Every loop must define when to stop, why it stopped, who owns the next decision, what context to send, and how the correction changes next time.
6. **Corrections become the moat.** The valuable dataset is not chat history. It is accepted outputs, rejected outputs, edits, stuck steps, missing context, better verifiers, and human decisions. Capture them.
7. **Humans hold accountability.** Agents own throughput, not final accountability. Every important branch terminates in a human owner. Humans keep irreversible commitments, pricing, hiring, legal/reputation risk, strategy, and customer promises.

## Modes

Choose the mode from the request. If unclear, use `full`.

- `diagnosis`: find the slow, repeated, valuable processes where loops can create leverage.
- `workflow-map`: turn a business goal into a workflow graph of connected loops (the primary planning mode).
- `loop-design`: write detailed loop cards (trigger, context, runner, output, verifier, human input, escalation, metric, trace).
- `runner-assignment`: choose the right runner per loop and set autonomy from verifier strength.
- `routing-map`: define handoffs, human-input items, and escalation paths across loops, agents, humans, and teams.
- `run`: execute the workflow — instantiate work packets, run loops, log verifier results and human input. (Execution mode.)
- `correction-log`: capture corrections from a run and turn them into loop improvements. (Execution mode.)
- `rollout`: create a 14-30 day pilot plan for one workflow with success criteria and a reverse gear.
- `audit`: review an existing agent/workflow setup for missing verifiers, owners, runner lock-in, unsafe autonomy, broken escalation, or uncaptured corrections.
- `full`: compact diagnosis, workflow map, top loop cards, runner assignment, routing, and rollout.

Read `references/playbooks.md` for templates, scoring, execution playbooks (run + correction log), and per-mode detail.

## Workflow (How To Run This Skill)

1. **Map the operating system.** Identify goals, recurring valuable processes, decision points, handoffs, blocked queues, and current tools and runners.
2. **Draw the workflow graph.** For the top goal, lay out the end-to-end process as connected loops. Mark each loop agent-owned, human-owned, or hybrid.
3. **Design loops.** For each loop write the card: trigger, context, runner, output, verifier, human input, escalation, owner, metric, trace.
4. **Assign runners and autonomy.** Pick the runner per loop. Set autonomy from verifier strength using the autonomy ladder. Default early loops to L1-L3.
5. **Design routing and escalation.** Specify when each loop answers, drafts, recommends, executes, asks a human, or reroutes — and who owns the next decision.
6. **Plan rollout.** Pilot one workflow end-to-end, instrument every run, compare to baseline, expand only after acceptance, and keep a reverse gear.
7. **Execute and correct.** Run work packets through loops, capture human input and corrections, and update the loops so the next run is better.

## Default Output

Use this compact structure unless the user asks for a longer plan:

```markdown
**Verdict**
The first workflow to build is ...
The first loops to automate are ...
Do not automate ... yet because ... (no verifier / no owner / irreversible).

**Goal And Bottleneck Read**
- Business goal:
- Constraint:
- Slow, repeated, valuable process:
- Highest-leverage human bottleneck:

**Workflow Graph**
Goal: ...
```text
loop A -> loop B -> [human review] -> loop C -> loop D
```

**Loop Cards**
| # | Loop | Trigger | Runner | Verifier | Human Input When | Owner | Metric |
|---:|---|---|---|---|---|---|---|
| 1 | ... | ... | Claude/Codex/human | ... | ... | ... | ... |

**Top Loop Card (detailed)**
### 1. Loop Name
- Goal served:
- Trigger:
- Context:
- Runner (and why):
- Output:
- Verifier (definition of done):
- Autonomy level:
- Human input when:
- Human owner:
- Escalation (stop / why / who / what context):
- Success metric + quality metric:
- Trace:
- Correction sink (where learnings go):

**Routing And Escalation**
| Event | Primary Resolver | Backup | Verifier | Escalation Rule |
|---|---|---|---|---|

**14-Day Pilot**
- Workflow:
- Build (which loops):
- Cut:
- Baseline:
- Success bar (speed AND quality):
- Reverse gear (when a loop drops from autonomous back to reviewed):
- Stop condition:
```

## Loop / Agent Fit Scoring

Score each candidate loop from 1-5 only when it improves the decision.

| Area | What 5 Means |
|---|---|
| Pain frequency | Happens often enough to matter every week |
| Context availability | Required context is accessible and structured enough |
| Tool readiness | The runner can use the needed systems safely |
| Verifiability | "Done" can be checked by test, rule, schema, source, or reviewer |
| Reversibility | Mistakes are cheap or reviewable |
| Human bottleneck | Frees scarce founder/operator/technical time |
| Escalation clarity | It is obvious when and where the loop should ask for human input |
| Strategic leverage | Accelerates revenue, learning, retention, or delivery |

Verifiability is the gate for autonomy: a high-frequency loop with no verifier stays human-owned until a verifier exists.

## Autonomy Ladder

Autonomy is set by verifier strength, not ambition.

- `L0 Observe`: summarize, classify, extract, monitor.
- `L1 Draft`: prepare artifacts for human approval.
- `L2 Recommend`: choose an option with rationale, human decides.
- `L3 Execute reversible`: take bounded actions that can be undone.
- `L4 Execute bounded irreversible`: act inside strict policy and approval thresholds.
- `L5 Own loop by exception`: run the loop, escalate exceptions only. Requires a strong verifier and a track record of corrections.

Default early loops to `L1-L3`. A loop may only rise a level after its verifier has held across enough runs — and must be able to drop back when quality falls (the reverse gear).

## Dynamics To Watch

- **The good flywheel:** runs → agents handle repeatable steps → humans resolve stuck/risky steps → corrections update loops → verifiers improve → more of the workflow runs with less supervision.
- **The safety loop:** more autonomy → less review → more chance of silent errors. Build a reverse gear so a loop can return to reviewed mode when quality drops.
- **Feedback delay:** catch bad output at the verifier or human-input step, not days later. Shortening feedback delay often beats making any one runner smarter.
- **Goodhart:** never optimize speed alone (people rubber-stamp) or automation alone (bad work ships). Measure speed AND quality together.

## Rules

- Always start from a goal and a workflow, never from a job title or a model.
- Do not create generic roles like "CEO agent" or "AI employee"; narrow to a loop inside a workflow.
- No verifier, no autonomy. If a loop needs trust but has no eval, make it L1 Draft / human-owned first.
- Name the runner per loop, and design so the runner is swappable without losing the loop or its corrections.
- Every loop needs a human owner, a verifier, allowed/forbidden actions, an escalation path, and a correction sink.
- If two loops share the same trigger, context, and owner, merge them or define the routing difference.
- Force prioritization into now / next / later when the user wants many loops.
- Always include a reverse gear: how a loop drops from autonomous back to reviewed.
- Measure accepted outcomes and corrections, not token usage or agent count.
- For startups, bias toward workflows that increase customer conversations, ship/learn cycles, support quality, or founder leverage. For larger companies, bias toward clear workflow ownership, compliance, auditability, and change management.
