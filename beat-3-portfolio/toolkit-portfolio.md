# Toolkit Portfolio

**Student:** Hanbin Tan

## Featured Tools

I picked these four because each one did live work this term and each one changed after it hit a real case.
issue-scout graded the issue my whole contribution came from.
The voice guide and guard touched almost every word I sent upstream.
The opensource skill took the same workflow outside the course and produced merged pull requests I did not expect when the term started.
The ship gate is where pr-precheck stopped being an eval tool and ran on a real pull request.

**issue-scout**

**What it is, and the judgment hole I wrote:** issue-scout searches GitHub for a first issue instead of grading one issue I already have.
It runs four queries, narrows the results, and grades the top candidates with a rubric I wrote.
The rubric has ten checks.
The judgment part is the boundary rules in that rubric.
I decide what counts as one piece of work, what counts as a repository I can work in, and when an issue is already taken even if it is still open.
It grew out of issue-select from Unit 1, which graded one candidate at a time and reached 20 out of 20 on its eval run in commit b9d6687 on September 16, 2026.

**How it evolved, dated:**

- 2026-10-14, I built issue-scout and ran its first scan.
  Four queries returned 400 results, I narrowed them to 139 repositories, and I graded the top five.
  Two full eval runs came back 19 out of 20.
  The misses came from one rule I had written too loosely, and in the second, a short list of missing variants in one component got read as an open ended feature list.
  I added to the umbrella rule after each miss, and the next complete run reached 20 out of 20.
- 2026-10-21, I changed the central check again for Unit 6.
  I replaced the one bounded task test with the staff scope-feasible row, and I split difficulty away from acceptance, so a hard issue could pass and carry a difficulty note instead of failing.

**Evidence:** The before and after of that central check, from my own rubric files.

```text
Before, tools/issue-select/rubric.md, commit b9d6687
Pass if the body asks for one change a newcomer could finish in a single
pull request. Fail if it is an umbrella or tracking issue: a list of other
issue numbers, a self-described "megaissue", or an open-ended program such
as "incrementally add X across the codebase".

After, the rubric behind the 20/20 run on 2026-10-14
(unit5-drafts/eval-runs/full-08-inputs/rubric.md)
Several possible causes or implementation suggestions for one observable bug
do not by themselves make an umbrella.
Completing the same behavior for a finite set of cases, variants or supported
operations in one component can also be one task; do not count each example as
an independent feature.
A trailing "etc." in a terse report does not by itself establish an ongoing
program when the title and examples identify that single component behavior.
```

```text
From scan-notes.md
All 20 calls completed, agreement was 19/20, all five category floors passed, and the harness exited 0 with a complete generated transcript.
`full-06` corrected the performance-report false negative but still scored 19/20 because a short list of missing variants in one component was misread as an open-ended feature list.
`partial-07` matched 5/5, then the independent complete `full-08` run matched 20/20 with every category perfect and no call errors.
```

The live result of its direct grading is in my contribution story.
The scout passed Altinn issue 10955, and that became pull request 21606.

**voice guide and voice guard**

**What it is, and the judgment hole I wrote:** The voice guide is one file that holds my rules for writing upstream.
I merged the rules from the Unit 2 to 4 skills into it, and I added rules for claims, questions, and pings.
Three live skills read the same guide.
The guard is a hook that runs check_voice.py on outgoing GitHub commands and stops a command when the body breaks a rule in the guide or when it cannot read a body at all.
The judgment is the guide itself.
Every rule in it is a line I drew about what I will and will not say to a maintainer.

**How it evolved, dated:**

- 2026-10-21, I installed the guide and the guard, and the first version already stopped a real command that day because the body file path did not resolve.
- 2026-10-25, the first dated rule in the log is the one about skipping praise, emoji, and grand claims.
- 2026-10-29, the rule against a guaranteed fix or a delivery date, and the rule about offering a first step and a report back window instead.
- 2026-11-02, the disclosure rules, naming the AI tools in Notes for Reviewers and disclosing assistance in every course pull request.
- 2026-11-03, the rule about asking one question after showing the attempt.
- 2026-11-04, three rules triggered stops in one day: never promise a fix before the evidence exists, mark a suspected cause as a hypothesis until a test isolates it, and do not claim I personally typed or ran work that an agent did.
- 2026-11-05, the rule against an untested root cause claim.

**Evidence:** From guard-log.md.
Between 2026-10-21 17:20 and 2026-11-07 21:07 the guard ran 429 checks, passed 338, and stopped 91.
Two stops from the log, word for word.

```text
- 2026-10-21 18:11 [hook] stop: could not read the body file: [Errno 2] No such file or directory: '/Users/ice/school/codepath/ai301/unit6-drafts/claim-post-01/claim-draft | target: gh issue comment https://github.com/Altinn/altinn-studio/issues/10955 --body-file
- 2026-10-21 18:12 [hook] pass | target: gh issue comment https://github.com/Altinn/altinn-studio/issues/10955 --body-file
- 2026-10-28 19:10 [hook] stop: rule broken: "Skip praise, emoji, grand claims, and extra headings that do not help a reader rerun the case." | target: gh pr create --repo Altinn/altinn-studio
- 2026-10-28 19:15 [hook] pass | target: gh pr create --repo Altinn/altinn-studio
```

The October 28 stop was an emoji attribution line in my pull request body.
I had it removed, the guard passed five minutes later, and pull request 21606 opened.

```text
Two rules in ~/.claude/voice-guard/voice-guide.md that none of my Unit 2-4 guides in tools/ has
#### Rule: Offer a first step and a report-back window
Name the reported behavior, the first check I intend to run, and a realistic window for reporting results or a blocker, even if I cannot reproduce it.
#### Rule: Ask one question after showing the attempt
Read the relevant documentation and thread, then include the command or steps I tried, the observed result, and one question the maintainer can answer.
```

```text
What each dated rule above stopped the first time: time and target from guard-log.md, draft line as the guard quoted it
2026-10-25 08:41 | gh pr create --base preview | Skip praise, emoji, grand claims | "🤖 Generated with [Claude Code](https://claude.com/claude-code)"
2026-10-29 00:27 | shopnex-ai/shopnex#47 claim draft | A guaranteed fix, delivery date, or request to reserve an issue | "... and I'll open a PR for it today."
2026-10-29 00:27 | same draft, next version | Offer a first step and a report-back window | "... and the PR will link back here."
2026-11-02 22:46 | PR bodies moving CLAUDE.md into AGENTS.md in my own repos, not course PRs | Disclose assistance in every course PR | "The whole draft: it has no Notes for Reviewers section and never names the AI tools used or what they helped with ..."
2026-11-03 19:05 | CherryHQ/cherry-studio claim draft | Ask one question after showing the attempt | "Is the main-process, memory-only queue still the direction you want, and should I wait for #22093 to settle what happens after `error` and `aborted`?"
2026-11-04 01:52 | doobidoo/mcp-memory-service#1852 claim draft | Never promise a fix or a deadline before the evidence exists | "I'll report back here within two days, with the PR or with whatever blocks it."
2026-11-04 12:12 | grafana reply to a reviewer | Trace the code, but mark a suspected cause as a hypothesis | "because `maxTextWidth` is too narrow once the browser adds letter spacing that `calculateFontSize` does not measure."
2026-11-04 22:14 | PR body for my own repo boring-agent-memory | Do not claim I personally typed, ran, reviewed, or rewrote work that an agent did for me | "I ran the README's commands from a wheel in a clean environment outside the repository, including the config, stdio and Python examples."
2026-11-05 22:49 | super-productivity#11434 PR comment | An untested root-cause claim | "This run's merge ref was built at 08:06 UTC that day, so it ran the old test. I haven't rerun it here."
```

```text
Two edits to voice-guide.md and the stops before them, from guard-log.md and the guide
- 2026-10-29 12:42 [hook] stop: rule broken: "A guaranteed fix, delivery date, or request to reserve an issue." | target: gh issue comment 536 -R  (draft line: "/assign")
  Added 2026-10-29 16:37: Exception: a comment that is nothing but one repository command, a single line of slash-command syntax such as `/assign` or a CLA bot's exact signature sentence, is not a request to reserve, and none of the rules for writing a claim apply to it
- 2026-10-29 16:47 [manual] pass | target: .../scratchpad/vg/assign.md
- 2026-10-29 16:48 [manual] stop: rule broken: "A guaranteed fix, delivery date, or request to reserve an issue." | target: .../scratchpad/vg/prose.md
- 2026-11-05 16:19 [hook] stop: rule broken: "In Notes for Reviewers, name the AI tools and what they actually helped with: investigation, code, tests, checks, or writing." | target: gh pr create -R ruvnet/ruflo
  Added 2026-11-05 17:20: This rule covers only PRs made for the CodePath AI301 course, such as Altinn/altinn-studio.
- 2026-11-05 17:23 [hook] pass | target: gh pr create -R ruvnet/ruflo
```

**opensource skill**

**What it is, and the judgment hole I wrote:** The opensource skill is the course workflow running outside the course.
It scans repositories, grades issues, and drives the work after I pick or approve one.
The agents do the scanning, the reproduction, the code, the tests, and the draft text.
I pick or approve the issue, I approve every piece of text before it goes out, I sign the CLA when a repository asks for one, and I make the calls when two reasonable options conflict.
Every outgoing text passes the voice guard above, and plans and code pass a Sol review before a pull request opens.
The judgment part is my profile for it, which repositories and issue shapes it should look for, and the rules I keep adding to that profile after something goes wrong.

**How it evolved, dated:**

- 2026-10-29, my first pull request from the opensource skill, shopnex 74, merged 29 minutes after it opened.
  An independent review then scored it 7 out of 10 because it ignored the issue asking for one example only, and it did not follow the install style in the README next to it.
  I added a rule after that: what the issue asks for and what the maintainer already does come before my own preference.
- 2026-10-30, I learned that popular repositories often ban AI from good first issues, beets, blockly, and Qiskit among them.
  I added repo_queries to the profile, ts-popular and py-popular, scanning help wanted on repositories over 5k stars, and I made the scan halve per_query when GitHub reports resource limits.
- 2026-11-01, a Sol reviewed rework landed: a follow command that prints the live state of every pull request in review at once, ledger append, atomic ledger writes with a check after writing, retries on 5xx errors, bot opened issues removed, and work files kept in a folder next to the clone.
- 2026-11-02, I changed the order rule from returning repositories first to new repositories first.
- 2026-11-03, nanocoder 1929 was claimed by someone else about an hour after my scan, while it sat waiting for my confirmation.
  I changed the rule so repositories that need a claim first get the claim text at once.

**Evidence:** My ledger as of 2026-11-07, after 19 scans from 2026-10-29 to 2026-11-05.
The ledger has 123 rows: rejected 71, accepted 23, dropped 7, closed 2, waiting 2, pull request open 9, merged 9.
The nine merged pull requests span five repositories and total plus 2349 and minus 91 lines.

```text
From ~/.claude/skills/opensource/profile.md, the repo_queries change
`ts-popular` and `py-popular` trace to "bounded bug fixes ... in TypeScript, Python" and to the user's ask on 2026-10-30 to prefer repos with more stars.
They look for `help wanted` because popular repos often keep `good first issue` for people working without AI (beets, blockly and Qiskit ban AI on that label).
```

| Pull request | Change | Opened (UTC) | Merged (UTC) |
|---|---|---|---|
| [shopnex 74](https://github.com/shopnex-ai/shopnex/pull/74) | docs | 10-29 07:44 | 10-29 08:13, 29 minutes |
| [ordewell 140](https://github.com/ordewell/ordewell/pull/140) | docs | 10-29 09:26 | 10-29 10:40 |
| [dex 952](https://github.com/exmergo/dex/pull/952) | DuckDB seed fix | 10-30 01:17 | 10-30 10:04 |
| [Sentient 537](https://github.com/existence-master/Sentient/pull/537) | forget tool fix | 10-29 20:25 | 10-31 04:45 |
| [dex 1025](https://github.com/exmergo/dex/pull/1025) | Snowflake estimate fix | 11-01 04:51 | 11-01 09:59 |
| [ordewell 142](https://github.com/ordewell/ordewell/pull/142) | composer tip | 11-01 07:01 | 11-01 17:57 |
| [dex 1052](https://github.com/exmergo/dex/pull/1052) | explore profile fix | 11-02 07:44 | 11-02 10:51 |
| [meta astryx 9719](https://github.com/meta/astryx/pull/9719), 14,712 stars | hook docs | 11-03 06:15 | 11-03 09:31 |
| [Sentient 548](https://github.com/existence-master/Sentient/pull/548) | memory fix | 11-02 09:13 | 11-07 16:25 |

A maintainer review, word for word, on Sentient 548.

```text
Thanks @hskl18, this does exactly what #547 asked for, and your real-test
notes matched what I saw. Approving.
```

The astryx pull request is the new repositories first rule paying off the next day.
It opened on November 3 and merged in 3 hours and 16 minutes.

**pr-precheck and ship gate**

**What it is, and the judgment hole I wrote:** pr-precheck is my Unit 4 tool.
It grades a pull request package against the plan it claims to follow and the issue behind that plan, and it answers one question: is this ready to submit.
The judgment part is its rubric, which I wrote.
The ship gate is what pr-precheck turned into on live work.
I wrote a manifest, ship-manifest.md, that lists the four checks from the Altinn frontend CI, unit tests, typecheck, ESLint with Prettier, and spell quick, with the workflow file each one came from.
The gate runs those four project checks and the six pr-precheck checks before a pull request is allowed to open.

**How it evolved, dated:**

- 2026-10-08, pr-precheck landed in commit 2c7ed2e as an eval facing tool.
- 2026-10-28, I wrote the ship manifest from the Altinn frontend CI.
  The first baseline run found two setup problems before it found anything about my change: my sparse checkout was missing testdata, and my reproduction test carried an unused import.
  I fixed both.
  The gate then passed all four project checks and all six pr-precheck checks.
  The voice guard stopped the pull request body over the emoji line described above, I had it removed, and the gate ran again before the pull request opened.
  After pull request 21606 opened, I removed the ship gate hook and kept the gate files and the manifest.

**Evidence:** One row from ship-manifest.md, and the two notes under the table.

```text
| Typecheck | `npx --yes --package=node@22 -- node .yarn/releases/yarn-4.18.0.cjs workspace studio-designer-frontend typecheck` | .github/workflows/designer-frontend-unit-tests.yml, step Doing the typecheck (`yarn typecheck` in src/Designer/frontend) |

The CI job's `yarn strict-null-checks` is not listed because tsconfig-strict.json only includes `libs`, which this change does not touch.
On main c298f416 (2026-10-28) every row passed except the untracked #10955 reproduction test, which failed by design and was removed from the checkout after its after-fix run.
```

```text
From the real gate run, unit7-drafts/gate-run-01/stdout.txt, started 2026-10-28 19:05 PDT, exit 0
ship-gate: PASS. fix/10955-keep-selected-component passed your manifest's checks and your pr-precheck. Open the PR through Claude Code within 30 minutes, without changing anything, and the ship-gate lets it through without running again.
  repo check Designer frontend unit tests: ok (114s)
  repo check Typecheck: ok (5s)
  repo check ESLint and Prettier: ok (85s)
  repo check Spell check of changed files: ok (2s)
```

## Inventory

- issue-select, Unit 1, commit b9d6687 on 2026-09-16, graded one candidate issue at a time and reached 20 out of 20, and issue-scout grew out of it in Unit 5.
- repro-check, Unit 2, commit 4bec228 on 2026-09-23, 20 out of 20, grades a claim and reproduction package before it posts, and on 2026-10-21 I added a report back window that does not promise a fix date.
- plan-check, Unit 3, commit c9fa271 on 2026-09-30, 20 out of 20, grades a plan package before I build from it, and it still carries a wording conflict I found on 2026-10-28 between its rubric and its procedure on reporting finished results honestly, which I left in place and recorded.
- repo memory, Unit 6, a CLAUDE.local.md file holding the Altinn build and test commands, with a 9 out of 9 AppContext baseline when I set it up.
- pr-monitor, installed 2026-10-28, watches my open pull request and drafts replies from a playbook built on my voice guide, and its first full run is in the arc below because its draft could not be sent.
- Sol review loop, the cdx review pass that plans and code go through before anything ships, with one to three rounds recorded on most of my external pull requests.

## The Arc

**Beat 1**
Date: October 14, 2026
Friction: issue-scout read a short list of missing variants in one component as an open ended feature list, and two full eval runs stopped at 19 out of 20
Change: I added to the umbrella rule in the rubric, saying several fixes for one behavior, or a finite set of variants in one component, do not make an issue an umbrella issue
Result: The next complete run reached 20 out of 20

**Beat 2**
Date: October 21, 2026
Friction: The voice guard stopped my claim comment on Altinn 10955 because it could not read the body file at a relative path
Change: I had Claude switch the command to an absolute path and post the claim through the guard instead of around it
Result: The guard passed at 18:12 and the claim posted once, and the same guard is still running, with 429 checks logged by November 7

**Beat 3**
Date: October 28, 2026
Friction: The ship gate baseline failed on my own setup, a sparse checkout missing testdata and an unused import in my reproduction test
Change: I added the missing folders, removed the import, and ran the four manifest checks and the six pr-precheck checks as one gate
Result: The gate passed in full, and after the voice guard stop on the emoji line was cleared, pull request 21606 opened that evening

**Beat 4**
Date: October 28, 2026
Friction: The pr-monitor draft for that same pull request picked the wrong discard path, called my local deletion fix unrelated, and its three passing summary missed six workflows waiting for approval
Change: I kept the draft local and had Codex write a corrected version from the Actions API instead of the summary
Result: No reply went out from that draft, and the replies that did go out waited until November 3, after the fixes reached beee7db6 and I approved them

**Beat 5**
Date: October 29, 2026
Friction: My first pull request from the opensource skill merged in 29 minutes, and an independent review still scored it 7 out of 10 because it ignored the issue asking for one example and did not follow the README install style next to it
Change: I added a rule to the opensource profile: what the issue asks for and what the maintainer already does come before my own preference
Result: ordewell 140 merged the same day, and the rule has governed every plan since

**Beat 6**
Date: November 2, 2026
Friction: My opensource scans kept returning to repositories I had already worked in, which made each new scan narrower than the last
Change: I changed the order rule from returning repositories first to new repositories first
Result: The next day Meta astryx 9719 opened and merged in 3 hours and 16 minutes, in a repository I had never touched before

**Beat 7**
Date: November 3, 2026
Friction: nanocoder 1929 was claimed by someone else about an hour after my scan found it, while it waited for my confirmation
Change: I changed the rule so a repository that needs a claim before work starts gets the claim text immediately, without waiting for me
Result: none

**Beat 8**
Date: November 7, 2026
Friction: Sentient 548 sat in review for five days with no maintainer response
Change: I left it alone under the no nudge rule instead of writing to the maintainer
Result: The maintainer ran their own real engine test, approved it with a note saying my real test notes matched what they saw, and merged it that day

## Limitations and What's Next

The toolkit still cannot finish a contribution without me.
It can scan, grade, reproduce, write, and check, and it cannot pick what is worth my time, approve words that carry my name, or decide a tradeoff like keeping dex 952 open after another pull request beat it by four minutes.
Most of its rules exist because a real case forced them, which also means the cases that have not happened yet have no rule.
Nothing in it tests how a change feels to use, only whether it works.

Next I keep improving the skills.
The voice guard reads command text and does not expand shell variables, so a path held in a variable still gets stopped.
The next change is to resolve those paths before the check runs.
The ship gate's npx pin ran Node 26 after Homebrew changed my default.
The next change is a pinned Node 22 toolchain that prints node -v on every run.
The rerun on November 3 already did this and printed v22.22.3.
The opensource skill has no screen reader or window resizing coverage on UI changes, and ordewell 142 needed the maintainer to add those fixes.
The next change is a UI check in the profile before a pull request opens.

I keep evaluating.
issue-scout has not run an eval since the scope-feasible change on October 21, so the current rubric has no score.
The next step is to rerun the Unit 1 harness against it.
pr-monitor has run in full only once, and that draft could not be sent.
The next step is one more full run on a pull request that is still open, with the two drafts compared.
plan-check still carries the wording conflict I found on October 28 between its rubric and its procedure on reporting finished results.
The next step is to settle that wording and rerun its eval.

I keep contributing.
Eight external pull requests are still open, including storybook 37092, renovate 47597, grafana 136956, and super-productivity 11434.
Altinn 21606 is still in review as of November 7, with six workflows waiting for approval.
Two issues are waiting on their owners, hass-eink-dashboard 103 and ucsd-easy-a-radar 86.
The repositories that already merged my work, such as dex, ordewell, and Sentient, still show up in my scans, and I keep taking work there.

Unit 10 is Demo Day, five minutes, presented from this page, and I would rather spend that time on the astryx and Sentient cases than on the tools themselves.

**Tool limits.** One line per featured tool, in the same order as the entries above.

issue-scout: It cannot tell whether an issue is about to be claimed by someone else, and its rubric has not been scored since the scope-feasible change on October 21, so its current accuracy is unmeasured
voice guide and voice guard: It reads the command text and does not expand shell variables, so paths held in variables and a body file read from stdin get stopped, and it crashed twice while another session was editing check_voice.py itself
opensource skill: UI changes carry no screen reader or window resizing coverage, and ordewell 142 needed the maintainer to add those fixes, and on this Mac some repositories fail tests on a clean base, astryx had 48, so a base comparison is the only way to judge my own failures
pr-precheck and ship gate: The manifest runs Node through an npx package pin, and after Homebrew put Node 26 on this machine that command ran 26 instead of 22, and the October 28 follow-up checks did not print a version, so the gate record does not prove which Node ran
