# Rubric: is this claim and reproduction ready to post?

Read the issue, claim, and report in that order.
Judge the observed behavior against the issue's specific trigger and failure mode, not whether the prose sounds confident or follows a template.
An honest, evidenced inability to reproduce can pass; an adjacent error presented as confirmation cannot.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| `claim-specific` | Claim comment compared with the issue's defining behavior and the report, if present | Names the issue-specific behavior or trigger and a concrete next investigation or report; any claim of reproduction is supported by the report. Does not promise a fix, date, or reserved ownership. | required |
| `environment-recorded` | Report's environment record compared with the issue's target versions, platform, build, and relevant configuration | Identifies the product and version or code state, plus the OS/runtime/configuration that can affect this failure. Material differences from the issue are stated and conclusions are limited to the tested setup. | required |
| `steps-rerunnable` | Report's setup, inputs, commands or actions, and public issue context | A stranger can recreate the starting state and run the attempted trigger from the posted information and public sources. A private or unspecified fixture, configuration, or command needed for the result fails. | required |
| `target-attempted` | Issue's defining trigger compared with the report's actual input, flags, version, and actions | The attempt exercises the issue's operative condition, or a cannot-reproduce report clearly states which condition could not be matched and what was tried. A changed operator, option, input, or unsupported old version presented as the same bug fails. | required |
| `behavior-evidenced` | Report's output, log, screenshot description, measurement, or explicit control result compared with the issue's actual behavior | A shown artifact demonstrates the issue's distinctive behavior, or demonstrates the observed nonfailure in an honest cannot-reproduce attempt. Setup success, a generic nonzero exit, an unshared artifact, or an assertion of a root cause without observed behavior does not pass. | required |
| `conclusion-bounded` | Report's expected/actual statement and claim compared with the shown artifact and issue | States what was expected and what actually happened; the conclusion follows the shown result. Distinguishes a hypothesis from a verified cause and reports cannot-reproduce and scope differences plainly. | required |
| `repo-conventions` | Repo-facts bug-report asks and contribution/AI policy compared with both comments and report | Supplies the substance of relevant requested context and obeys requirements for issue comments, including AI-use disclosure with tool and extent when the repo requires it. A PR-only disclosure rule does not impose disclosure on issue comments; no literal template headings or extra boilerplate are required. | required |

## Verdict rule

**accept** only when every applicable required check passes.
Any required `fail` or `unclear` makes the verdict **reject**; missing proof is not a pass.
In live claim-only mode, mark checks that need the repro report `unclear` with `not yet applicable: claim-only draft` and exclude them from the verdict, as `SKILL.md` directs.
No preferred checks or majority vote change the verdict.

For this course's eval packages, assess any repository disclosure requirement as applying to the AI-assisted candidate comments.
Use only the bundle's stated policy to decide whether disclosure is required in issue comments; do not infer a requirement from silence or from a PR-only rule.
