# Codex Agent Org Designer Skill

Plan and run the hybrid-workforce operating model — before you automate the wrong work.

This Codex skill helps founders, operators, and technical teams design how AI agents and humans work together: not as a pile of "digital employees," but as **workflows made of loops**, run by swappable runners, gated by verifiers, and improved by corrections.

The opinion behind the skill:

> Companies will not manage prompts or individual agents. They will manage workflows made of loops, run by agents and humans, improved by corrections.

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

## The Operating Model In One Line

> Agents run the loops. Humans resolve the judgment. The workflow improves after every run.

## What It Does

- Maps a business goal into a **workflow graph** of connected loops
- Designs each loop: trigger, context, runner, output, verifier, human input, escalation, owner, metric, trace
- Assigns **swappable runners** (Claude, Codex, Claude Code, Cowork, OpenClaw, Copilot, internal agents, or humans) per loop
- Sets autonomy from **verifier strength** — no verifier, no autonomy
- Routes **human input** as the normal management chain, with escalation paths
- Gives execution templates (work packets/runs and a correction log) so you can *run* the workflow, not just plan it
- Captures **corrections** as the compounding moat and feeds them back into the loops
- Builds 14-30 day rollout plans with a reverse gear and stop conditions
- Audits existing setups for missing verifiers, runner lock-in, unsafe autonomy, broken escalation, and uncaptured corrections

## The Eight Core Elements

```text
Goal          the business outcome (throughput, quality, speed, cost, learning)
Workflow      the full process connecting loops, agents, humans, approvals
Loop          a reusable job description for one part of the workflow
Runner        what executes a loop (any agent or a human) — replaceable
Work packet   one run of a loop, carrying context, output, status, owner, history
Verifier      the definition of done — no verifier, no autonomy
Human input   the normal management chain when stuck, risky, or judgment-heavy
Correction    the learning captured from human judgment — the compounding moat
```

If you cannot fill out a loop's trigger, context, runner, output, verifier, owner, and escalation, you are not ready to run it.

## Why This Exists

Most companies start with the wrong question:

```text
What AI agents should we hire?
```

The better question is:

```text
What company process is slow, repeated, and valuable — and which loops can an agent run, which need a human, and what proves each step is done?
```

The company process does not belong to any one agent vendor. OpenAI owns OpenAI runs. Anthropic owns Claude runs. Microsoft owns Copilot runs. **The company owns the workflow.** This skill designs and runs that workflow so runners stay swappable and corrections compound.

## Load-Bearing Rules

1. Design workflows first, agents second.
2. Loops outlive runners — keep the runner swappable.
3. No verifier, no autonomy.
4. Human attention is the scarce resource — spend it where judgment changes the outcome.
5. Escalation is part of the process, not an exception.
6. Corrections become the moat.
7. Humans hold accountability; agents own throughput.

## Installation

```bash
npx --yes codex-agent-org-designer-skill@latest
```

This installs the skill into:

```text
~/.codex/skills/agent-org-designer
```

Restart Codex so it can discover the skill.

## Usage

Map a workflow (primary planning mode):

```text
Use $agent-org-designer to map the customer-evidence workflow for our seed-stage B2B SaaS company.

Context:
- 8 people
- Founder-led sales
- 25 customer calls per month
- Product feedback scattered across Gong, Slack, Linear, Notion
- Runners available: Claude, Codex, Cowork; humans: founder + head of product
- Biggest bottleneck: turning calls into product and sales follow-up
```

Design a single loop:

```text
Use $agent-org-designer in loop-design mode to write a loop card for synthesizing customer evidence from calls and support threads, including the verifier and escalation.
```

Assign runners:

```text
Use $agent-org-designer in runner-assignment mode to choose runners and autonomy levels for each loop in our support-resolution workflow.
```

Execute a run:

```text
Use $agent-org-designer in run mode to create work packets for the renewal-prep workflow and track verifier results and human input.
```

Capture corrections:

```text
Use $agent-org-designer in correction-log mode to turn this week's human edits and stuck steps into loop improvements.
```

Audit:

```text
Use $agent-org-designer in audit mode to review our current setup: a sales research agent, meeting notes agent, support triage agent, and engineering triage agent. Check verifiers, owners, runner lock-in, and uncaptured corrections.
```

## Modes

Planning:

- `diagnosis`: find slow, repeated, valuable processes where loops create leverage
- `workflow-map`: turn a goal into a workflow graph of connected loops (primary planning mode)
- `loop-design`: write detailed loop cards
- `runner-assignment`: choose runners per loop and set autonomy from verifier strength
- `routing-map`: define handoffs, human-input items, and escalation paths
- `rollout`: 14-30 day pilot plan with a reverse gear

Execution:

- `run`: instantiate work packets and move them through loops
- `correction-log`: capture corrections and turn them into loop improvements

Review:

- `audit`: review an existing agent/workflow setup against the operating model
- `full`: compact diagnosis, workflow map, top loop cards, runner assignment, routing, and rollout

## Default Output

Codex will return:

```text
Verdict
Goal And Bottleneck Read
Workflow Graph
Loop Cards
Routing And Escalation
14-Day Pilot
```

Each loop is designed as:

```text
trigger -> context -> runner -> output -> verifier -> done or human input -> correction
```

## Repository Structure

```text
agent-org-designer/
  SKILL.md
  agents/openai.yaml
  references/playbooks.md   (planning + execution playbooks, run + correction templates)
scripts/
  install.js
examples/
  seed-b2b-saas-output.md  (workflow-graph example)
LAUNCH.md
```

## Manual Installation

Clone the repository:

```bash
git clone https://github.com/kvergins/codex-agent-org-designer-skill.git
```

Copy the skill into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R codex-agent-org-designer-skill/agent-org-designer ~/.codex/skills/agent-org-designer
```

Restart Codex.

## Inspired By

The installable package shape is inspired by the public Codex skill pattern used in [codex-startup-pressure-test-skill](https://github.com/Kappaemme-git/codex-startup-pressure-test-skill). The workflow operating model and playbooks in this repo are original.

## License

MIT
