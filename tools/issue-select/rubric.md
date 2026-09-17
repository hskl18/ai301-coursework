# Rubric: is this a good first issue?

Ten checks over five surfaces: is the maintainer alive, is the repo in
use, does the scope fit a newcomer, is anyone already on it, and am I
allowed to contribute the way I work (AI-assisted).

**Date basis.** Every recency threshold is measured against the bundle's
`captured:` date in eval mode, and against today in live mode. Never
against the current calendar date when grading a snapshot.

## Checks

| Check                 | Evidence                                           | Pass condition                                           | Weight    |
| --------------------- | -------------------------------------------------- | -------------------------------------------------------- | --------- |
| `repo-not-archived`   | repo line: `archived:` flag                        | `archived: no`                                           | required  |
| `maintainer-active`   | last 5 default-branch commits                      | a human commit within 90 days                            | required  |
| `repo-in-use`         | latest release, last push                          | release within 12 months, or push within 6 months        | required  |
| `one-bounded-task`    | issue title and body                               | one pull request's worth of work                         | required  |
| `spec-settled`        | comment count, linked-PR states                    | under 20 comments and at most 1 closed-unmerged PR       | required  |
| `maintainer-triaged`  | author_association, labels, commenter associations | filed, labelled, or endorsed by someone with repo rights | required  |
| `unclaimed`           | assignees, linked-PR states, claim comments        | no assignee, no open PR, no claim under 12 months old    | required  |
| `ai-policy-permits`   | contribution-policy line                           | no outright ban on AI-assisted work                      | required  |
| `fast-first-response` | maintainer first-response sample                   | one sampled reply within 30 days                         | preferred |
| `newcomer-sized`      | labels and body                                    | newcomer label, or a named place to start                | preferred |

## Check details

The table is the contract; these notes say how to read the evidence at
the edges, and why each threshold sits where it does.

### `repo-not-archived` (required)

Read the `archived:` flag on the repo line (live mode: the archived
banner across the repo front page). `archived: yes` fails: the repo is
read-only, so nothing can be merged and no issue text can rescue it.

### `maintainer-active` (required)

Read the dates and authors of the last 5 default-branch commits. Pass if
at least one is within 90 days of the capture date **and** is authored by
a human, or by a bot merging a human's pull request. A bot's own
housekeeping commit (`dependabot`, `pre-commit-ci` bumping dependencies)
is not human life by itself. Fail when the newest qualifying commit is
older than 90 days: nobody is left to review a newcomer's PR.

### `repo-in-use` (required)

Pass if the latest release is within 12 months of the capture date, **or**
there has been a push to any branch within 6 months. The second clause is
what carries a healthy repo that publishes no releases at all
(`latest release: none published`) and a mature repo that ships slowly.
Fail only when both are stale.

### `one-bounded-task` (required)

Pass if the body asks for one change a newcomer could finish in a single
pull request. Fail if it is an umbrella or tracking issue: a list of other
issue numbers, a self-described "megaissue", or an open-ended program such
as "incrementally add X across the codebase". Also fail a usage or support
question, which is not a change at all.

Two things that are **not** failures here: a list of files touched by one
change is not an umbrella, and a terse body, an acceptance-criteria
checklist, or a bug report that names its likely causes is bounded. Grade
the size of the work asked for, not the polish of the write-up.

### `spec-settled` (required)

Pass only if both hold: the thread runs fewer than 20 comments, and at
most one linked PR is closed unmerged. Twenty-plus comments means the
design is still being argued and a newcomer would be writing the spec;
two or more abandoned attempts means the work is harder than the friendly
label claims. A single closed PR is one abandoned attempt, not a pattern.

### `maintainer-triaged` (required)

Pass if any one holds: the issue was filed by someone with repo rights
(`OWNER`, `MEMBER`, `COLLABORATOR`); or it carries at least one label
(only accounts with triage rights can label an issue, so a label is a
maintainer's hands on it); or an owner/member/collaborator comment
endorses the work.

Fail when an outside account filed it, no label was ever applied, and no
maintainer has replied. An untriaged outside request is a proposal
awaiting a product decision, not work anyone has agreed to.

### `unclaimed` (required)

Fail on any of: an assignee; an open linked PR, or a PR the thread
describes as in progress; a claim comment ("I'll take this", "working on
this") newer than 12 months that went unanswered.

A claim older than 12 months with no PR behind it is stale and does not
block, especially where a maintainer has since invited takers. A closed
unmerged PR is an abandoned attempt, not a claim.

Live mode: apply the claim-related house rule in `scope.md`. Inside Path
Review, a classmate's claim signals do not block: neither their claim
comments nor their open pull requests, since course credit attaches to
the PR you open rather than to whether it merges. A staff assignee still
blocks. Outside Path Review, read this check as written.

### `ai-policy-permits` (required)

Read the contribution-policy line (live mode: `CONTRIBUTING.md`,
`.github/CONTRIBUTING.md`, the contributor docs it links out to,
`AI_POLICY.md` / `AI_USAGE_POLICY.md`, and PR-template disclosure
checkboxes).

Pass when the policy is silent on AI, welcomes AI tools, or sets
conditions this workflow can meet: disclose AI use, personally understand
and test every change, human-review AI output, or "fully AI-generated
contributions are not accepted" while assistive use is allowed.
Conditions are terms to follow, not reasons to walk away.

Fail only on an outright ban, e.g. "we do not accept AI-generated code or
documentation". This course's workflow is AI-assisted, so a ban means the
PR is refused before a maintainer reads a line of it.

### `fast-first-response` (preferred)

Read the maintainer first-response sample (5 recently updated issues, days
to the first owner/member/collaborator comment). Pass if at least one drew
a reply within 30 days. Preferred only: repos that ship daily but answer
few threads are still worth contributing to, so a slow sample lowers the
rank, never the verdict.

### `newcomer-sized` (preferred)

Pass if the issue carries a `good first issue`, `documentation`, or
`easy` label, or names where to start (a file, a component, or an
acceptance-criteria list). Preferred only: it orders accepted issues by
how fast a first PR can land.

## Verdict rule

- **accept** if every `required` check passes. Any single `required` fail
  makes the verdict **reject**. There is no third verdict and no scoring
  by majority: each required check names a way a first contribution dies
  outright.
- `preferred` checks never change a verdict. Report their grades and use
  them to rank the accepted issues (live mode then orders that ranked
  list by the fit profile in `scope.md`).
- `unclear` on a required check counts as **fail**: a first issue whose
  risk you cannot verify is not one to take. Two documented exceptions,
  where absent evidence is genuinely passing rather than unknown:
  `ai-policy-permits`, since no stated policy is not a restriction, and
  `repo-in-use` when the repo publishes no releases at all, which is
  graded on push recency instead.
