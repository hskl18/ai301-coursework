# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

- Eval locations: Plan context's accepted plan, scope, exclusions, repro, test plan and any deviation notes; Candidate PR's Diff, Commits, Title and Description.
- Live locations: the named `plan.md`, including `## Deviations`; `git diff main...HEAD` and branch commits in the fork root; the named `pr_draft.md`; the student's posted plan in the issue thread.
- Compare each hunk to the planned operation and compare each promise back to delivered code.
  Good evidence accounts for both extra work and omissions, with a reason recorded in the plan's deviations and an accurate description of the resulting scope.
  A claim of exact fidelity beside an unrelated refactor or silently omitted requirement is drift even when tests pass.

## Test evidence (harness category: not-tested)

- Eval locations: Issue and Plan context's repro and expected-after/test plan; Candidate PR's Test evidence, Diff and Description; Repo facts' required checks.
- Live locations: the named `test_evidence.md` with captured commands, environment, revisions, stdout/stderr and exit codes; `plan.md`'s quoted original repro and test plan; `pr_draft.md`'s testing section; the student's own issue repro comment or supplied house repro pack; the repository template and contribution instructions.
- Good evidence shows the real changed behavior on the original trigger with an observed after compared with before and expected results, covers distinct planned modes and affected controls, and accounts for repository check outcomes.
  An assertion added to a test file proves the check exists, not that it ran; an expected result or generic green total cannot replace the core repro.
  Compact frozen-package command/outcome summaries count as evidence; do not require unavailable live logs in eval.
  Reused before output is valid when clearly identified, and disclosed failing/no-tests results remain real evidence rather than fabricated success.
  A bounded unverified case must narrow the completion claim; no substantive check at all is not an honest partial verification.

## Diff quality (harness category: unreviewable)

- Eval locations: Candidate PR's complete unified Diff and Commits, read against the issue and Plan context.
- Live locations: `git diff main...HEAD`, its file list/stat and branch commit list, paired with `plan.md` and the issue.
- Good evidence lets a reviewer follow the bounded fix and its necessary tests/docs without debug leftovers, dead code, commented-out blocks, unrelated cleanups or formatting churn.
  Inspect hunk purpose, not just filenames or commit titles; an unrelated hunk can hide in an otherwise planned file, and a necessary support file need not have been predicted by name when a deviation explains it.

## Standards and comms (harness category: standards-wall)

- Eval locations: Repo facts' PR-template asks and contribution/AI policy, Thread highlights' material maintainer direction, Candidate PR's Title, Description, Commits and any supplied branch metadata.
- Live locations: the target repo's `.github/PULL_REQUEST_TEMPLATE.md`, `docs/CONTRIBUTING.md`, issue thread, course assignment/house rules, `pr_draft.md` and branch metadata; `voice-guide.md` supplies separate personal voice feedback.
- Good evidence fills every required section with real content or justified N/A, links the issue, honors applicable naming and disclosure asks, and addresses material maintainer direction.
  No stated template or AI policy in an eval package means no invented template or disclosure gate.
  Live coursework always requires truthful AI-use disclosure in Notes for Reviewers; before opening, the assignment explicitly keeps hosted CI unchecked, while the repository still requires green CI for review later.
  A classmate's PR is coordination context under the course house rules, not a veto.
  Description-versus-diff truth belongs to the fidelity/truth checks even if the template is perfectly filled.
