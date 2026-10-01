# Rubric: is this plan ready to post and build from?

Judge the proposed work against the issue and reproduced behavior, rather than headings, length, or polish.
A supported, bounded hypothesis may be ready to investigate and implement; a cause contradicted by the reproduction is not.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| `diagnosis-grounded` | Cause claims in the plan and comment compared with the complete Repro evidence, controls, traces, issue history, and environment | The proposed mechanism fits the failing case and controls and does not contradict a trace or move the fix to a layer the reproduction rules out. A mechanism inferred from those observations is sufficient for a plan when it names a bounded investigation or verification that can check it; proof of every internal detail and the literal word 'hypothesis' are not required. Reject an unsupported causal leap with no concrete resolving check, or a claim that dismisses contrary evidence. | required |
| `cause-targeted` | Issue's expected behavior and Repro evidence compared with the proposed changes and approach | The approach addresses the failure mechanism and requested outcome, rather than hiding an error, changing an unrelated layer, or documenting a workaround while leaving the requested fix unresolved. A workaround or documentation change is sufficient when the issue or maintainer explicitly asks for that outcome. | required |
| `scope-bounded` | Scope, exclusions, files or areas, and all proposed changes compared with the issue | The work is one coherent change with identifiable boundaries. Supporting tests and documentation belong to that change; unrelated refactors, dependency replacements, feature additions, and open-ended sweeps do not. Boundaries may be expressed in ordinary prose without a literal out-of-scope heading. | required |
| `executable` | Named files or code areas, starting operation, intended effect, and any bounded localization steps in the plan | Another contributor can start from the named area and operation without inventing the core approach. Tracing a named flow within identified modules to locate exact functions is executable when the trace has a concrete method and the intended change is already specified. Multiple cooperating modules are allowed. Reject an unspecified layer, a menu of unrelated approaches, or 'profile and optimize whatever turns up' with no bounded change. Exact function names, line numbers, and complete implementation code are not required. | required |
| `verification-observable` | Test plan compared with the original reproduction's inputs, steps, expected result, and controls | The plan checks the original failure through the changed implementation or documented workflow, gives rerunnable inputs or steps and a specific expected observation, and preserves relevant neighboring behavior when a concrete regression risk exists. Manual or automated checks can pass. A suite name alone, 'no regressions', or a stand-in bypassing changed code is insufficient. | required |
| `honesty` | Claims of observed, tested, or completed work in both drafts compared with the whole package, including the repro summary, issue's version history, risks, unknowns, and any Deviations | Do not claim that the fix, its tests, or the build already succeeded, and do not contradict or misstate what the package's reproduction, controls, traces, or version window observed. A first-person report of a preparatory check that the package does not contradict is testimony, not a false claim, when it is not offered as verification of the fix and remaining uncertainty has a bounded next check; a claim to have traced or established a cause fails when the package contradicts it or no bounded check resolves it. Assertive wording of a coherent, checkable causal model is not by itself dishonest. Read the entire reported regression window rather than demanding an independent run on every mentioned version. Material unknowns have bounded next checks, and build deviations are explained consistently. A missing risks heading alone does not fail. | required |
| `thread-and-conventions` | Plan comment compared with Issue, Thread highlights, Repo facts contribution policy, and material maintainer requests | The comment states the contributor's own actionable approach, addresses material maintainer direction or existing work, and obeys stated conventions for issue comments. Where required, disclose the AI tool and extent and respect human-review or human-authorship requirements. PR-only rules do not add comment requirements; silence does not create a policy. Relevant context can come from the package's quoted report without repeating every bug-report field. | required |

## Verdict rule

Return `accept` (ready) only when every required check is `pass`.
Any required `fail` or `unclear` returns `reject` (hold).
Preferred checks, if added later, never change the verdict.
Do not average checks, compensate for a failed check, or invent a third verdict.

Missing required substance is `fail`; genuinely ambiguous or insufficient evidence is `unclear`.
Both hold the package, but distinguish a missing plan element from unresolved uncertainty.
Use only the frozen bundle in eval mode.
Apply Path Review's house rules in live mode: classmates' parallel plans do not block this student's own plan.
