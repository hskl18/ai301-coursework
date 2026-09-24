# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

hskl18

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5806149675

I'd like to investigate #72 in `core/security.py`.
The issue says `verify_password("password", "not_a_valid_bcrypt_hash")` should return `False`, but passlib's `UnknownHashError` escapes.

I'll rerun the existing H-05 test with `--runxfail` in a clean checkout, recording the commit and the Python, passlib, and bcrypt versions, so its actual result is visible.
I'll compare the malformed stored hash with a valid bcrypt hash and post the exact steps and output in a separate report, including if the behavior differs from the issue.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5806176715

I reproduced the malformed-hash behavior in #72 on my fork at commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088`, which is the same commit as `codepath/pathreview-ai301-fa26-s3` `main` at fork time.

Environment: macOS 27.2, arm64; Python 3.11.15; passlib 1.7.4; bcrypt 4.3.0; pytest 9.1.1; uv 0.11.28.
The focused unit test did not need the app, PostgreSQL, or Redis running.

From a fresh clone of the fork:

```sh
git clone https://github.com/hskl18/pathreview-ai301-fa26-s3.git
cd pathreview-ai301-fa26-s3
uv venv --python 3.11 .venv
uv pip install --python .venv/bin/python -e '.[dev]'
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format --runxfail -q --tb=short --disable-warnings
```

The last command failed as follows:

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

The test's `wrong_hash` is `"not_a_valid_bcrypt_hash"`.
Without `--runxfail`, the same test reports `1 xfailed`, because it carries a strict xfail marker for H-05.

As a control, I ran the neighboring test, which asserts that a wrong password against a valid bcrypt hash returns `False`:

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_password_incorrect -q --disable-warnings
```

```text
1 passed, 2 warnings in 0.52s
```

Expected: verification against an unrecognizable stored hash returns `False`.
Observed: passlib's `UnknownHashError` escapes from `verify_password` for the issue's malformed hash.
The normal wrong-password case returns `False`, so the failure is specific to the unrecognizable stored hash rather than to verification generally.

The traceback shows the exception surfacing from `pwd_context.verify()` at `core/security.py:37`; I have not isolated a cause beyond that call, and I have not tested other versions or a fix.
This result is from the environment above only.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

One run: 20/20.

That single full run is the one `eval-run.txt` records.
Its agreement line reads `agreement: 20/20 scored items  (bar: 18/20: PASS)`, and its category line reads `categories: clear-accept 8/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`.
No `--only` re-run and no second full run followed, because the first full run cleared the 18/20 bar with a match in every category, including the single-package `disclosure` category that sets the floor.

**Package analysis**

`pkg-20`.
My rubric decided **reject**, and the gold label is **reject**, so the two agree.

This is the eval set's only `disclosure` package, so it is the single item that decides the category floor.
Six of my seven required checks passed on it: the report's environment line, its verbatim config and query commands, its trigger, its captured `^[[?997;2n` versus `^[[?997;1n` artifact, and its bounded expected/actual statement all held up.
The package failed on one required check, `repo-conventions`, which is what produced the reject.

My rubric read it that way because that check keys disclosure on the scope the repo's own stated policy covers.
The bundle's Repo facts state the policy as "All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance; the human in the loop must fully understand the work; AI-assisted issues and comments must be reviewed and edited by a human before submission".
That names issue comments, not pull requests only, so the requirement reaches this candidate claim comment and report - and neither one names a tool or an extent of assistance.
Under my verdict rule, one required `fail` is enough: "Any required `fail` or `unclear` makes the verdict **reject**; missing proof is not a pass."

**Check rationale**

The final row of the checks table, quoted exactly as it reads now:

> | `repo-conventions` | Repo-facts bug-report asks and contribution/AI policy compared with both comments and report | Supplies the substance of relevant requested context and obeys requirements for issue comments, including AI-use disclosure with tool and extent when the repo requires it. A PR-only disclosure rule does not impose disclosure on issue comments; no literal template headings or extra boilerplate are required. | required |

It reads that way because a disclosure check has two opposite ways to fail, and the wording has to block both.

The first is under-reading.
A check that only asked "does the comment follow the repo's conventions" never reaches AI disclosure at all, which loses `pkg-20` and with it the whole `disclosure` category, and the category floor means no score elsewhere can make that up.
So the pass condition names disclosure explicitly, and names what a sufficient disclosure contains: the tool and the extent.

The second is over-reading, which is what the second sentence exists to stop.
"A PR-only disclosure rule does not impose disclosure on issue comments" keeps the check from firing on every package whose repo mentions AI anywhere, and the evidence guide carries the same boundary: "If the policy requires AI disclosure for all use in issues or comments, a candidate assisted by AI must name the tool and extent; disclosure only for pull requests is not an issue-comment requirement."
A check that rejected any undisclosed comment in an AI-mentioning repo would have turned accept-labelled packages into rejects and cost agreement in `clear-accept`.

I rejected a template-conformance reading in favour of "supplies the substance of relevant requested context ... no literal template headings or extra boilerplate are required", so a terse report that answers the template's asks in prose still passes.

**Trade-offs**

Nothing changed after the run, and here is how I know: the one full run agreed on all 20 scored packages, so there was no disagreement to chase, no check to loosen, and therefore no canary to re-run with `--only`.
The trade-off below is one I accepted when writing the check, not one a re-run forced.

What `repo-conventions` gives up is the unwritten convention.
It decides disclosure from stated policy only, and my rubric says so directly: "Use only the bundle's stated policy to decide whether disclosure is required in issue comments; do not infer a requirement from silence or from a PR-only rule."
So a repo where maintainers plainly expect AI disclosure but never wrote it into CONTRIBUTING.md gets a pass from this check, and a package that would annoy a real maintainer is graded ready.

I took that cost on purpose, because the alternative costs more.
Inferring a requirement from silence means every package in the set is a candidate for a disclosure failure, which converts accepts into rejects across `clear-accept` - eight scored packages - to protect one.
The live case shows the same boundary working in the direction it was built for: the Path Review repo states no AI-use policy in `docs/CONTRIBUTING.md`, `.github/`, or `README.md`, so this check does not demand disclosure of my own comments there, and it would demand it the moment that policy named issue comments.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
