# Plan for issue #72: fail closed on malformed stored password hashes

Issue: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72
Fork: https://github.com/hskl18/pathreview-ai301-fa26-s3
Author: hskl18
Base: 2f4e82f52efbcfcc57d65b3fa5348672163ca088
Branch: fix/72-malformed-password-hash
Built commit: 4e7ce33cf13e67e1e061eadc51f6e68d24cbfbaf
Status: implemented and pushed to my fork; the as-built plan and comment passed live plan-check run 5 with all seven checks passing.
Plan comment, posted after the build: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5925518483

## Reproduction evidence

My posted Unit 2 report is https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5806176715.
The report below is quoted verbatim; its output is the recorded before result, not an after-change result.

> I reproduced the malformed-hash behavior in #72 on my fork at commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088`, which is the same commit as `codepath/pathreview-ai301-fa26-s3` `main` at fork time.
>
> Environment: macOS 27.2, arm64; Python 3.11.15; passlib 1.7.4; bcrypt 4.3.0; pytest 9.1.1; uv 0.11.28.
> The focused unit test did not need the app, PostgreSQL, or Redis running.
>
> From a fresh clone of the fork:
>
> ```sh
> git clone https://github.com/hskl18/pathreview-ai301-fa26-s3.git
> cd pathreview-ai301-fa26-s3
> uv venv --python 3.11 .venv
> uv pip install --python .venv/bin/python -e '.[dev]'
> .venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format --runxfail -q --tb=short --disable-warnings
> ```
>
> The last command failed as follows:
>
> ```text
> tests/unit/test_security.py:227: in test_verify_with_wrong_hash_format
>     result = verify_password("password", wrong_hash)
> core/security.py:37: in verify_password
>     return bool(pwd_context.verify(plain_password, hashed_password))
> .venv/lib/python3.11/site-packages/passlib/context.py:2343: in verify
>     record = self._get_or_identify_record(hash, scheme, category)
> .venv/lib/python3.11/site-packages/passlib/context.py:2031: in _get_or_identify_record
>     return self._identify_record(hash, category)
> .venv/lib/python3.11/site-packages/passlib/context.py:1132: in identify_record
>     raise exc.UnknownHashError("hash could not be identified")
> E   passlib.exc.UnknownHashError: hash could not be identified
> 1 failed, 2 warnings in 0.97s
> ```
>
> The test's `wrong_hash` is `"not_a_valid_bcrypt_hash"`.
> Without `--runxfail`, the same test reports `1 xfailed`, because it carries a strict xfail marker for H-05.
>
> As a control, I ran the neighboring test, which asserts that a wrong password against a valid bcrypt hash returns `False`:
>
> ```sh
> .venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_password_incorrect -q --disable-warnings
> ```
>
> ```text
> 1 passed, 2 warnings in 0.52s
> ```
>
> Expected: verification against an unrecognizable stored hash returns `False`.
> Observed: passlib's `UnknownHashError` escapes from `verify_password` for the issue's malformed hash.
> The normal wrong-password case returns `False`, so the failure is specific to the unrecognizable stored hash rather than to verification generally.
>
> The traceback shows the exception surfacing from `pwd_context.verify()` at `core/security.py:37`; I have not isolated a cause beyond that call, and I have not tested other versions or a fix.
> This result is from the environment above only.

## Diagnosis

At this base commit, core/security.py's verify_password directly returns the result of pwd_context.verify without catching validation errors.
The posted traceback shows passlib's hash-identification path raising UnknownHashError for "not_a_valid_bcrypt_hash"; the valid-hash wrong-password control returns False.
Source inspection confirms the shared wrapper has no exception boundary, and api/routes/auth.py uses it in the login credential check.
That is enough to plan the helper change; the report does not establish an HTTP result from a running application.

On September 30, I probed the unchanged helper directly from the fork root with the same .venv (Python 3.11.15, passlib 1.7.4, bcrypt 4.3.0):

```sh
.venv/bin/python -c 'from core.security import verify_password
for h in ("not_a_valid_bcrypt_hash", "", "$2b$12$abc"):
    try: print(repr(h), verify_password("password", h))
    except Exception as e: print(repr(h), type(e).__name__, e)'
```

```text
'not_a_valid_bcrypt_hash' UnknownHashError hash could not be identified
'' UnknownHashError hash could not be identified
'$2b$12$abc' ValueError salt too small (bcrypt requires exactly 22 chars)
```

These are supplementary local observations, not claims that the Unit 2 report covered every malformed format.
The installed passlib 1.7.4 source defines UnknownHashError as a ValueError subclass and InternalBackendError as a RuntimeError subclass.
Its CryptContext.verify docstring documents ValueError when the hash matches no configured scheme or an argument has an invalid value, and TypeError when an argument has an invalid type: https://passlib.readthedocs.io/en/stable/lib/passlib.context.html and https://passlib.readthedocs.io/en/stable/lib/passlib.exc.html.

## Thread and existing work

As read on September 30, the issue thread has no maintainer or collaborator comments; classmates have posted claims, reproductions, and plans.
Open PR #78 (https://github.com/codepath/pathreview-ai301-fa26-s3/pull/78, unreviewed and unmerged) catches `(UnknownHashError, ValueError)` in verify_password and deletes the H-05 marker, but its diff adds no malformed-hash test cases.
Under the course house rules, parallel work on this shared issue does not block my own plan; this plan is built from my own reproduction and adds the empty and truncated-hash cases.
docs/CONTRIBUTING.md asks contributors to comment on the issue before working and states no AI-use policy for issue comments; its CI-green and PR-template rules apply to the later PR.

## Scope and files

One bounded change: malformed stored hashes produce False from the shared verification helper instead of escaping as validation exceptions.

- core/security.py: add a ValueError boundary around the existing pwd_context.verify call and clarify the returned-failure behavior in its docstring.
- tests/unit/test_security.py: remove only the issue #72/H-05 strict xfail marker and expand that malformed-hash regression to cover the issue string, an empty stored hash, and the truncated bcrypt-shaped string observed above.

Existing valid-password and wrong-password tests supply the successful and unsuccessful valid-hash controls.
No changes to password hashing, hash schemes, authentication routes, database contents, tokens, dependencies, other seeded bugs, or baseline suppressions.
Do not commit plan.md or comment.md to the implementation branch; the coursework repo holds the submitted plan.

## Approach

The sequence below is retained from the live-accepted draft.
The implementation and process differences are recorded under Deviations.

1. After the live skill accepts and my own plan comment is posted, create fix/72-malformed-password-hash from the verified base in this existing fork checkout.
2. Preserve the existing verification call and bool conversion; catch ValueError from that call and return False. Do not use a catch-all exception handler or return a successful authentication result on invalid input.
3. With explicit test-file authorization, remove the H-05 xfail and parameterize its existing assertion with the three observed malformed strings. Read each diff before keeping it.
4. Keep backend/runtime failures and programming TypeErrors visible rather than converting all exceptions to a credential mismatch.
5. Run the target and controls below, inspect the diff, and record actual before/after output. Fill Deviations after the build; re-grade and update the upstream comment if the built approach changes materially.

## Test plan

All commands run from the fork's root using its existing .venv; no application, database, or Redis writes are needed for this helper reproduction.

### Original reproduction through real code

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format --runxfail -q --tb=short --disable-warnings
```

Before: the quoted Unit 2 command reports UnknownHashError and 1 failed.
After: the issue-string case must return False, and the parameterized malformed cases must pass without validation exceptions.
Also run without --runxfail so the removed strict xfail cannot hide the regression or produce XPASS(strict).

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -q --tb=short --disable-warnings
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_password_correct tests/unit/test_security.py::TestSecurity::test_verify_password_incorrect -q --disable-warnings
.venv/bin/pytest tests/unit/test_security.py -q --disable-warnings
```

Expected: malformed stored hashes return False, matching valid credentials remain True, wrong credentials remain False, and the existing security suite has no failures or remaining H-05 xfail.
The existing long-password and empty-password-with-valid-hash tests must retain their current outcomes.

### Repository gates

```sh
make lint
.venv/bin/black --check .
make typecheck
make test-unit
```

Use black --check in place of make format's whole-repository writes; review any required formatting within the scoped files.
Record complete outcomes, including unresolved failures; do not rewrite unrelated tests or seeded-bug suppressions to make counts look green.
Integration and frontend CI requirements must be resolved before the Unit 4 PR; these helper checks alone do not establish a running HTTP login result or hosted CI readiness.

## Risks and unknowns

ValueError is broader than UnknownHashError and also covers some invalid-password value errors; these will fail closed as False, never grant access.
Catching only UnknownHashError would miss the locally observed truncated bcrypt hash, while a separate custom parser would duplicate passlib validation.
Unexpected runtime/backend errors and TypeErrors remain visible because they are not caught.
The existing long-password behavior, hash generation, and valid-hash controls must be verified after the change.
The local result is limited to Python 3.11.15, passlib 1.7.4, and bcrypt 4.3.0; no compatibility claim is made for untested combinations.
The observed helper and repository checks are recorded under Deviations and in the coursework Evidence field.
They do not establish an HTTP login result, hosted CI, or a merged fix.

## Deviations

The code follows the accepted draft's ValueError boundary and three malformed-hash cases.
I added two parameterized checks that inject TypeError and RuntimeError so the stated exception boundary remains covered; these stay in the planned security test file.
No additional source files, routes, dependencies, hash schemes, or database contents changed.

Process deviation: I built and pushed the branch before posting a plan comment upstream.
The accepted draft called for posting the plan before implementation; I did not follow that order.
I posted the plan comment on October 1, 2026 at 05:44 UTC, after the build: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5925518483

The three malformed-hash cases failed against the original helper, then passed after the change with and without --runxfail.
The security suite had 29 passed, and the repository unit suite had 380 passed and 52 expected failures for other seeded bugs.
Lint, Black, mypy, and the 18 frontend tests passed.
Integration collected no tests and exited 5; the repository CI explicitly accepts that empty-suite outcome.
The built source and test commit is 4e7ce33cf13e67e1e061eadc51f6e68d24cbfbaf.
The as-built plan and comment received accept with all seven checks passing in live plan-check runs 4 and 5; run 5 graded the exact comment text that was then posted.
The plan-check skill files are unchanged from the complete 20/20 eval.


### Original reproduction after the fix

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format --runxfail -q --tb=short --disable-warnings
```

```text
...                                                                      [100%]
3 passed, 2 warnings in 0.32s
```


### The same regression without an xfail override

```sh
.venv/bin/pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -q --tb=short --disable-warnings
```

```text
...                                                                      [100%]
3 passed, 2 warnings in 0.17s
```


### The security suite, including the valid-hash controls and exception propagation checks

```sh
.venv/bin/pytest tests/unit/test_security.py -q --disable-warnings
```

```text
.............................                                            [100%]
29 passed, 2 warnings in 4.88s
```
