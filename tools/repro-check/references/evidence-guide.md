# Evidence guide: where reproduction proof lives

In eval mode, the package is the entire evidence set.
Use its Issue, Thread highlights, Repo facts, Candidate claim comment, and Candidate repro report sections only.
In live mode, read the issue and relevant contribution policy on GitHub, then grade the exact draft text supplied by the student.
Do not silently borrow a detail from a local file that a maintainer could not see in the posted comments or linked public source.

## Environment

Look in the report's environment statement and compare it with the issue's version, code branch or commit, operating system, runtime, installation method, build profile, and configuration where those affect the failure.
In live mode, the issue body, relevant maintainer replies, repository setup docs, and the draft report establish that comparison.
Record the tested code state precisely enough to place a source checkout; a release version can do the same for a packaged build.
Different environments can still support a valid reproduction or a useful cannot-reproduce report when the difference is named and the conclusion stays within what was tested.
An old release tested against a current-branch issue without acknowledging that gap cannot establish the current issue.

## Steps

Look for a starting state, the exact relevant input or configuration, and the command or action that reaches the trigger.
The issue may supply a public fixture that the report identifies unambiguously; the report need not copy every line again.
An input's required shape can be enough when the omitted values do not affect the trigger; do not demand byte-for-byte fixtures or a particular number of steps.
In live mode, check that referenced issue text or public files are actually accessible and that omitted setup does not decide the outcome.
Use the smallest complete path through the behavior; extra setup or speculative variants do not improve a rerunnable report.
Private repos, hidden configs, and unshared screenshots cannot be the only way to re-run the attempt.

## Behavior shown

Find the artifact produced by the attempt: output, traceback, log lines, measured state, or an accessible screenshot description with the decisive visual observation.
Compare both the trigger and the result with the issue's distinctive behavior.
For example, a syntax-validation error is not evidence of a panic, a live terminal showing raw escape codes is not a terminal crash, and visible tabs are not proof that a pane is blank.
An exit code is useful when it separates these outcomes; a generic error or a setup banner alone is not.
A control run can strengthen a causal comparison, but do not require one when a single artifact already settles the behavior.
For cannot-reproduce, show what actually happened under the attempted trigger, including a normal result or control, and identify the untested condition that may explain the difference.

## Honesty

Read the report's expected and actual statements against its artifact, then read the claim comment for assertions the report would need to support.
State the observed result first and label causes as hypotheses until separately tested.
Do not convert a plausible code reading into a verified root cause, or generalize from one build to another without evidence.
An evidenced cannot-reproduce is a valid outcome when the author records a real attempt and the material differences; a confident confirmation of the wrong behavior is not.

## Comms

Compare the claim with the issue's specific behavior and the writer's next action.
A claim before reproduction should promise a report of findings, not assert a reproduction or guarantee a fix date.
After reproduction, an assertion can pass when the report actually backs it.
Read the bundle's Repo facts contribution policy and bug-report asks in eval mode; in live mode, read the repository's contribution guide, any linked AI policy, and issue template for applicable requirements.
Judge substance rather than copied headings.
If the policy requires AI disclosure for all use in issues or comments, a candidate assisted by AI must name the tool and extent; disclosure only for pull requests is not an issue-comment requirement.
If the policy asks for comments in the contributor's own voice, require the writer to review and put the final words in their own voice; formulaic praise and guaranteed deadlines do not supply evidence.
