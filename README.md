# Orchestra

Agent-agnostic harness for orchestrating multiple AI coding
agents in production, with a human review gate on every change.

> Orchestra Core is in active private development and daily use on [orchestra-core](https://github.com/imdela/orchestra-core).

## Why

Multi-agent coding pipelines fail in specific, recurring ways: agents drift
from stated rules under context pressure, take forbidden shortcuts even when
the correct path is known, and produce diffs that look plausible but weren't
checked against the same standard a human's code would be. Orchestra exists
to make those failure modes visible and reviewable, not to make agents faster.

## How it works

- **Pilot/executor pattern.** Claude Code runs as pilot; OpenCode and
  DeepSeek run as executors.
- **Strict layer separation.** Agents don't cross into layers they weren't
  assigned.
- **Dependency-gated task status.** A task can't move forward until its
  declared dependencies are actually satisfied, not just claimed as done.
- **Enforced response format.** Every agent turn follows
  ANALYSIS → PLAN → EXECUTION → VERIFICATION.
- **Human review gate.** Every diff, from every agent, is reviewed before
  merge — the same standard as human-written code.

## Roadmap

- [x] Core harness (pilot/executor pattern, layer separation, review gate)
- [ ] AIOps / incident-response module (ITIL-encoded incident model, wired
      to Prometheus + PagerDuty)
- [ ] Public interface stubs/example configuration

## Related writing

Findings from running this in production are written up on the
[Harness Engineering series](https://log.delaa.dev) — including agents
breaking their own rules under context pressure, and a controlled
comparison of Spec Kit, BMAD and OpenSpec.

## Status

Implementation is private while the harness is still changing shape.
This repo tracks the public-facing design and roadmap. Follow the blog
for progress; the code moves here once it's stable enough to support
outside use.
