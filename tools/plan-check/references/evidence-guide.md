# Evidence guide: where evidence lives in a plan package

In eval mode, the bundle is the entire evidence set; never fetch the source issue or use the answer key while grading.
In live mode, read the issue and student's own posted report, but grade candidate grounding from what the drafts contain and quote.
Repo facts and maintainer statements provide context, not substitutes for reproduction evidence.

## Diagnosis and grounding

- Eval: Issue, Repro evidence, and cause or diagnosis in Candidate plan and Candidate plan comment.
- Live: issue body, the student's posted Unit 2 report, and quoted reproduction and diagnosis in plan.md and comment.md.
- Good: the mechanism fits the failing case, controls, and traces. Observational support plus a bounded trace or decisive verification can make an inferred mechanism sufficient for planning without proof of every internal step or a literal hypothesis label. A mechanism that contradicts a control or trace still fails, even with an otherwise detailed test plan.
- Example: calib-01's push succeeds but color updates only after re-entering, supporting a refresh hypothesis. Calib-03 stays slow without a pager, contradicting a pager-binding cause.

## Scope

- Eval: scope, in/out statements, change lists, files, and approach in Candidate plan, compared with the issue's requested outcome.
- Live: scope, files, approach, and Deviations in the plan, checked against the comment.
- Good: all edits support one bounded outcome. Supporting tests and docs are allowed; unrelated architecture rewrites and open-ended sweeps are not.
- Example: calib-01 targets the push callback's refresh scope and excludes push-status computation and other views' refresh behavior.

## Executability

- Eval: named files or code areas, operations, and order in Candidate plan; relevant implementation direction in Thread highlights.
- Live: draft source locations and approach. Issue context explains constraints, but unquoted local code cannot supply an absent approach.
- Good: a contributor can start from a named flow or code area, a concrete operation, and its intended effect. Exact functions may be localized by a stated tracing method within those identified modules; cooperating modules along the same flow are not incompatible alternatives. A vague subsystem search or a menu of possible fixes leaves the approach unresolved.
- Example: calib-01 names pkg/gui/controllers/sync_controller.go and adding the commits context to the successful-push refresh scope.

## Test plan

- Eval: Repro evidence steps and controls compared with the plan's checks, expected observations, and relevant regression cases.
- Live: quoted Unit 2 trigger and output, then proposed commands or steps and expected after-change results.
- Good: the check exercises real changed behavior and distinguishes the original failure from success. Manual observation is valid; a suite name alone is insufficient. Include a relevant control for a concrete regression risk.
- Example: calib-01 repeats the push steps and requires the color to change without leaving the view, also checking the main commits panel and force push.

## Honesty

- Eval: causal and completion claims in both candidate sections; assumptions, uncertainties, and caveats anywhere in the plan.
- Live: draft language, quoted evidence, risks/unknowns, and Deviations. An unbuilt plan may leave the final deviation report pending.
- Good: observed results, inferred mechanisms, intended work, and completed work remain distinct. Compare actual testing claims with all supplied evidence, including the repro's summary and reported version window, rather than only its Environment line. Assertive phrasing of a supported proposed mechanism is not on its own a false claim of completed verification. Material unknowns have bounded checks; deviations explain the final approach.
- First-person claims: an uncontradicted preparatory check, such as a dependency option tried locally or diagnostic logging already set up, is testimony rather than a false claim when it is not presented as verification of the fix and remaining work has a bounded check. A first-person claim to have traced or established a cause fails when the repro's controls or traces contradict it, or when nothing bounded would resolve it.
- Supplementary live observations: look for a quoted real-code command or steps, actual output, and an explicit distinction from the student's already-posted Unit 2 report. These can support the draft without being misrepresented as part of the older report; unquoted sibling-file evidence remains outside the package.
- Example: calib-01 proposes a refresh change with an observable check; it need not supply an already-built implementation result to be ready.

## Comms

- Eval: Candidate plan comment read against Issue, Thread highlights, and Repo facts contribution policy. The package's report may supply already-reported environment and steps.
- Live: comment.md, the live issue thread, and applicable CONTRIBUTING or AI-policy documents at the source repo's current default branch, retrieved with gh or the GitHub API.
- Good: the comment states an independent approach, addresses material maintainer directions and existing work, and follows requirements for this type of comment. An AI-disclosure requirement needs the tool and extent. Human-authorship and disclosure rules are different; follow stated wording rather than judging style.
- Do not infer disclosure from silence or PR-only rules. Scarce PR review capacity is not a ban on issue discussion. Do not demand bug-report headings in a plan comment built from an already supplied report.
- Example: calib-01's review-bandwidth note favors a bounded proposal, not an automatic hold. In live Path Review, classmates' plans do not block this student's own work; 'same as above' is not an independent plan.
- For an overlapping live PR, look for acknowledgement of the proposed change and an independent plan based on this student's evidence. Acknowledging the overlap satisfies coordination; the house rules do not require abandoning the issue or waiting for that PR.
