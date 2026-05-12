# Agent Org Designer Playbooks

Use these playbooks when the user asks for a specific mode, deep design work, or reusable templates.

## Diagnosis Mode

Role: Act as an operating-system designer for the company.

Task: Find the highest-leverage places where agents can accelerate progress without creating hidden operational risk.

Steps:
- Identify the company's current goals and bottlenecks.
- Map slow recurring loops: sales, product learning, support, delivery, finance, recruiting, ops, compliance, engineering.
- Separate "humans are overloaded" from "the process is unclear".
- Find loops with accessible context, repeatable decisions, and clear escalation.
- Give a direct recommendation on the first 1-3 agents to build.

Output:
- Company bottleneck read
- Agentable loops
- Non-agent problems
- First 3 agents
- What not to automate yet

## Portfolio Mode

Task: Design a prioritized portfolio of agents for a company or team.

Prioritize with this order:
1. Revenue or customer-learning speed.
2. Repeated human bottlenecks.
3. High-frequency internal coordination.
4. Work where output quality can be checked.
5. Work with clean escalation paths.

Portfolio table:

| Priority | Agent | Job | Trigger | Human Owner | Autonomy | Why Now | Metric |
|---:|---|---|---|---|---|---|---|
| 1 | ... | ... | ... | ... | L1-L3 | ... | ... |

Now / next / later:
- Now: 1-2 agents that can be piloted in 14 days.
- Next: useful after the first agents create traces and baseline data.
- Later: broad, high-risk, or strategically tempting agents that need more process maturity.

## Charter Mode

Task: Turn a candidate agent into an implementation-ready role.

Agent charter template:

```markdown
### Agent Name

**One-line job**
...

**Outcome**
The measurable business or operational result this agent exists to improve.

**Trigger**
When the agent runs: scheduled, event-driven, human-invoked, or routed by another agent.

**Inputs**
Documents, tickets, CRM records, product analytics, emails, calls, code, databases, or APIs.

**Tools**
Systems the agent can read from and write to.

**Allowed actions**
Specific actions the agent may take.

**Forbidden actions**
Specific actions that require humans or are out of scope.

**Autonomy level**
L0-L5, with reason.

**Human owner**
The person accountable for quality and business outcome.

**Escalates when**
Ambiguity, risk, missing context, low confidence, policy breach, or strategic importance.

**Success metric**
One primary metric and one quality metric.

**Trace**
What must be logged: trigger, context used, decision, output, resolver, outcome, label.

**Eval**
How humans judge quality and how often.
```

## Routing Map Mode

Task: Define how agents work alongside humans and route work when stuck.

Resolver types:
- Agent
- Human owner
- Team queue
- Escalation path
- External system

Routing table:

| Intent/Event | Primary Resolver | Backup Resolver | Timeout | Escalation Rule | Trace Required |
|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | yes |

Rules:
- Every high-risk route needs a human owner.
- Timeouts must have a backup path.
- Agents should escalate uncertainty before acting silently.
- Repeated escalations are a signal to improve tools, data, policy, or the role charter.

## Rollout Mode

Task: Build a 14-30 day implementation plan that validates one or two agent roles before expansion.

Plan shape:

```markdown
**Pilot Goal**
...

**Scope**
- Build:
- Cut:
- Human owner:
- Users:

**Baseline**
Current time, cost, cycle time, error rate, backlog, response time, or missed opportunity.

**Instrumentation**
Trace every trigger, context source, output, human edit, escalation, and accepted outcome.

**Week 1**
- Charter
- Access
- Golden examples
- First dry runs

**Week 2**
- Run on real work with human approval
- Label outputs
- Compare against baseline
- Decide: expand, revise, or stop

**Success Bar**
...

**Stop Condition**
...
```

## Audit Mode

Task: Evaluate existing agents and find design flaws.

Audit checklist:
- Does each agent have a human owner?
- Is the trigger clear?
- Is the output tied to a company bottleneck?
- Are allowed and forbidden actions explicit?
- Is the autonomy level appropriate for risk?
- Are tools and data sources sufficient?
- Is there a routing or escalation path?
- Are decisions and outcomes traced?
- Is quality evaluated against examples or labels?
- Are there duplicate agents solving the same loop?

Output:
- Red flags
- Duplicate or overlapping roles
- Missing owners
- Unsafe autonomy
- Missing evals
- Recommended merges, cuts, and redesigns

## Common Startup Agent Roles

Use these as starting points, not defaults.

| Agent | Useful When | Usually Avoid If |
|---|---|---|
| ICP Research Agent | Founder needs more qualified customer conversations | ICP is still vague |
| Discovery Prep Agent | Calls happen but prep is inconsistent | There are too few calls |
| Call Synthesis Agent | Insights are trapped in notes and recordings | No one labels decisions |
| Product Feedback Triage Agent | Feedback is scattered across calls, support, Slack, issues | Product owner will ignore it |
| Outbound Prep Agent | Founder-led sales needs personalized context | User wants unsupervised spam |
| Support Triage Agent | Support volume hides patterns and urgency | Knowledge base is stale |
| Delivery QA Agent | Customer deliverables need consistency | Quality criteria are subjective |
| Ops Watcher Agent | Follow-ups and decisions go stale | No one owns the escalation queue |
| Engineering Triage Agent | Bugs, logs, and customer reports need sorting | Codebase has no tests or owner |
| Compliance Packet Agent | Enterprise sales stalls on security/audit answers | Answers require legal approval |

## Anti-Patterns

- Building a "chief of staff agent" before defining the loops it owns.
- Giving agents broad write access before evals exist.
- Automating a broken process instead of simplifying it.
- Measuring token usage instead of accepted outcomes.
- Treating agents as headcount replacements instead of throughput multipliers.
- Creating one agent per human job title.
- Letting agents fail silently without a resolver path.
