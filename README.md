# Codex Agent Org Designer Skill

Design the AI agents your company actually needs before you automate the wrong work.

This Codex skill helps founders, operators, and technical teams decide what internal agents to build, what each agent should own, how much autonomy it should have, when it should escalate to humans, and how to roll it out safely.

The opinion behind the skill is simple:

> Do not design "digital employees." Design owned operational loops.

## What It Does

- Finds the company bottlenecks where agents can create real leverage
- Turns messy workflows into agentable loops
- Designs agent portfolios and priority order
- Writes implementation-ready agent role charters
- Defines autonomy levels, forbidden actions, and human owners
- Maps handoffs between agents, employees, teams, and escalation paths
- Creates 14-30 day rollout plans with metrics and stop conditions
- Audits existing agents for overlap, missing owners, unsafe autonomy, and weak evals

## The Agent Design Canvas

Every useful agent needs this before it gets built:

```text
Outcome
Trigger
Inputs
Tools
Allowed actions
Forbidden actions
Human owner
Autonomy level
Escalation rule
Success metric
Trace
Eval
```

If you cannot fill this out, you are not ready to build the agent.

## Why This Exists

Most companies start with the wrong question:

```text
What AI agents should we hire?
```

The better question is:

```text
Where does our operating system lose momentum, and what owned loop could an agent improve?
```

This skill uses systems thinking, jobs-to-be-done, theory of constraints, RACI-style ownership, autonomy ladders, and routing design to answer that question in a practical way.

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

Agent portfolio:

```text
Use $agent-org-designer to design the first internal agents for our seed-stage B2B SaaS company.

Context:
- 8 people
- Founder-led sales
- 25 customer calls per month
- Product feedback is scattered across Gong, Slack, Linear, and Notion
- Biggest bottleneck is turning calls into product and sales follow-up
```

Single role charter:

```text
Use $agent-org-designer to write a role charter for a Customer Evidence Agent that works with sales calls, support tickets, and product feedback.
```

Routing map:

```text
Use $agent-org-designer to design a routing map for agents that work alongside sales, support, product, and engineering.
```

Audit:

```text
Use $agent-org-designer to audit our current internal agent setup. We have a sales research agent, meeting notes agent, support triage agent, and engineering triage agent.
```

## Modes

- `diagnosis`: identify where agents could accelerate the company
- `portfolio`: design the agent portfolio and priority order
- `charter`: write detailed role charters for one or more agents
- `routing-map`: define handoffs between agents, humans, teams, and escalation paths
- `rollout`: create a 14-30 day pilot plan
- `audit`: review an existing internal-agent setup
- `full`: compact diagnosis, portfolio, top charters, routing, and rollout

## Default Output

Codex will return:

```text
Verdict
Company Bottleneck Read
Agent Portfolio
Top Role Charters
Routing And Escalation
14-Day Pilot
```

Each agent is designed as:

```text
trigger -> inspect context -> decide/act -> produce output -> trace outcome -> escalate when needed
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

## Repository Structure

```text
agent-org-designer/
  SKILL.md
  agents/openai.yaml
  references/playbooks.md
scripts/
  install.js
examples/
  seed-b2b-saas-output.md
LAUNCH.md
```

## Inspired By

The installable package shape is inspired by the public Codex skill pattern used in [codex-startup-pressure-test-skill](https://github.com/Kappaemme-git/codex-startup-pressure-test-skill). The agent design framework and playbooks in this repo are original.

## License

MIT
