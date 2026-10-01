# Procedure: how this skill grades a plan package

## Read order

1. Determine the mode. For eval, read only the bundle and do not fetch its source issue. For live drafts, enforce scope.md, read voice-guide.md, and identify the supplied issue URL and both draft files.
2. Read rubric.md and references/evidence-guide.md. Record every check name, weight, pass condition, and verdict rule before grading.
3. Read the issue and reproduction before the candidate diagnosis. Record failing inputs or steps, expected and observed results, controls, traces, and environment limits so candidate confidence cannot replace evidence.
4. Read repo facts and thread highlights. In live mode, use gh or the GitHub API to read the issue and applicable repository policy. Identify the student's own posted Unit 2 report; another student's report is not theirs. Follow the house repro-pack exception in SKILL.md when applicable.
5. Read the entire plan and draft comment, including scope, approach, tests, unknowns, and Deviations. Missing headings are not missing substance. The drafts must contain or quote the reproduction they rely on; unrelated working-directory files are not part of the package.

## Evidence gathering

1. For diagnosis and grounding, pair each causal claim with reproduced observations, controls, or traces. Read the complete repro, including its summary and regression window, alongside issue history. Separate what the observations demonstrate from the proposed internal explanation; a mechanism may be a supported working inference even without the literal word 'hypothesis'. Record whether a bounded trace or decisive check can resolve its remaining uncertainty, and reject an explanation contradicted by a control or trace.
2. For scope, list change locations and their purpose, plus exclusions stated directly or made clear by the bounded operations. Separate supporting tests and docs from unrelated work.
3. For executability, record the starting area, proposed operation, and intended effect. If exact functions are deferred, record the named flow or modules and the concrete tracing method used to locate them. Distinguish cooperating locations in one flow from unrelated alternative fix sites or an unspecified subsystem. Identify unresolved choices that actually prevent starting the stated approach.
4. For tests, map the original trigger to the after-change check. Record inputs or steps, expected observation, whether it exercises the real changed behavior, and concrete neighboring behavior at risk. Reproduction steps referenced within the same bundle or quoted draft may supply the steps.
5. For honesty, compare claims of observed, tested, or completed work with the complete supplied evidence, including version history and the repro's own summary. Do not equate a proposed causal model with a claim that a fix was already verified. Classify each first-person claim of investigation or checking: preparatory testimony the package does not contradict, a completed fix or test result, or a traced or established cause. Testimony is acceptable when it is not offered as verification of the fix and leftover uncertainty has a bounded next check; a completed result fails before it exists; a traced cause fails when the package contradicts it or nothing bounded resolves it. Missing output for testimony is not by itself a contradiction. Record material unknowns and resolution steps, and differences between the plan and any final build. In live mode, supplementary observations in the drafts may be used when their real-code command or steps and actual result are quoted and they are clearly distinguished from the posted Unit 2 report; do not reconstruct missing output from sibling files.
6. For comms, compare the comment with the issue, material maintainer requests, and linked work. In live Path Review, classmates' parallel work does not block an independent plan. An existing PR proposing the same change is material context to acknowledge, not a reason to demand the student abandon the issue or await permission. Record the exact applicable policy and its scope before deciding what it requires. Treat package candidates as AI-assisted where an applicable disclosure policy needs that fact; do not infer prohibited authorship from writing style alone.
7. Keep an evidence note for every row. In live mode, also record the student's report permalink and the relevant quoted draft evidence. Do not use unquoted sibling reports or local source files to repair omissions in the drafts.

## Check execution

1. Execute every rubric row in table order using gathered evidence. Do not stop at the first failure; produce all check grades.
2. Give pass only when the stated condition is met. Give fail for a contradiction or clearly absent required substance. Give unclear when evidence cannot decide the condition. Do not invent implementation details or presume tests have succeeded.
3. Put the deciding observation or short quote in each check's evidence field. For fail or unclear, identify the exact contradiction or missing information. Re-read only relevant sections to resolve a specific question.
4. Allow concise plans, bounded localization, evidence-supported causal inferences, and manual checks that meet the condition. Do not demand proof of every internal step before a plan can be implemented, automated tests, all possible edge cases, literal headings, a fixed file count, or repeated template fields unless a stated applicable requirement calls for them. A concrete test plan does not rescue a cause already contradicted by reproduction evidence.
5. In live mode, apply the house rules to parallel classmates' work. Report voice-guide violations separately with the rule quoted; personal voice feedback alone does not change this rubric's verdict.
6. If the procedure leaves a relevant decision unresolved, report the gap rather than invent a new rule. Genuinely unresolved required evidence receives unclear.

## Verdict assembly

1. Apply the verdict rule mechanically: all required checks pass means accept; any required fail or unclear means reject. Preferred checks never gate the verdict.
2. Summarize deciding evidence for failures or unclear grades and report procedure gaps. Do not replace evidence with 'looks fine' or an agreement target.
3. Emit the SKILL.md output contract as the last fenced JSON object: item, every check's name, grade, and evidence, and verdict. Grades are pass, fail, or unclear; verdict is accept or reject. Put nothing after the JSON block.
