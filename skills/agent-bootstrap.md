# Bootstrap Agent Usage in This Project

## Goal

Make this repository easy and safe for coding agents to work in. A single
agent or a team of agents should be able to pick up the repo, learn its
design and workflow in minutes, and contribute without breaking conventions.

Create an `AGENTS.md` at the repository root as a thin pointer file, plus a
set of specification documents under `spec/docs/`. The spec docs are the
source of truth for agents; `AGENTS.md` only tells them where to look.

## Steps

### 1. Study the Project First

Read the existing README, contribution guide, build files (Makefile, CI
workflows), and the main source/documentation files. Identify the project's
purpose, its file layout, its conventions, and any structural problems
(broken build scripts, duplicated content, inconsistencies).

### 2. Create `spec/docs/` as the Knowledge Base

Write one focused markdown document per topic. Start with these (adjust
names to the project):

- **`overview.md`** — what the project is, its scope/content policy, and a
  file-by-file layout of the repository.
- **`conventions.md`** — how the project's documents and code are structured
  and formatted: naming, entry format, ordering rules, style rules.
- **`plan.md`** — the open-task list (fixed location used by the copied
  workflow files; see step 3).
- **Planned docs** (reference them from `AGENTS.md` as "planned but not yet
  written"): `contribution.md` for the contribution workflow and `tooling.md`
  for build/CI behavior. Until they exist, point agents at the repo's
  existing `CONTRIBUTING.md`, `Makefile`, and CI workflows.

### 3. Copy the Workflow Files

The companion files `task_tracking.md`, `report_tracking.md`, and `work.md`
sit in the same directory as this prompt. Obtain them the same way you
obtained this prompt: if it was given as a local file, copy from that
directory; if it was fetched from a URL, fetch each companion from the
same URL, replacing this prompt's filename with the companion's. Copy all
three into the new project's `spec/skills/` (create the directory) verbatim.

These files define the day-to-day workflow and use fixed locations: the
plan document `spec/docs/plan.md` and the reports under `spec/report/`.
Do not rename the files or the locations they reference.

### 4. Write `AGENTS.md` at the Root

Keep it short. State the repo purpose in one line, then list the `spec/docs/`
files with a one-line description of what each covers, and instruct agents to
read them before working. Also list the `spec/skills/` workflow files
(`work.md`, `task_tracking.md`, `report_tracking.md`) and instruct agents to
read them. Mention planned docs and where to find the authoritative rules
until they exist.

## Docs and Implementation Sync

The project is documentation-driven: the `spec/docs/` documents describe the
intended design. Every agent must keep documentation and implementation in
sync while working. At the commit/finish point of any task, the agent MUST:

- **Check** whether the work made any part of the documentation stale or
  inaccurate.
- **Update** any stale document as part of the same change, so the docs never
  lag behind the implementation.
- **Ask for a hint** when the mismatch is ambiguous — for example, when it is
  unclear whether the code or the document reflects the intended behavior. Do
  not guess.

This rule belongs in the project's workflow file — `spec/skills/work.md`
(copied in step 3) — and must be written so it survives: concise, directive,
and unmissable.

## Design Decisions

- **Describe the ideal, not the broken.** The docs describe the intended
  design. If the repo has discrepancies (duplicated sections, TODOs, dead
  references), keep the docs clean and fix the discrepancies in follow-up
  work instead of documenting them as "known issues".
- **Enforce an 88-character line cap** on markdown. Wrap at word boundaries;
  never split an inline code span, URL, or link destination.
- **Do not use tables** in markdown — convey information with bulleted lists
  instead (tables cannot be wrapped to a line cap without breaking).
- **Plain-text questions only.** When agents need input from the user, they
  must ask in plain text — never via predefined-option/dialog widgets or
  preset choice lists.

## Commit

Commit the new `AGENTS.md`, the copied `spec/skills/` workflow files, and
the `spec/docs/` files with a short imperative message in the style of the
repo's existing history.