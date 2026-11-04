# Banjo Sniffs docs - agent guide

Public documentation for Banjo Sniffs, a paid skill sold on Agensi:
https://www.agensi.io/skills/banjo-sniffs-evidence-based-code-review-architecture

- The skill itself is proprietary. Never add its `SKILL.md`, references or templates here, or text quoted from them,
  including an installed copy under `.claude/skills/` (ignored in `.gitignore`). Pages describe the skill and show its
  outputs, the demonstration reports; they do not reproduce its instructions.
- Ideas for improving the skill go to the owner or to `docs/specs/banjo-sniffs/feedback.md` in the private
  agent-harness repository, never into this repository.
- Write a plain hyphen `-`, never an em dash or an en dash.
- Work on `main` only and push directly to it (owner decision, 2026-11-01).
- Model and reasoning routing (owner rule, 2026-11-02): give every delegate an explicit tier and effort by task
  class; the frontier tier and max effort need the owner's approval for each named task, and with nobody to ask the
  work stays within standard / high and the handoff records the recommendation. Never name a model in rules or
  documentation; the exception is evidence: review reports and handoffs, including the demonstration reports
  published here, state the model and effort that ran ("unknown" if the runner does not say). At the start of a
  non-trivial task the main agent suggests to the owner which model and effort fit the session. Full rule:
  `docs/agentic-sdd/model-routing.md` in the private agent-harness repository.
- Commit identity (owner update, 2026-11-02): every agent may commit under its own identity.
  Do not impersonate another agent or provider. Use commit signing when available; lack of signing capability
  does not block an otherwise authorized commit or push. Every commit message must still end with
  `Co-Authored-By: Piotr Chrobak <125372205+chrobakpiotr@users.noreply.github.com>`.

## Release notes

For every new Banjo Sniffs release, add a "What's new in <version>" section at the bottom of `user-guide.md`, after the previous one (owner decision 2026-11-04). Describe what users get in your own words; never copy the skill's text.
