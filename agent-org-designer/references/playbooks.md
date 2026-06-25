# Agent Org Designer Playbooks

Use these playbooks when the user asks for a specific mode, deep design work, execution templates, or reusable artifacts. Everything here is built on the operating model: **workflows made of loops, run by swappable runners, gated by verifiers, improved by corrections.**

Planning modes: diagnosis, workflow-map, loop-design, runner-assignment, routing-map, rollout, audit.
Execution modes: run, correction-log.

---

## Diagnosis Mode

Role: Act as an operating-system designer for the company.

Task: Find the slow, repeated, valuable processes where loops can create leverage without hidden operational risk.

Steps:
- Identify the company's goals and constraints.
- Map slow recurring processes: sales, product learning, support, delivery, finance, recruiting, ops, compliance, engineering.
- Separate "humans are overloaded" from "the process is unclear" — only the first is a candidate for loops; the second needs process design first.
- For each candidate, check: accessible context, repeatable decisions, a checkable definition of done, and a clear escalation path.
- Recommend the first 1-3 workflows (not isolated agents) to build.

Output:
- Goal and bottleneck read
- Candidate workflows (each as a chain of loops)
- Non-agentable problems (process, data, or ownership gaps)
- First workflow to build
- What not to automate yet (and why: no verifier / no owner / irreversible)

---

## Workflow-Map Mode (primary planning mode)

Task: Turn one business goal into a workflow graph of connected loops.

Steps:
1. State the goal as an outcome (throughput, quality, speed, cost, learning).
2. Lay out the end-to-end process as a sequence/graph of loops.
3. For each loop, mark it agent-owned, human-owned, or hybrid.
4. Mark every human-input and approval point.
5. Mark where corrections feed back into earlier loops.

Workflow graph shape:

```text
Goal: <business outcome>

trigger event
-> loop A (runner, verifier)
-> loop B (runner, verifier)
-> [human review: owner, decision]
-> loop C (runner, verifier)
-> done
        ^
        |__ corrections update loops A-C
```

Examples of real workflows as loop chains:

```text
support resolution = classify + retrieve context + draft reply + policy check + human approve + send
engineering delivery = issue intake + plan + code + test + review + merge
client research = gather data + summarize + check claims + human edit + deliver
renewal prep = research account + analyze risk + draft recommendation + human review + draft follow-up + update CRM
```

Output:
- Goal
- Workflow graph (loops in order, owner type per loop)
- Loop summary table (see below)
- Human-input points
- Correction feedback points

Loop summary table:

| # | Loop | Trigger | Runner | Verifier | Human Input When | Owner | Metric |
|---:|---|---|---|---|---|---|---|
| 1 | ... | ... | Claude/Codex/Cowork/human | ... | ... | ... | ... |

---

## Loop-Design Mode

Task: Turn one loop into an implementation-ready card. A loop is durable; the runner is replaceable.

Loop card template:

```markdown
### Loop Name

**Goal served**
Which business outcome this loop moves.

**Trigger**
When the loop starts: scheduled, event-driven, human-invoked, or handed off from another loop.

**Context**
The inputs the runner needs: documents, tickets, CRM records, analytics, emails, calls, code, databases, APIs, prior corrections.

**Runner**
Claude / Codex / Claude Code / Cowork / OpenClaw / Copilot / internal agent / human — and why this runner fits. Note that it is swappable.

**Output**
The artifact this loop produces.

**Verifier (definition of done)**
Test, rule, source check, schema check, second agent, or human reviewer. Be specific. No verifier, no autonomy.

**Autonomy level**
L0-L5, justified by verifier strength.

**Allowed actions / Forbidden actions**
What the runner may do; what requires a human or is out of scope.

**Human input when**
Verifier fails, runner blocked, context missing, decision risky/irreversible/judgment-heavy.

**Human owner**
The person accountable for quality and business outcome.

**Escalation**
When to stop, why it stopped, who owns the next decision, what context to send.

**Success metric + quality metric**
One throughput metric and one quality metric (measure both — watch Goodhart).

**Trace**
What must be logged: trigger, context used, runner, decision, output, verifier result, resolver, outcome, label.

**Correction sink**
Where learnings land: instruction update, new context field, new verifier, accepted example, policy/escalation rule, or "this runner is wrong for this loop."
```

---

## Runner-Assignment Mode

Task: Choose the right runner per loop and set autonomy from verifier strength.

Steps:
- For each loop, list candidate runners (agent options and human).
- Pick the runner that best fits the context, tools, and risk — not the trendiest model.
- Set autonomy from the verifier: strong verifier → higher autonomy; weak/none → human review.
- Confirm the loop survives a runner swap (Claude → Codex → human) without losing definition or corrections.

Runner-assignment table:

| Loop | Chosen Runner | Alternative Runners | Verifier Strength | Autonomy | Reverse-Gear Trigger |
|---|---|---|---|---|---|
| ... | Claude | Codex, human | strong/medium/weak | L1-L5 | quality metric drops below X |

Rules:
- The runner is replaceable; the loop and corrections persist.
- Do not lock a workflow to one vendor's runtime.
- A loop with no verifier stays human-owned regardless of how capable the runner is.

---

## Routing Map Mode

Task: Define how loops, agents, and humans hand off work and route human input when stuck.

Resolver types:
- Runner (agent or human executing the loop)
- Verifier (automated or human)
- Human owner
- Team queue
- Escalation path
- External system

Routing table:

| Event | Primary Resolver | Verifier | Backup Resolver | Timeout | Escalation Rule | Trace Required |
|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | yes |

Rules:
- Every high-risk route terminates in a human owner.
- Timeouts must have a backup path.
- A loop escalates uncertainty before acting silently.
- Repeated escalations on the same loop are a signal to improve context, tools, verifier, runner, or the loop card — log them as corrections.

---

## Run Mode (execution)

Task: Execute a workflow by instantiating work packets and moving them through loops. This is how the user *executes* the plan, not just designs it.

A run is one instance of a loop doing work. Track it with the work packet below.

Work packet / run template:

```markdown
## Run: <workflow> / <loop> / <id>

- Goal:
- Trigger event:
- Context used:
- Runner:
- Output:
- Verifier result: pass / fail / needs-human
- Status: running / blocked / done / escalated
- Owner:
- Human input needed: (what was tried, what is needed, what decision unblocks it)
- Correction: (link to correction-log entry, if any)
- History: (timestamps, runner swaps, re-runs)
```

Run loop checklist:
1. A business event fires the trigger → create a work packet.
2. Assign the runner and gather context.
3. Runner produces output.
4. Verifier checks the output.
5. Pass → advance the packet to the next loop. Fail/stuck → create a human-input item with full context.
6. Human resolves, corrects, rejects, or reroutes.
7. Log a correction (see below) and update the loop.
8. Close the packet with an outcome label.

Good human-input item includes: what was tried, what is needed, and what decision will unblock the workflow.

---

## Correction-Log Mode (execution)

Task: Capture the learning from human judgment and convert it into a durable improvement. Corrections are the compounding moat — capture them every run.

Correction log entry template:

```markdown
## Correction: <date> / <workflow> / <loop>

- Run / work packet id:
- What happened: (the output, the stuck step, or the rejection)
- Human judgment: (what the human decided and why)
- Root cause: (missing context / weak verifier / wrong runner / bad instruction / policy gap)
- Correction type:
  - [ ] better instruction
  - [ ] required context field
  - [ ] new or stronger verifier
  - [ ] accepted/golden example
  - [ ] policy rule
  - [ ] escalation rule
  - [ ] runner is wrong for this loop
- Change applied to the loop card:
- Expected effect on next run:
- Owner:
```

Rules:
- Every human-input resolution should produce a correction or an explicit "no change needed."
- Corrections that recur across runs are the highest-value upgrades — prioritize them.
- The dataset that compounds is corrections, not chat history: accepted outputs, rejected outputs, edits, stuck steps, missing context, better verifiers, human decisions.

---

## Rollout Mode

Task: Build a 14-30 day plan that validates one workflow end-to-end before expansion.

Plan shape:

```markdown
**Pilot Goal**
The business outcome and the one workflow being validated.

**Scope**
- Workflow:
- Build (which loops):
- Cut:
- Human owner:
- Users:

**Baseline**
Current time, cost, cycle time, error rate, backlog, response time, or missed opportunity for this workflow.

**Instrumentation**
Trace every work packet: trigger, context, runner, output, verifier result, human input, correction, accepted outcome.

**Week 1**
- Workflow graph + loop cards
- Access and runner setup
- Golden examples and verifiers
- First dry runs (work packets, no irreversible actions)

**Week 2**
- Run on real work with human approval at each verifier
- Log corrections
- Compare speed AND quality against baseline
- Decide: expand autonomy, revise loops, or stop

**Success Bar**
Speed and quality together (never speed alone).

**Reverse Gear**
The quality threshold at which a loop drops from autonomous back to reviewed.

**Stop Condition**
When the workflow does not beat baseline or corrections never converge.
```

---

## Audit Mode

Task: Evaluate an existing agent/workflow setup against the operating model.

Audit checklist:
- Is there a workflow graph, or just a pile of isolated agents?
- Does each loop have a human owner?
- Is each trigger clear?
- Is each loop tied to a business goal?
- Does each loop have a real verifier (definition of done)?
- Is autonomy justified by verifier strength (no verifier → no autonomy)?
- Are allowed and forbidden actions explicit?
- Is the runner swappable, or is the process locked to one vendor's runtime?
- Is there a routing and escalation path with a human owner on risky branches?
- Are runs traced (trigger, context, runner, output, verifier, outcome)?
- Are corrections captured and fed back into the loops?
- Is there a reverse gear when quality drops?
- Are there duplicate loops solving the same step?

Output:
- Red flags
- Missing verifiers
- Missing owners
- Runner lock-in
- Unsafe autonomy
- Broken or missing escalation
- Uncaptured corrections (the biggest hidden loss)
- Recommended merges, cuts, and redesigns

---

## Common Workflows And Their Loops

Use these as starting points, not defaults. Each is a workflow (chain of loops), not a single agent.

| Workflow | Loops (chain) | Useful When | Usually Avoid If |
|---|---|---|---|
| Customer evidence | gather → summarize → tag → human review → route | Insights trapped in calls/support/Slack | No one labels decisions |
| Support resolution | classify → retrieve context → draft → policy check → human approve → send | Volume hides patterns and urgency | Knowledge base is stale |
| Renewal prep | research account → analyze risk → draft rec → human review → follow-up → update CRM | Renewals slip through cracks | Usage/CRM data is missing |
| Engineering delivery | issue intake → plan → code → test → review → merge | Bug/feature flow is inconsistent | No tests or owner |
| Client research | gather data → summarize → check claims → human edit → deliver | Deliverables need consistency | Quality criteria are subjective |
| Outbound | account research → draft personalized outreach → human approve → send | Founder-led sales needs context | User wants unsupervised spam |
| Compliance packet | gather questions → draft answers → legal review → deliver | Enterprise sales stalls on security | Answers require legal sign-off every time |

---

## Anti-Patterns

- Designing a pile of agents instead of a workflow graph.
- Building a "chief of staff agent" before defining the loops and workflow it owns.
- Giving a loop autonomy before it has a verifier.
- Locking a workflow to one vendor's runtime instead of keeping runners swappable.
- Automating a broken process instead of simplifying it first.
- Treating human input as failure instead of the normal management chain.
- Letting a loop fail silently without a resolver path.
- Throwing away corrections (keeping chat history but not the learnings).
- Measuring token usage or agent count instead of accepted outcomes and corrections.
- Optimizing speed alone (rubber-stamping) or automation alone (bad work ships).
- Creating one agent per human job title.
