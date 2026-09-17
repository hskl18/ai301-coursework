# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72

**Verdict output**

Live-mode run over three candidates (#72, #69, #73), pasted verbatim. The ranked
read-out puts #72 first; the fenced JSON block carries the per-issue verdicts,
accepted first in rank order, and records `"verdict": "accept"` for #72.

````
All three are in-scope (`codepath/pathreview-ai301-fa26-s3`), and all three clear every required check. Repo-level evidence is shared: not archived, human commit today (`Aburke225`, 2026-09-16), no releases published so graded on push recency (pushed 2026-09-16), and no AI policy anywhere (`docs/CONTRIBUTING.md`, PR template, issue templates all silent; no `AI_POLICY.md`) — silence passes. Preferred `fast-first-response` passes off issue #52 (opened 2026-09-10, collaborator reply 2026-09-16 = 6 days).

Per-issue: each was filed by `Aburke225` (COLLABORATOR) and carries four labels including `good first issue`; each has 0 comments, 0 assignees, and the repo has no pull requests at all (open or closed), so `spec-settled` and `unclaimed` pass cleanly. House rule on classmate claims never had to fire — nothing to ignore.

**Ranked (accepted, fit order):**

1. **#72 — `verify_password` raises `UnknownHashError`** — tightest acceptance criteria of the three: `tests/unit/test_security.py:218` already holds a `strict=True` xfail asserting `verify_password("password", "not_a_valid_bcrypt_hash") is False`, so the fix has a binary pass signal. Python, one fail-closed guard in `core/security.py:36`, 1-2 hours, and it exercises the repo's conventions (marker removal + five CI jobs) which is exactly the skill you said you want to practice.
2. **#73 — README vs `.env.example` key mismatch** — verified the disagreement directly: README says add `OPENROUTER_API_KEY`, `.env.example` offers only `mock`/`openai` and lists `OPENAI_API_KEY`. Plain markdown + env file, 1-2 hours, docs/DX as preferred. Ranks below #72 only because it has no test behind it and leaves you one small judgment call about which file is canonical.
3. **#69 — output parser JSON array fallback** — same xfail structure (`tests/unit/test_output_parser.py:141`), but 2-4 hours and the biggest surface of the three.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
    "checks": [
      {"name": "repo-not-archived", "grade": "pass", "evidence": "repo metadata: \"isArchived\": false"},
      {"name": "maintainer-active", "grade": "pass", "evidence": "human commit 2026-09-16T21:42:18Z by Aburke225 (Andrew Burke), 0 days old"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "latest release: none published; pushedAt 2026-09-16T21:50:20Z (same day)"},
      {"name": "one-bounded-task", "grade": "pass", "evidence": "one fail-closed guard in core/security.py plus removing the H-05 xfail marker; \"Estimated effort: 1-2 hours\""},
      {"name": "spec-settled", "grade": "pass", "evidence": "0 comments; repo has no PRs at all, so 0 closed-unmerged linked PRs"},
      {"name": "maintainer-triaged", "grade": "pass", "evidence": "filed by Aburke225 [COLLABORATOR]; labels bug, good first issue, api, tier-1 applied 2026-09-10"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees: none; no linked or mentioned PRs; 0 comments so no claim comments"},
      {"name": "ai-policy-permits", "grade": "pass", "evidence": "docs/CONTRIBUTING.md, PR template and issue templates mention no AI policy; AI_POLICY search total_count 0"},
      {"name": "fast-first-response", "grade": "pass", "evidence": "issue #52 opened 2026-09-10, first COLLABORATOR reply 2026-09-16 = 6 days"},
      {"name": "newcomer-sized", "grade": "pass", "evidence": "\"good first issue\" label plus named files core/security.py and tests/unit/test_security.py"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
    "checks": [
      {"name": "repo-not-archived", "grade": "pass", "evidence": "repo metadata: \"isArchived\": false"},
      {"name": "maintainer-active", "grade": "pass", "evidence": "human commit 2026-09-16T21:42:18Z by Aburke225 (Andrew Burke), 0 days old"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "latest release: none published; pushedAt 2026-09-16T21:50:20Z (same day)"},
      {"name": "one-bounded-task", "grade": "pass", "evidence": "\"Make the two files agree\" across README.md and .env.example; \"Estimated effort: 1-2 hours\""},
      {"name": "spec-settled", "grade": "pass", "evidence": "0 comments; repo has no PRs at all, so 0 closed-unmerged linked PRs"},
      {"name": "maintainer-triaged", "grade": "pass", "evidence": "filed by Aburke225 [COLLABORATOR]; labels bug, good first issue, docs, tier-1 applied 2026-09-16"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees: none; no linked or mentioned PRs; 0 comments so no claim comments"},
      {"name": "ai-policy-permits", "grade": "pass", "evidence": "docs/CONTRIBUTING.md, PR template and issue templates mention no AI policy; AI_POLICY search total_count 0"},
      {"name": "fast-first-response", "grade": "pass", "evidence": "issue #52 opened 2026-09-10, first COLLABORATOR reply 2026-09-16 = 6 days"},
      {"name": "newcomer-sized", "grade": "pass", "evidence": "\"good first issue\" and \"docs\" labels plus named files README.md and .env.example"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69",
    "checks": [
      {"name": "repo-not-archived", "grade": "pass", "evidence": "repo metadata: \"isArchived\": false"},
      {"name": "maintainer-active", "grade": "pass", "evidence": "human commit 2026-09-16T21:42:18Z by Aburke225 (Andrew Burke), 0 days old"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "latest release: none published; pushedAt 2026-09-16T21:50:20Z (same day)"},
      {"name": "one-bounded-task", "grade": "pass", "evidence": "handle array responses in rag/generator/output_parser.py fallback plus removing the H-02 xfail; \"Estimated effort: 2-4 hours\""},
      {"name": "spec-settled", "grade": "pass", "evidence": "0 comments; repo has no PRs at all, so 0 closed-unmerged linked PRs"},
      {"name": "maintainer-triaged", "grade": "pass", "evidence": "filed by Aburke225 [COLLABORATOR]; labels bug, good first issue, rag, tier-1 applied 2026-09-10"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees: none; no linked or mentioned PRs; 0 comments so no claim comments"},
      {"name": "ai-policy-permits", "grade": "pass", "evidence": "docs/CONTRIBUTING.md, PR template and issue templates mention no AI policy; AI_POLICY search total_count 0"},
      {"name": "fast-first-response", "grade": "pass", "evidence": "issue #52 opened 2026-09-10, first COLLABORATOR reply 2026-09-16 = 6 days"},
      {"name": "newcomer-sized", "grade": "pass", "evidence": "\"good first issue\" label plus named files rag/generator/output_parser.py and tests/unit/test_output_parser.py"}
    ],
    "verdict": "accept"
  }
]
```
````

---

## Eval iterations

**Run history**

One run: 20/20. I wrote the rubric out in full before grading anything, then ran
the whole eval set once with `--save-run`. The committed `eval-run.txt` ends with
`agreement: 20/20 scored items  (bar: 18/20: PASS)` over
`categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 4/4`.
No `--only` re-grades followed, because there were no disagreements to chase.

**Issue analysis**

`issue-20` (excalidraw/excalidraw#11811, "Add company logo shape to the toolbar").
My rubric decided **reject**; the gold label is **reject**. Nine of my ten checks
passed it. The repo is plainly alive (`all 5 default-branch commits dated
2026-08-04, authored by humans (dwelle, yanrin13, nihaarsirikonda)`), nothing is
claimed, and even `one-bounded-task` passed on `single new toolbar shape
(place/resize/move/export), with custom-upload/branding explicitly deferred out
of v1`. The single fail was `maintainer-triaged`: `opened by cursor[bot] (NONE);
labels: none; 0 comments so no maintainer endorsement`. Every required check
gates the verdict, so that one fail decided it. That is the read I wanted: a
well-written feature wish that nobody with repo rights has agreed to is a product
decision waiting to happen, not a first issue, and the tidiness of the body does
not change that.

**Check rationale**

`maintainer-triaged` (required), quoted as it currently stands in
`tools/issue-select/rubric.md`:

> Pass if any one holds: the issue was filed by someone with repo rights
> (`OWNER`, `MEMBER`, `COLLABORATOR`); or it carries at least one label
> (only accounts with triage rights can label an issue, so a label is a
> maintainer's hands on it); or an owner/member/collaborator comment
> endorses the work.
>
> Fail when an outside account filed it, no label was ever applied, and no
> maintainer has replied. An untriaged outside request is a proposal
> awaiting a product decision, not work anyone has agreed to.

It stands as three cheap proxies for one expensive question — has anyone who can
merge this agreed it should exist? — because none of the other nine checks ask
it. The liveness, scope, and claim checks all quietly assume the work is wanted.
I made it an OR of three signals rather than one rule because repos triage
differently: some label everything and comment on nothing, others have
maintainers file their own bugs and never label them. Requiring all three would
sink maintainer-filed issues that carry no labels; keeping only the label clause
would sink `issue-16`, where the label exists but the author association is the
stronger signal.

**Trade-offs**

It buys the `issue-20` verdict and pays with false rejects on good untriaged bug
reports from outsiders. `issue-02` is the visible instance in my run: a clean,
reproducible BSD-`sed` bug where `one-bounded-task` and `newcomer-sized` both
passed (`body names the exact sed line to fix and gives the portable
replacement`), while `maintainer-triaged` failed on `author sermelipharo is NONE,
labels: none, both commenters are NONE association`. There it changed nothing,
because `maintainer-active` and `repo-in-use` had already sunk the issue — a dead
repo triages nothing. In a living repo the same shape, a good outsider bug report
filed yesterday before a maintainer got to it, would be rejected, and I accept
that: I would rather wait a week for a label than write a patch nobody asked for.
The proxy runs the other way too — one stale label passes the check with no human
judgment behind it — and that is the clause I would tighten first if a live
candidate ever slipped through on it.

---

## Selection rationale

**Selection rationale**

1. **Fit and time.** #72 is Python, one fail-closed guard in `core/security.py`,
   and the issue itself estimates 1-2 hours — which matches the few evening hours
   I have. It also sits on an auth path, which is the kind of small, checkable
   correctness fix I would rather practice on than a UI feature.
2. **What the verdict caught, and what I weighed on top.** The rubric confirmed
   the mechanical things: repo alive (human commit the same day), no assignee, no
   PRs in the repo at all, four labels including `good first issue` from a
   COLLABORATOR, and no AI policy to trip over. What it cannot see is that #72
   comes with a `strict=True` xfail at `tests/unit/test_security.py:218` already
   asserting the behaviour, so the fix has a binary pass signal instead of my own
   judgment about whether it is done. #73 was the close second and I passed on it
   because it has no test behind it and leaves a judgment call about which file is
   canonical; #69 is the same shape as #72 but 2-4 hours over a larger surface.
3. **Claiming.** Low friction and one real risk. Nothing blocks the claim: 0
   comments, 0 assignees, and the Path Review house rule means classmates' claims
   would not block me anyway. The risk is that #72 is a tier-1 `good first issue`
   in a classroom repo, so several of us may land on it; that costs nothing for
   credit, but I should expect a shared thread and write a claim comment that says
   specifically what I plan to change rather than "taking this".

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
