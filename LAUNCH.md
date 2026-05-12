# Launch Kit

Use this when publishing the repo.

## GitHub Description

Design the AI agents your company actually needs before automating the wrong work.

## GitHub Topics

```text
codex
codex-skill
ai-agents
agentic-workflows
agent-design
startup
automation
future-of-work
operating-system
ai-ops
```

## Short Launch Post

Most teams are asking the wrong question:

"What AI agents should we hire?"

The better question is:

"Where does our operating system lose momentum, and what owned loop could an agent improve?"

I built Agent Org Designer, a Codex skill that helps teams design useful AI agent roles before they automate the wrong work.

It turns company bottlenecks into:
- agent portfolios
- role charters
- autonomy boundaries
- routing and escalation maps
- 14-day rollout plans

Repo: https://github.com/kvergins/codex-agent-org-designer-skill

## Hacker News Title Options

- Show HN: A Codex skill for designing useful AI agent roles
- Show HN: Agent Org Designer, a skill for deciding what agents a company should build
- Show HN: Design AI agents from company bottlenecks, not job titles

## Longer Launch Post

The mistake I keep seeing with internal AI agents:

Companies design them like fake employees.

They make a "CEO agent", "analyst agent", "chief of staff agent", or "sales agent" before defining the actual operating loop the agent owns.

That creates impressive demos and messy operations.

The better pattern is:

```text
trigger -> inspect context -> decide/act -> produce output -> trace outcome -> escalate when needed
```

So I built Agent Org Designer, a Codex skill that helps a team answer:

- Which agents should we build first?
- What should each agent own?
- How autonomous should it be?
- What actions are forbidden?
- Who is the human owner?
- When should it escalate?
- How do we know it is working?

It is intentionally opinionated: agents should own throughput, not final accountability.

Install:

```bash
npx --yes codex-agent-org-designer-skill@latest
```

Repo: https://github.com/kvergins/codex-agent-org-designer-skill

## First Issue Ideas

- Add more example outputs for support, sales, product, engineering, and operations teams
- Add an enterprise-agent audit example
- Add a checklist for deciding whether an agent should be L1, L2, or L3 autonomy
- Add example prompts for founder-led sales, customer success, recruiting, and engineering teams
