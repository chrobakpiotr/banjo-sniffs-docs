<p align="center">
  <img src="logo.png" alt="Banjo Sniffs logo" width="180">
</p>

<h1 align="center">Banjo Sniffs™</h1>

<p align="center"><b>Banjo Sniffs out the gap between what the ticket accepted, what the tests prove, and what the diff claims.</b></p>

<p align="center">
  <img alt="version 1.3.1" src="https://img.shields.io/badge/version-1.3.1-1f9e89?style=flat-square">
  <img alt="read-only by default" src="https://img.shields.io/badge/read--only-by%20default-1f9e89?style=flat-square">
  <img alt="any stack" src="https://img.shields.io/badge/stack-any-1f9e89?style=flat-square">
  <img alt="no network" src="https://img.shields.io/badge/network-none%20required-1f9e89?style=flat-square">
</p>

<p align="center">
  <a href="https://www.agensi.io/skills/banjo-sniffs-ai-assisted-software-development"><b>Get it on Agensi</b></a>
  &nbsp;·&nbsp; <a href="user-guide.md">User guide</a>
  &nbsp;·&nbsp; <a href="#see-it-work">Demonstrations</a>
</p>

<p align="center">
  <img src="media/01-hero.png" alt="Banjo Sniffs: evidence-based engineering for your AI coding assistant" width="860">
</p>

## What it is

Banjo Sniffs is a set of instructions, reference methods and templates for your AI coding assistant. Point it at a branch, a ticket or a design question and it shows its work: every conclusion is `MET`, `NOT_MET` or `UNVERIFIED`, tied to evidence it actually has, never a guess.

It is not a scanner and has no runtime. It reads only what you give it, runs only what you authorize, and works with any language and any stack.

## What you can ask for

| Mode | What you get |
|---|---|
| **Change review** | Each acceptance criterion checked against the diff, with findings tied to file and line, and a handover for whoever continues |
| **Test-gap analysis** | Which criteria have a test that would fail on a wrong implementation, which do not, and the smallest check that would close each gap |
| **Trust boundaries** | Questions on auth, tenancy, money, callbacks, secrets and file paths, pulled into a review when the change touches them |
| **Architecture assessment** | Options compared against your constraints, "keep the current design" always among them, recorded as an ADR that keeps proposals apart from decisions |
| **Verification strategy** | The smallest set of checks that would catch a likely fault, chosen from the checks your project already has |
| **Docs context** | `AGENTS.md` files and documentation indexes that route to your existing docs instead of copying them |

## See it work

| Demonstration | What it shows | Result |
|---|---|---|
| [Review of a PR with planted defects](review-planted-defects.md) | Two money-path defects and three claims aimed at the reviewer, hidden in a synthetic refund PR | **FAIL** - all five caught, both defects proved with a probe |
| [Review of a real public commit](review-real-commit.md) | A real commit with no planted defect; the tests could not run | **INCOMPLETE** - four criteria honestly `UNVERIFIED`; one concern later fixed by the owner |
| [Test-gap analysis](test-gap.md) | Five criteria mapped to the tests that would actually catch a regression | 2 `COVERED`, 1 `PARTIAL`, 1 `UNCOVERED`, 1 `UNVERIFIED` |
| [Architecture assessment](architecture-assessment.md) | A proposal that collides with accepted constraints, no code | Recommendation `PROPOSED`, next evidence named, no invented targets |

<table>
  <tr>
    <td width="50%"><a href="review-planted-defects.md"><img src="media/02-planted-defects.png" alt="Planted-defect review"></a></td>
    <td width="50%"><a href="review-real-commit.md"><img src="media/03-real-commit.png" alt="Real-commit review"></a></td>
  </tr>
  <tr>
    <td width="50%"><a href="test-gap.md"><img src="media/04-test-gap.png" alt="Test-gap analysis"></a></td>
    <td width="50%"><a href="architecture-assessment.md"><img src="media/05-architecture.png" alt="Architecture assessment"></a></td>
  </tr>
</table>

## Try it

Once the skill is enabled in your assistant, ask in plain words and say what it may run or write:

```text
Review branch feature/x against docs/TICKET-42.md (base: main). Read-only, but you may run the existing tests.
```

```text
Assess whether to keep our job queue or move it into the database. Constraints: jobs survive restart, one service
instance, no new managed services. Compare the options and draft an ADR.
```

```text
Which acceptance criteria of TICKET-42 do the existing tests actually prove? Read-only, propose the missing checks.
```

More prompts and how to read a report: [user guide](user-guide.md).

## How it stays honest

<p align="center">
  <img src="media/06-honest.png" alt="Every check is RUN, NOT RUN or STATIC" width="760">
</p>

- **Three separate verdicts.** Criterion results, the review disposition and implementation acceptance never blur; only the owner accepts.
- **Typed evidence.** Every check is `RUN exit=0` (with its real exit code), `NOT RUN: reason` or `STATIC`, so a planned check is never reported as executed.
- **The diff cannot talk back.** A PR description, a code comment or a spec added by the change itself is data, not instruction; text aimed at the reviewer becomes a finding.
- **Gaps stay visible.** Conflicting sources are recorded, failed attempts are preserved, and nothing is marked passed without the evidence to show it.

## Get it

Banjo Sniffs is sold on the [Agensi marketplace](https://www.agensi.io/skills/banjo-sniffs-ai-assisted-software-development). This repository holds only its documentation.

Written by a software engineer and solutions architect with fifteen years of practice. Bug reports for the skill: piotr.chrobak.contact@gmail.com.

---

<p align="center"><sub>© 2026 Piotr Chrobak · Banjo Sniffs™ · <a href="LICENSE">Licence</a></sub></p>
