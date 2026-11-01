<p align="center">
  <a href="README.md"><img src="logo.png" alt="Banjo Sniffs logo" width="120"></a>
</p>

<p align="center">
  <a href="README.md">Home</a> &nbsp;·&nbsp; <b>User guide</b> &nbsp;·&nbsp; <a href="review-planted-defects.md">Planted-defect review</a> &nbsp;·&nbsp; <a href="review-real-commit.md">Real-commit review</a> &nbsp;·&nbsp; <a href="test-gap.md">Test-gap analysis</a> &nbsp;·&nbsp; <a href="architecture-assessment.md">Architecture assessment</a> &nbsp;·&nbsp; <a href="https://www.agensi.io/skills/banjo-sniffs-ai-assisted-software-development"><b>Get it on Agensi</b></a>
</p>

---

# User guide

<sub>Banjo Sniffs 1.3.1</sub>

> Banjo Sniffs out the gap between what the ticket accepted, what the tests prove, and what the diff claims.

Banjo Sniffs guides an engineering assistant through evidence-based software work. It supplies instructions, optional methods, and adaptable templates. It does not provide a runtime or grant access to your project, tools, or services.

## Choose a mode

- **Change review:** Compare a delivered change with accepted requirements and project context. Reviews are read-only by default. Requested review reports are allowed; implementation edits, commits, dependency installs, and deployment need separate authorization.
- **Test-gap analysis:** Map accepted criteria to the checks that already exist (`COVERED`, `PARTIAL`, `UNCOVERED`, `UNVERIFIED`), rank the gaps by risk, and get the smallest proposed check for each. Static by default; tests are proposed, not written.
- **Security and trust boundaries:** During a review that touches authentication, authorization, tenancy, money, callbacks, secrets, or file paths, the assistant also works through a set of questions to falsify with pointers; it is not a scanner and makes no compliance claim.
- **Architecture assessment:** Compare practical design options against project constraints. Distinguish recommendations from decisions already accepted; include the current design when viable.
- **Verification strategy:** Select proportionate checks based on risk, existing project practices, and available authorized tools. There is no universal test command.
- **Project documentation context:** Find, reconcile, or draft project guidance such as `AGENTS.md`, documentation indexes, or decision records. Existing project policy takes precedence over adaptable examples and templates.

## Example prompts

Include the relevant requirements, files, and constraints in your request. These examples are starting points; tailor them to your project.

- **Review:** “Review this pull request against the accepted requirements in `docs/requirements.md`. Check the changed files and relevant project guidance. Report findings with evidence and criterion statuses. Do not edit files or run commands.”
- **Architecture:** “Assess whether to keep our current job queue or move to a database-backed queue. Constraints: jobs must survive restart; we operate one service instance; no new managed services. Compare options and label any recommendation as proposed.”
- **Test gaps:** “Which acceptance criteria of TICKET-42 are covered by the existing tests, which are not, and what minimal checks would close the gaps? Read-only.”
- **Verification strategy:** “Given this change and the project’s existing checks, propose the smallest useful verification plan. Identify checks that need an environment or permission we do not have. Do not run them.”
- **Documentation context:** “Review the documentation index and relevant `AGENTS.md` files for this module. Suggest a concise update that links existing guidance instead of duplicating it. Draft the requested changes only.”

## Getting started

1.  Use a host or assistant environment that supports skill instructions and can make relevant project context available.
2.  Have the skill installed or enabled through that host’s supported process. Hosts manage skill availability differently; follow their own instructions for adding a `SKILL.md` package. This guide does not provide a download route or assert that a particular host or marketplace client has been tested.
3.  Open the target project or provide the relevant files and accepted requirements. Give the assistant only the access needed for the task.
4.  State the desired mode, scope, constraints, and whether you authorize any requested edits or checks. The assistant should identify missing evidence rather than invent it.

No particular language, framework, test runner, repository layout, or connected service is required. Tool availability and permissions come from the host and task environment, not from Banjo Sniffs.

## Reading review statuses

A review uses separate labels for individual criteria and the overall disposition:

| Label                | Meaning                                                                                                                                                    |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MET`                | Available evidence shows the criterion is satisfied.                                                                                                       |
| `NOT_MET`            | Available evidence shows the criterion is not satisfied.                                                                                                   |
| `UNVERIFIED`         | Evidence, access, or an unresolved decision is insufficient to determine the result.                                                                       |
| `PASS`               | Overall review disposition: the reviewed scope meets the accepted criteria based on available evidence; behavioral criteria were exercised, not only read. |
| `PASS (static only)` | Every behavioral criterion rests on reading the source; the runtime gap is named.                                                                          |
| `FAIL`               | Overall review disposition: one or more accepted criteria are not met.                                                                                     |
| `INCOMPLETE`         | Overall review could not reach a complete disposition, for example because required evidence is unavailable.                                               |

Every entry in the verification record is typed `RUN exit=<n>` (executed, with its output), `NOT RUN: <reason>` (planned, unavailable or declined), or `STATIC` (established by reading source), so a planned check is never reported as an executed one. The report opens with a seven-line summary (disposition, blockers, owner decisions, what ran, what did not, basis, next step); the handover points to the report and never restates its tables. Implementation acceptance (`ACCEPTED`, `NOT_ACCEPTED`, `UNVERIFIED`) is set only by the accepting owner.

A test-gap analysis uses its own classes for existing checks: `COVERED` (a check would fail on a wrong implementation), `PARTIAL` (exercised but under-asserted), `UNCOVERED`, `UNVERIFIED`. These describe tests, not the implementation, and never turn into `MET`.

These labels describe the stated review scope; they do not establish general production readiness. A review disposition is also distinct from whether an implementation has been accepted. Ask the assistant to state the evidence and limits behind each conclusion.

## Templates and generated material

Templates are optional starting points, not project policy. Ask the assistant to use or adapt one for an authorized task, for example: “Draft an ADR using the project’s existing format; if none exists, use the available ADR template and mark the decision as proposed.” Review the result before adopting it. Generated reports or documentation should stay within the scope and destination you authorized. Any rights or terms for generated material depend on the applicable host and marketplace terms; this guide makes no rights grant or legal promise.

## Optional HTML version

From version 1.4.0. Ask for it when you want a report you can open in a browser or send to someone, for example: “Also save the report as HTML.” The assistant writes a self-contained `.html` file next to the Markdown file: the same content, status labels in colour, no scripts and no remote resources. The Markdown file stays the canonical record.

How the Markdown itself looks depends on where you read it: formatted in tools that render Markdown, plain text in a terminal.

## Your output and the licence

Everything the skill produces for you - review reports, handovers, test-gap maps, decision records, project guidance, including template wording that ends up inside those documents - is yours to keep, commit and share with the people working on the same project. The skill itself (instructions, references, unfilled templates) may not be extracted, copied or redistributed, alone or inside another skill or service; the marketplace controls access to it. Provided as is, liability limited to the price paid, without affecting rights the law or the marketplace's money-back guarantee give you.

## Limitations and troubleshooting

- **The answer lacks project context:** Provide the accepted requirements and the relevant source files or authorize access to them. The assistant should mark affected criteria `UNVERIFIED` if evidence remains unavailable.
- **A project rule conflicts with a request or another source:** Ask the assistant to identify the competing sources and precedence. Unresolved affected criteria should remain `UNVERIFIED`.
- **A command, service, or fixture is unavailable:** Ask for a verification plan that identifies the missing prerequisite. A proposed check is not a test result.
- **A review proposes edits or execution:** Reviews are read-only by default. Explicitly authorize the specific edits or checks if you want them performed.
- **A template does not match your project:** Adapt it to established conventions, or continue using the project’s existing format.
- **The host does not expose the skill or needed tools:** Consult that host’s skill and tool instructions. The package itself cannot install into a host, enable permissions, or establish compatibility.

Banjo Sniffs does not require external network access by default. Do not provide secrets or transfer customer data unless the task, authorization, and environment expressly allow it.

## Demonstrations

- [Review of a real public commit](review-real-commit.md)
- [Review of a synthetic PR with planted defects](review-planted-defects.md)
- [Test-gap analysis](test-gap.md)
- [Architecture assessment](architecture-assessment.md)

---

<p align="center"><sub>© 2026 Piotr Chrobak · Banjo Sniffs™ · <a href="LICENSE">License</a> · Bug reports for the skill: piotr.chrobak.contact@gmail.com</sub></p>
