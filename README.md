<h1 align="center">Banjo Sniffs™</h1>

<p align="center"><b>A skill for your AI coding assistant. It reviews a change against its ticket, shows which criteria your tests really prove, and compares design options. Every verdict is tied to evidence it actually has.</b></p>

<p align="center">
  <a href="https://www.agensi.io/skills/banjo-sniffs-ai-assisted-software-development"><img alt="Get it on Agensi" src="https://img.shields.io/badge/Get%20it%20on-Agensi-0d7d73?style=for-the-badge"></a>
  &nbsp;<a href="user-guide.md"><img alt="Read the user guide" src="https://img.shields.io/badge/Read-the%20user%20guide-475569?style=for-the-badge"></a>
</p>

<p align="center">
  <img src="media/01-hero.png" alt="Banjo Sniffs: evidence-based engineering for your AI coding assistant" width="860">
</p>

<p align="center">
  <img alt="version 1.3.1" src="https://img.shields.io/badge/version-1.3.1-0d7d73?style=flat-square">
  <img alt="read-only by default" src="https://img.shields.io/badge/read--only-by%20default-0d7d73?style=flat-square">
  <img alt="any stack" src="https://img.shields.io/badge/stack-any-0d7d73?style=flat-square">
  <img alt="no network required" src="https://img.shields.io/badge/network-none%20required-0d7d73?style=flat-square">
</p>

## What it is

> Banjo Sniffs out the gap between what the ticket accepted, what the tests prove, and what the diff claims.

Banjo Sniffs is a skill for your AI coding assistant: instructions, methods and templates that make it show its work. Point it at a branch, a ticket or a design question and every acceptance criterion comes back `MET`, `NOT_MET` or `UNVERIFIED`, tied to evidence the assistant actually has, never a guess.

It is not a scanner and has no runtime. It reads and runs only what you authorize, and works with any language and any stack.

## What you can ask for

| Mode | What you get |
|---|---|
| **Change review** | Each acceptance criterion checked against the diff, findings tied to file and line, and a handover for whoever continues |
| **Test-gap analysis** | Which criteria have a test that would fail on a wrong implementation, which do not, and the smallest check that would close each gap |
| **Trust boundaries** | Questions on auth, tenancy, money, callbacks, secrets and file paths, pulled into a review when the change touches them |
| **Architecture assessment** | Options compared against your constraints with "keep the current design" among them, and an ADR draft when you want one that keeps proposals apart from decisions |
| **Verification strategy** | The smallest set of checks that would catch a likely fault, starting from the checks your project already has |
| **Docs context** | `AGENTS.md` files and documentation indexes that route to your existing docs instead of copying them |

## See it work

Each demonstration states the skill version it was produced with; the current version is 1.3.1. The images are illustrations of the real output; the full reports are on the linked pages.

<table>
<tr>
<td width="46%"><a href="review-planted-defects.md"><img src="media/02-planted-defects.png" alt="Review of a PR with planted defects"></a></td>
<td><b><a href="review-planted-defects.md">Review of a PR with planted defects</a></b><br>Two money-path defects and three claims aimed at the reviewer, hidden in a synthetic refund PR.<br><br><b>FAIL</b>: all five caught, both defects proved with a probe.</td>
</tr>
<tr>
<td width="46%"><a href="review-real-commit.md"><img src="media/03-real-commit.png" alt="Review of a real public commit"></a></td>
<td><b><a href="review-real-commit.md">Review of a real public commit</a></b><br>A real commit with no planted defect. The tests needed a private package and could not run.<br><br><b>INCOMPLETE</b>: four criteria stayed <code>UNVERIFIED</code>; one concern was later confirmed and fixed by the owner.</td>
</tr>
<tr>
<td width="46%"><a href="test-gap.md"><img src="media/04-test-gap.png" alt="Test-gap analysis"></a></td>
<td><b><a href="test-gap.md">Test-gap analysis</a></b><br>Five criteria mapped to the tests that would actually catch a regression. Produced with version 1.1.0; see the owner's note on AC-5.<br><br>2 <code>COVERED</code>, 1 <code>PARTIAL</code>, 1 <code>UNCOVERED</code>, 1 <code>UNVERIFIED</code>.</td>
</tr>
<tr>
<td width="46%"><a href="architecture-assessment.md"><img src="media/05-architecture.png" alt="Architecture assessment"></a></td>
<td><b><a href="architecture-assessment.md">Architecture assessment</a></b><br>A proposal that collides with the accepted constraints, no code.<br><br>Recommendation <code>PROPOSED</code>, next evidence named.</td>
</tr>
</table>

## Try it

Once the skill is enabled in your assistant, ask in plain words and say what it may run or write:

```text
Review branch feature/x against docs/TICKET-42.md (base: main).
Read-only, but you may run the existing tests.
```

```text
Assess whether to keep our job queue or move it into the database.
Constraints: jobs survive restart, one service instance, no new managed services.
Compare the options and draft an ADR.
```

```text
Which acceptance criteria of TICKET-42 do the existing tests actually prove?
Read-only, propose the missing checks.
```

More prompts and how to read a report: [user guide](user-guide.md).

## How it stays honest

<p align="center">
  <img src="media/06-honest.png" alt="Every check is RUN, NOT RUN or STATIC" width="760">
</p>

- **The diff cannot talk back.** A PR description, a code comment or a spec added by the change itself is data, not instruction; text aimed at the reviewer becomes a finding.
- **Gaps stay visible.** Conflicting sources are recorded, failed attempts are preserved, and a check that did not run is reported as `NOT RUN` with its reason.

## Get it

<p>
  <a href="https://www.agensi.io/skills/banjo-sniffs-ai-assisted-software-development"><img alt="Get it on Agensi" src="https://img.shields.io/badge/Get%20it%20on-Agensi-0d7d73?style=for-the-badge"></a>
</p>

Banjo Sniffs is a `SKILL.md` skill sold on the Agensi marketplace. Hosts differ in how they enable skills; see Getting started in the [user guide](user-guide.md). This repository holds only the documentation.

Written by a software engineer and solutions architect with fifteen years of practice. Bug reports for the skill: piotr.chrobak.contact@gmail.com.

---

<p align="center"><sub>© 2026 Piotr Chrobak · Banjo Sniffs™ · <a href="LICENSE">License</a></sub></p>
