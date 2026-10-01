# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

hskl18

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5925518483

Posted 2026-10-01 05:44:57 UTC, after the branch was built and pushed (see Deviations in plan.md).
The posted text, exactly:

My proposed change for #72 is on `fix/72-malformed-password-hash` at commit `4e7ce33`:
https://github.com/hskl18/pathreview-ai301-fa26-s3/commit/4e7ce33cf13e67e1e061eadc51f6e68d24cbfbaf
It builds on my own reproduction:
https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5806176715

The change catches `ValueError` around the existing passlib call in `core/security.py` and returns `False`.
That covers `UnknownHashError` and malformed bcrypt values.
`TypeError` and runtime/backend errors still propagate.
This boundary also rejects some invalid-password values; the existing long-password behavior remains covered.

In `tests/unit/test_security.py`, I removed the H-05 strict xfail and covered `"not_a_valid_bcrypt_hash"`, `""`, and `"$2b$12$abc"`.
I also added checks that programming and backend errors are not swallowed.
These are the only two changed files.

My verification repeats the original reproduction with and without `--runxfail`, then checks matching credentials, valid-hash mismatches, and the security suite.
On Python 3.11.15, passlib 1.7.4, and bcrypt 4.3.0, the three malformed cases now return `False`; the security suite has 29 passed.
The repository unit run has 380 passed and 52 expected failures for other seeded bugs.
Lint, formatting, type checking, and the 18 frontend tests also passed locally.

PR #78 already proposes the catch and marker removal.
My course branch uses my own reproduction and adds the empty and truncated-hash cases.
I built and pushed this branch before posting this comment.
I have not opened a PR or verified a live HTTP login.

---

## Your branch

**Branch**

`fix/72-malformed-password-hash`

Fork branch: https://github.com/hskl18/pathreview-ai301-fa26-s3/tree/fix/72-malformed-password-hash
Built and pushed commit: `4e7ce33cf13e67e1e061eadc51f6e68d24cbfbaf`.
The remote branch SHA was checked against local HEAD.

**Evidence**

Before (from my posted Unit 2 report, https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5806176715, on unchanged commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088`):

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format --runxfail -q --tb=short --disable-warnings
```

```text
tests/unit/test_security.py:227: in test_verify_with_wrong_hash_format
    result = verify_password("password", wrong_hash)
core/security.py:37: in verify_password
    return bool(pwd_context.verify(plain_password, hashed_password))
.venv/lib/python3.11/site-packages/passlib/context.py:2343: in verify
    record = self._get_or_identify_record(hash, scheme, category)
.venv/lib/python3.11/site-packages/passlib/context.py:2031: in _get_or_identify_record
    return self._identify_record(hash, category)
.venv/lib/python3.11/site-packages/passlib/context.py:1132: in identify_record
    raise exc.UnknownHashError("hash could not be identified")
E   passlib.exc.UnknownHashError: hash could not be identified
1 failed, 2 warnings in 0.97s
```

Before control:

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_password_incorrect -q --disable-warnings
```

```text
1 passed, 2 warnings in 0.52s
```

After on the built branch, using the real shared helper:

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format --runxfail -q --tb=short --disable-warnings
```

```text
...                                                                      [100%]
3 passed, 2 warnings in 0.32s
```

Without --runxfail, to confirm H-05 is no longer hidden behind an expected failure:

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -q --tb=short --disable-warnings
```

```text
...                                                                      [100%]
3 passed, 2 warnings in 0.17s
```

Existing correct/wrong-password, long-password, empty-password, and token controls, plus the new TypeError/RuntimeError propagation checks:

```sh
.venv/bin/pytest tests/unit/test_security.py -q --disable-warnings
```

```text
.............................                                            [100%]
29 passed, 2 warnings in 4.88s
```

Repository gates:

```sh
make lint
.venv/bin/black --check .
make typecheck
LLM_PROVIDER=mock make test-unit
.venv/bin/pytest tests/integration -v --tb=short
cd frontend
npm ci
npm test -- --run
```

Recorded outcomes: lint passed; Black left all 110 files unchanged; mypy found no issues in 76 source files; unit suite had 380 passed and 52 xfailed; frontend had 18 passed.
Integration collected zero tests, returning 5, which the repository CI explicitly treats as success.
These are local results; no hosted CI run or portal submission is claimed.


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Full runs, in order:

1. Full run 1 (written 2026-10-01T01:20:19Z, original rubric): `agreement: 19/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 6/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4`.
2. Full run 2 (written 2026-10-01T01:51:18Z, final revision 3 files): `agreement: 20/20 scored items  (bar: 18/20: PASS)`, with `categories: clear-accept 7/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4`.

The submission-candidate `eval-run.txt` is full run 2, and its fingerprints match the rubric, evidence guide, procedure, and SKILL.md in `tools/plan-check/`.

Partial `--only` runs between them, which are diagnostic and not full scores:

- Revision 2 on pkg-14 plus ten canaries: `agreement: 9/11 scored items`. pkg-14 still rejected, now only on `honesty`, and canary pkg-03, a gold accept that agreed in run 1, newly failed `honesty`.
- Revision 3 on pkg-03, pkg-14, and six reject canaries: `agreement: 8/8 scored items`.

Full run 1 already met the bar; I kept going only to understand and remove its one false rejection without losing agreement in any category.

**Package analysis**

`pkg-14` (zellij-org/zellij#5174, category `clear-accept`, gold label accept).

In full run 1 my rubric decided reject, failing `diagnosis-grounded`, `executable`, and `honesty`.
The original `diagnosis-grounded` row allowed "A plausible hypothesis ... if marked as such with a concrete way to resolve its uncertainty," and the plan states its mechanism as fact: "the reattach path wires the client's stdin to the session before the query responses have been consumed."
The grader wrote "the mechanism is not marked as a hypothesis."
`executable` read the plan's files line, "the client attach/reattach path in `zellij-server` (session connection handling) and `zellij-client`'s terminal query issuance; exact functions to be pinned in the PR after tracing the query issuance with debug logs," as two crates with no decision rule.
`honesty` held the comment's "0.44.1 clean, 0.44.2 on leaking" against a repro environment of "zellij 0.44.3 (cargo install)".

None of those is a contradiction in the package.
The repro's own summary says "every reattach on 0.44.x from 0.44.2 on prints the raw OSC responses ... the regression window and cache observation both reproduce," fresh creates are clean, and 0.44.1 is clean over 5 reattach cycles, which is the pattern the mechanism predicts.
The two crates are one attach flow with a stated tracing method, and the intended change, draining OSC responses before pane input is wired, is already specified.
So revision 2 changed the rules in general terms: a mechanism inferred from the observations passes when a bounded check can test it, tracing a named flow across cooperating modules is executable, and version claims are read against the whole reported window.

In the revision 2 partial run, `diagnosis-grounded` and `executable` passed but `honesty` still failed: "Claims debug logs are 'working' and 'the leak's origin is visible in zellij --debug output' ... none of this is in the package."
The same rule failed pkg-03 for "I have verified gzip, xz, and zstd locally," so the fault was in my rule, not in either plan: it treated any first-person preparatory check without pasted output as dishonest.
Revision 3 made `honesty` separate three kinds of first-person claim: uncontradicted preparatory testimony, a claimed fix or test result, and a claimed traced cause.

In the final full run my rubric decided accept on all seven checks, matching gold.
Its `honesty` evidence reads: "debug-logging claim is bounded preparatory testimony with 'exact functions to be pinned in the PR' as the open next step."

**Check rationale**

```text
| `diagnosis-grounded` | Cause claims in the plan and comment compared with the complete Repro evidence, controls, traces, issue history, and environment | The proposed mechanism fits the failing case and controls and does not contradict a trace or move the fix to a layer the reproduction rules out. A mechanism inferred from those observations is sufficient for a plan when it names a bounded investigation or verification that can check it; proof of every internal detail and the literal word 'hypothesis' are not required. Reject an unsupported causal leap with no concrete resolving check, or a claim that dismisses contrary evidence. | required |
```

The original row ended "A plausible hypothesis is allowed if marked as such with a concrete way to resolve its uncertainty."
That made the label decisive: in full run 1 it failed pkg-14 because "the mechanism is not marked as a hypothesis," even though nothing in the repro contradicted it.
The current row moves the test from wording to evidence.
The mechanism has to fit the failing case and the controls, and the plan has to name a check that could prove it wrong.
In the final run pkg-14 passed on "Fresh-attach-clean / every-reattach-leaks / 0.44.1-clean pattern fits the stdin-wired-before-query-consumed mechanism ... a bounded trace (zellij --debug)."

The reject side is kept explicit because the wrong-cause category depends on it.
All four wrong-cause packages still failed this row in the final run on a named contradiction, for example pkg-07: "the repro's control shows an instance-method misuse prints the friendly error correctly in the identical build," and pkg-16: "repro step 4 shows the table 'arrives as int64 with value 1; the zeros are already gone in the parsed table, before any cast to string could run.'"

**Trade-offs**

This row now lets a plausible mechanism pass before anyone has shown it is right, as long as it fits the evidence and names a check.
pkg-14's stdin-wiring explanation is never demonstrated in the package; the row accepts it because the plan's debug-log trace and repro loop would expose it.

That made the check more permissive on rejects as well, and the final run shows it.
`diagnosis-grounded` passed pkg-06 ("Preload-structure-mismatch mechanism matches issue's own suspicion and the repro control") and pkg-19, both of which failed it in run 1.
Both packages still rejected, pkg-06 on `scope-bounded`, `executable`, `verification-observable`, and `honesty`, and pkg-19 on `scope-bounded` and `thread-and-conventions`, so this row no longer catches an unproven cause on its own.

Two things limit that risk in the eval.
Contradiction still fails: all four wrong-cause packages failed this row on their controls or traces in the final full run and in every targeted run that included them (pkg-01 in revision 2; pkg-07, pkg-11, and pkg-16 in both).
The unbuildable canaries still hold: pkg-10, pkg-17, and pkg-18 failed both `diagnosis-grounded` and `executable` in the final run, for example pkg-17's "Only causal claim is 'mouse handling clearly changed somewhere between 0.61 and 0.62,' restating the repro's regression window with no proposed mechanism."

These are single runs, so not every per-check difference comes from this row: `thread-and-conventions`, whose rubric row did not change, also went from fail to pass on pkg-01, pkg-06, and pkg-17 between the two full runs, from grader variance or the other procedure edits.
A plan with a coherent but wrong cause that no control contradicts would pass this row, and I accept that miss rather than require proof before a plan is built.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
