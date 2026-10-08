# Procedure: how this tool grades a PR package

## Read order

1. Determine the mode and package identity.
   In eval, read only the supplied frozen bundle as evidence and ignore scope and voice.
   In live, first enforce scope, then read the voice guide and identify the issue URL, fork root, branch and explicitly named plan, description and evidence files.
2. Read the rubric and evidence guide; record all rows, weights and verdict rule.
   Stop if the rubric or procedure is empty rather than making up checks.
3. Read issue context, reproduction, thread and repository requirements before the candidate's claims.
   In live, fetch the issue thread, PR template and CONTRIBUTING policy with read-only access.
   Use the student's own linked reproduction, or the supplied house repro pack; classmates' parallel PRs do not block the student.
   Record which asks apply now and which require a published PR.
4. Read the complete plan, including exclusions, test plan and Deviations, before the diff so the diff cannot silently redefine the agreed scope.
5. Read the branch's commits and every hunk from `git diff main...HEAD` in live, or the bundle's commit list and unified diff in eval.
   Read the entire test evidence, then compare the title and full description against these artifacts.
   Worktree edits outside that committed diff are not delivered changes.

## Evidence gathering

1. Plan fidelity: pair each substantive hunk with a planned operation or a deviation that states what changed and why.
   Check in both directions: extra changes and promised changes missing from the diff.
   Pair each mismatch with the description's scope/limitation wording; a description-only admission is not a missing plan deviation.
2. Observable behavior: map every distinct planned trigger, expected result and affected control to the supplied command/input and observed before/after.
   A reused original repro output is allowed when its provenance and revision are clear.
   Distinguish direct execution of the built code from a mock-only check, assertion text, generic suite total or future intention.
   Record missing modes and whether the plan/deviations and description honestly limit completion.
3. Repository checks: enumerate the applicable suite, lint, type, build or other required checks from repository facts and the plan.
   Match each to the command and actual result, or a specific reason it could not run with its impact disclosed.
   Preserve failures, warnings, no-tests outcomes and exit codes when supplied.
   Distinguish an inner tool exit from a wrapper exit and local from hosted status.
4. Description truth: pair each material claim and checked box with its supporting hunk or actual command result.
   Read the evidence as a whole; compact but concrete frozen-package observations count without invented raw logs.
   Note claims contradicted by the diff or outcomes, and claims that omit a material limit.
5. Diff focus: inspect all hunks, including seemingly harmless cleanups, debug prints and commented-out code, against the issue's purpose.
   Identify necessary support separately from unrelated edits; a deviation note does not excuse debris.
6. Standards: match each stated template section, checklist, contribution rule and material maintainer request with actual candidate content.
   Apply only stated requirements, with justified N/A where appropriate; do not import this course's template or AI policy into eval packages.
   In live, the assignment requires AI-use disclosure in Notes for Reviewers even if repository policy is silent, and leaves hosted CI unchecked before PR creation.
   Report the repository's eventual CI-green review requirement separately from course pre-opening readiness.
7. Keep one evidence note per row naming the decisive location, fact or quote, including the specific absence when evidence is missing.
   Never fetch extra evidence in eval or use a gold label to decide a grade.

## Check execution

1. Execute every rubric row in table order, even after finding a failure.
2. Grade pass only when that row's condition is met; fail for a contradiction or clearly absent required substance; unclear for evidence that cannot resolve the condition.
   A failed command honestly reported is not automatically a failed rubric row, and a confident description is not proof.
3. Re-read relevant paired sections when needed; do not invent missing outcomes or new requirements.
   Accept concise concrete evidence, necessary supporting files and properly explained deviations without demanding polished prose or exhaustive testing of unrelated behavior.
4. In live, report title/description voice violations with the broken rule quoted.
   Personal voice alone never changes these rubric grades.
5. If the procedure leaves a relevant decision unresolved, name the gap and use unclear for a required condition that remains unverifiable.

## Verdict assembly

1. Apply the rubric mechanically: all required rows pass means accept; any required fail or unclear means reject.
2. Give a readable line for each check with deciding evidence.
   For reject, quote the first failing or unclear required check in rubric order as the primary reason, then list the other failures without hiding them.
   Report gaps, live voice notes and disclosed limits before the JSON.
3. End with the exact SKILL.md JSON schema: item, checks in rubric order with name/grade/evidence, then verdict.
   Use only pass, fail or unclear grades and accept or reject verdicts; emit no text after the fenced JSON.
