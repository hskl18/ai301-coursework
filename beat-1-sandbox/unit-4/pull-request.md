# Unit 4 - Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Status as of October 8, 2026 PDT: the official eval is complete at 20/20 and upstream PR #109 is open.

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/109

Opened by hskl18 at 2026-10-08T16:03:04Z against codepath/pathreview-ai301-fa26-s3:main from hskl18:fix/72-malformed-password-hash.
The PR closes issue #72.
GitHub stored the exact title and body reviewed by live-04; the delivered implementation contains only core/security.py and tests/unit/test_security.py.

**Branch**

`fix/72-malformed-password-hash`

Verified pushed implementation commit: `4e7ce33cf13e67e1e061eadc51f6e68d24cbfbaf`.

## Eval iterations

**Run history**

Every run, in the order I ran them (times are when each run finished, UTC):

1. Full run, 00:46:22, original rubric: `agreement: 18/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 5/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`.
   pkg-02 failed `Observable behavior` and pkg-08 was `unclear` on `Repository checks`.
2. Partial `--only` run, 00:48:29, revision 1, on pkg-02 and pkg-08 plus canaries pkg-04, pkg-07, pkg-17, pkg-20: `agreement: 6/6 scored items`.
3. Full run, 00:52:05, revision 1: `agreement: 19/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 6/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`.
   pkg-19, which agreed in run 1, failed `Observable behavior` because its two controls were only stated as unchanged.
4. Partial `--only` run, 00:53:26, revision 2, on pkg-19 plus canaries pkg-07, pkg-09, pkg-12, pkg-20: `agreement: 5/5 scored items`.
5. Full run, 00:56:34, revision 2: `agreement: 18/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 5/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`.
   pkg-11 and pkg-16, which agreed in runs 1 and 3, failed `Description matches evidence` on wording nitpicks.
6. Partial `--only` run, 00:57:55, revision 3, on pkg-11 and pkg-16 plus canaries pkg-01, pkg-04, pkg-17, pkg-20: `agreement: 6/6 scored items`.
7. Full run, 01:01:44, revision 3: `agreement: 19/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 6/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`.
   pkg-05 failed `Observable behavior` because revision 2's new sentence demanded a separate observed result for its second planned case.
8. Partial `--only` run, 01:02:54, revision 4, on pkg-05 plus canaries pkg-07, pkg-14, pkg-17, pkg-20: `agreement: 5/5 scored items`.
9. Full run, 01:04:13, revision 4: `agreement: 20/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 7/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`.

All runs were on October 8, 2026 UTC.
The partial runs are diagnostics: they never write `eval-run.txt` and cannot decide the bar or the category floor.
The submission-candidate `eval-run.txt` is run 9, and its four fingerprints match `SKILL.md`, `rubric.md`, `procedure.md`, and `references/evidence-guide.md` in `tools/pr-precheck/`.
Every revision changed only `rubric.md`; the other three fingerprinted files are the originals from run 1.
I stopped at 20/20.

**Package analysis**

`pkg-02` (Textualize/rich#4208, category `clear-accept`, gold label accept).

In run 1 (full) my rubric decided reject, failing only `Observable behavior`: "Repro and new test exercise only save_text; no failed-write check for save_html or save_svg, and the omission is not disclosed while the description claims all three are fixed."
The plan applies the same fix "in all three `save_*` methods (same one-shape fix, same file)", and its test plan names one trigger: "re-run the issue's script, expect `export_text()` to still return `'IMPORTANT OUTPUT\n'` after the failed save; a successful save still clears; run pytest."
The evidence does exactly that.
The after run prints `'IMPORTANT OUTPUT\n'` where the before run printed `''`, the new test's second half checks that a successful save still clears, and `pytest tests/ -q passes (1462 passed, 12 skipped)`.
My original row said "Distinct planned failure modes and affected controls are checked", and the grader counted each identical sibling as its own failure mode, then held the PR to tests its own plan never asked for.

Revision 1 added a general rule: when the plan applies one identical change shape at sibling sites and its test plan names a representative trigger, observing that trigger satisfies the row.
In run 9 (the final full run) my rubric decided accept on all six checks, matching gold.
Its `Observable behavior` evidence reads: "Issue repro before shows '' and after shows 'IMPORTANT OUTPUT\n'; the new test covers the successful-save-still-clears control; siblings use the same change shape with save_text as the representative trigger."

**Check rationale**

This is the exact current row from `tools/pr-precheck/rubric.md`:

```text
| Description matches evidence | Candidate title, description and checklist claims beside the actual diff, commit list, plan/deviations and test-evidence results. | Claims of changed behavior, coverage, execution, success and completeness are supported by those artifacts and do not contradict them. Planned, completed and unverified work are distinguished; tests in a diff are not claimed as executed without outcomes. Honest limitations are preserved rather than replaced with broader claims. Fail a material claim (what changed, what was tested or run, what is complete) that the artifacts contradict or leave unsupported; a summary phrase the diff substantially bears out, a condensed output excerpt, or a concern about code the package does not show is a note, not a contradiction. | required |
```

The first three sentences are the original design: the description has to answer to the diff and to real command output, so a ticked box or an added test cannot stand in for a run.
The last sentence is revision 3.
In run 5 (full) the original row failed two clean PRs on details that are not contradictions.
For pkg-11 the grader wrote that the new test has "no unescaped-trim assertion", but the test input `"foo\\   \n"` carries unescaped trailing spaces that the fix trims.
For pkg-16 it objected that the pasted error text lacked the `loading images:` prefix the diff would add, and speculated about start-path callers the package never shows.
The revision sets the bar at material claims: what changed, what ran, and what is complete.
I kept the fail side concrete because silent drift depends on it.
In run 9 this row still failed pkg-01 on "check added 'to the bulk-copy path' but the diff places it at function entry" and pkg-17 on "docs 'now documents the limitation' but the diff has no docs change".

**Trade-offs**

The materiality sentence and revision 2's control rule make the rubric more lenient, and the canaries show what that cost.
In run 1, pkg-04 failed `Description matches evidence` because the description calls its fallback "the same flag set the successful probe path uses" while the diff adds only `--RAW-CONTROL-CHARS`.
In run 9 the same row passed pkg-04 and called that phrase "imprecise ... but only a note."
pkg-04 still rejects, but only because its `Observable behavior` row finds no command or before/after at all.
pkg-20, one of the two standards-wall packages, went from three failed rows in run 1 to one: only `Repository standards` still fails it, for the missing disclosure its AI policy requires.
So the rubric now catches these packages through fewer independent checks.
A PR that falsely says a control was unchanged, or misdescribes one detail of its own diff while showing a real repro, can now pass.
I accepted that so honest PRs with compact evidence stop failing on nitpicks, and every revision was checked with standards-wall and not-tested canaries before the confirming full run.

---

Related paths: `eval-run.txt` in this directory; the complete skill in `tools/pr-precheck/`.
