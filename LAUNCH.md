# Launch Kit

Use this when publishing the repo.

## GitHub Description

Plan and run the hybrid-workforce operating model: workflows made of loops, run by swappable agents and humans, improved by corrections.

## GitHub Topics

```text
codex
codex-skill
ai-agents
agentic-workflows
hybrid-workforce
workflow-design
human-in-the-loop
agent-orchestration
automation
future-of-work
ai-ops
```

## Short Launch Post

Most teams are asking the wrong question:

"What AI agents should we hire?"

The better question:

"What process is slow, repeated, and valuable — and which loops can an agent run, which need a human, and what proves each step is done?"

The company process does not belong to any one agent vendor. OpenAI owns OpenAI runs. Anthropic owns Claude runs. The company owns the workflow.

I built Agent Org Designer, a Codex skill that helps teams plan AND run that workflow.

It turns a business goal into:
- a workflow graph of loops
- loop cards (trigger, context, runner, output, verifier, escalation)
- swappable runners (Claude, Codex, Cowork, OpenClaw, Copilot, internal, or human)
- routing and human-input paths
- work-packet/run templates and a correction log
- 14-day rollout plans with a reverse gear

Repo: https://github.com/kvergins/codex-agent-org-designer-skill

## Hacker News Title Options

- Show HN: A Codex skill for designing and running hybrid human-agent workflows
- Show HN: Agent Org Designer — workflows made of loops, not a pile of AI employees
- Show HN: Plan and run AI work as loops with verifiers and corrections

## Longer Launch Post

The mistake I keep seeing with internal AI:

Companies build a pile of agents — a "CEO agent", "analyst agent", "chief of staff agent" — before defining the actual process those agents run inside.

That creates impressive demos and messy operations.

The better model: companies will not manage prompts or individual agents. They will manage **workflows made of loops**, run by agents and humans, improved by corrections.

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

The runner is replaceable. The loop and its correction history persist. That is why you can swap Claude for Codex, OpenClaw, Copilot, an internal model, or a human without losing the process.

So I built Agent Org Designer, a Codex skill that helps a team answer:

- What workflow are we actually running?
- Which agent or human owns each loop?
- What proves each step is done (the verifier)?
- When does a loop ask a human for input?
- Where did the workflow get stuck?
- What correction improves the next run?

It is intentionally opinionated:
- No verifier, no autonomy.
- Loops outlive runners.
- Human attention is the scarce resource.
- Corrections are the compounding moat.

And it ships execution templates — work packets and a correction log — so you can run the workflow, not just diagram it.

Install:

```bash
npx --yes codex-agent-org-designer-skill@latest
```

Repo: https://github.com/kvergins/codex-agent-org-designer-skill

## First Issue Ideas

- Add workflow-graph examples for support, sales, product, engineering, and operations
- Add an enterprise audit example focused on missing verifiers and runner lock-in
- Add a decision checklist for moving a loop up the autonomy ladder (and the reverse-gear trigger)
- Add a correction-log starter that converts a week of human edits into loop upgrades
- Add example runs (work packets) for founder-led sales, customer success, and engineering
