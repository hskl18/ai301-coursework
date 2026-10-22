# Contribution: Preserve selected form component after refresh

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Hanbin Tan
**GitHub Username:** hskl18
**Issue:** https://github.com/Altinn/altinn-studio/issues/10955
**Pull Request:** Pending - no implementation or PR has been started.

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Building the scout, running its first scan, and patching the rubric**

2026-10-14: I upgraded my Unit 1 issue selector to issue-scout and ran a full scan: four GitHub searches returned 400 results, ranking narrowed them to 139 repositories, and I graded the top five against my ten-check rubric.
The scan accepted an automated fixture and treated a terse report as unbounded, so I clarified repository-purpose, human-triage and task-boundary rules.
I then graded three issues shown on the course Issue Selection site, kept two Altinn interface issues as candidates and rejected a browser-title change because an open pull request already covers it.
After two 19/20 full regressions, I clarified that several proposed fixes or variants of one behavior do not make an umbrella, checked genuine umbrella cases, and confirmed 20/20 with the unchanged Unit 1 harness.

**Unit 6: One canonical voice guide, a posting guard, and scoped repository memory**

2026-10-21: With Codex assistance, I installed the staff voice guard, merged my Unit 2-4 rules into one canonical guide with claim/question/ping rules, and connected the three live skills to it.
In a fresh Claude Code session, the hook blocked a real `gh issue comment --help` tool call before it ran, and the guard's Sonnet voice pass returned pass on both the first and the revised version of my claim draft.
I replaced the scout's strict scope check with scope-feasible and separated difficulty from acceptance; I also clarified repro-check's old no-date wording so a report-back window is allowed without promising a fix deadline.
Codex prepared locally excluded CLAUDE.local.md notes and ran the 9/9 AppContext baseline; during posting, a relative --body-file path failed the guard, so Claude used an absolute path and the checked claim posted once.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I selected [Altinn/altinn-studio#10955](https://github.com/Altinn/altinn-studio/issues/10955), which asks the form editor to preserve the selected component after a page refresh by storing its identity in the URL.
It came from the Issue Selection site's candidates I recorded in Unit 5, rather than being one of the first public scan's top five.
My Unit 5 scout accepted it; its only thread comment names prerequisite PR #15947, and a fresh check confirmed that PR merged on October 27, 2025.
On October 21, the issue remained open and unassigned, the complete thread contained no claim, and no open PR explicitly referenced #10955 among the 142 open PRs inspected.
I switched from my course-site reservation of #12123 because that issue still has a 2024 claim and maintainer permission; my scout's twelve-month expiry rule accepted it, but Unit 6's stricter claim rule says to choose another issue.
On October 21, I released the #12123 reservation and claimed #10955 on the course Issue Selection site.
My screenshot shows the release banner, the matching #10955 title under Your issues (1), and an Unclaim button; this confirms the course-site reservation, not a GitHub claim comment or maintainer assignment.

This fits my React/TypeScript experience and gives me practice distinguishing in-memory UI state from URL state, preserving neighboring routing behavior and writing evidence a maintainer can review.
At the checked-out commit, Studio routes frontend major versions 9+ to ux-editor, 4 through 8 to ux-editor-v4 and earlier versions to ux-editor-v3; the first two keep component selection in local React state, so the editor-version scope needs a maintainer answer before implementation.
On October 21, my Unit 6 scout re-grade, run directly in Claude Code with the scope-feasible rubric, accepted both #10955 and #12123.
Its difficulty note rates #10955 ambitious: the issue is marked for consideration, ready-for-dev was removed on September 25, 2026, and the editor-version scope is open, so my claim has to raise that question first.
It rated #12123 straightforward and ranked it higher on fit, but that accept still rests on the stale-claim allowance described above.
My scout helped find a coherent candidate, but its old availability rule and the course-site reservation were not sufficient evidence that #12123 was available under this week's rules.
I applied the course scope-feasible patch and recorded the replaced check in scan-notes.md; the final Unit 5 20/20 run belongs to the earlier rubric, not this patched version.
This story draft, source investigation and local baseline were prepared with Codex assistance; I reviewed the final claim wording myself before it was posted.

Claim comment: https://github.com/Altinn/altinn-studio/issues/10955#issuecomment-6330240501 (posted 2026-10-21 18:12 PDT).
The prepared draft asks about the editor-version scope, names the first reproduction check, gives a one-week report-back window and discloses Codex assistance.
On October 21, a claim-only repro-check accepted the first draft: claim-specific and repo-conventions passed, and the five checks that need a reproduction report were excluded.
The voice guard's manual Sonnet check of that first draft returned pass with exit 0.
Codex then revised the editor names and report-back wording and asked which editor package, if any, the maintainer would welcome work on.
Later on October 21, a claim-only repro-check of the revised draft also accepted it with the same two checks passing, and the voice guard's Sonnet check of the revised draft returned pass with exit 0.
Just before posting, the thread was still open and unassigned, with no new comments, events or referencing pull requests.
I posted the revised draft once through Claude Code with the voice guard active; the guard first stopped the command because it resolved a relative --body-file path against the session directory, and the same draft passed and posted once with an absolute path.
GitHub stored the comment byte-identical to the checked draft; no maintainer has replied or assigned the issue yet, and I owe a report of findings, a cannot-reproduce result or a setup blocker within a week.

**Toolkit**

- Tool: issue-scout, re-run directly in Claude Code on October 21 with the Unit 6 scope-feasible rubric after the Unit 5 direct read-out.
- What it produced: Unit 5 accepted #10955 and #12123 and rejected #14892 for existing work; the Unit 6 re-grade accepted #10955 (ambitious) and #12123 (straightforward), and current thread/PR checks support preparing #10955 instead of claiming over #12123's old contributor.
- Difficulties: a course-site reservation is not a GitHub claim, the scout's stale-claim allowance is looser than Unit 6's rule, and the editor-version scope across ux-editor, ux-editor-v4 and ux-editor-v3 is not settled by a newcomer label.
- What changed: replaced one-bounded-task with scope-feasible, added live-only difficulty notes, switched the selected issue to #10955 with my explicit confirmation, and left the maintainer question visible instead of silently guessing scope.

---

## Understanding the Issue

**Problem Description**

The report asks the forms editor to keep the same component selected after refreshing the page.
This is a selection-persistence behavior, not a request to change component IDs, saved layout content or data submission.

**Expected Behavior**

Selecting a component should place enough identity in the URL for the same component to be selected when that URL reloads.
Existing page/layout selection should continue to work.

**Current Behavior**

The GitHub report says selection is lost on refresh.
Current source at 0a62afac023248918e345457044a72c6deda8052 reads a layout query parameter and initializes a Page selection; later component selections are kept in local React state.
An authorized local test now confirms that the ux-editor provider changes selectedItem from component Input to page Side1 after a fresh mount at the captured URL.
This is a provider/remount result, not a full browser refresh or a verification of every editor version.

**Affected Components**

- src/Designer/frontend/packages/ux-editor/src/AppContext.tsx: URL-derived page initialization and local selectedItem state.
- src/Designer/frontend/packages/ux-editor/src/containers/DesignView/FormTree/FormTree.tsx: sets the selected component.
- src/Designer/frontend/packages/ux-editor/src/AppContext.test.tsx: existing baseline tests for provider selection behavior.
- src/Designer/frontend/packages/ux-editor/src/AppContext.selectionPersistence.repro.test.tsx: the new local, uncommitted remount reproduction; its complete source is included below.
- ux-editor-v4 has similar state; UiEditor.tsx chooses between the three editor packages by frontend version, so the target package needs scope confirmation.

**Toolkit**

- Tool: scoped source orientation with Codex, the issue thread, applicable AGENTS.md files and CONTRIBUTING.md.
- What it produced: the three active-editor entry points above and a short CLAUDE.local.md importing the repository's own root guidance.
- Difficulties: a React state setter alone does not prove the actual browser-refresh outcome, and the issue predates the current editor-version split.
- What changed: separated the source hypothesis from runtime evidence and made the version choice an explicit question in the claim draft.

---

## Reproduction Process

**Environment Setup**

macOS 27.2 arm64; Node 22.23.3 selected through npx; committed Yarn 4.18.0; React 19.2.8; React Router 7.18.2; Vitest 5.0.1; Testing Library React 16.3.2; jsdom 30.1.1.
My source checkout is public Altinn/altinn-studio main at 0a62afac023248918e345457044a72c6deda8052; a read-only API check confirmed that this was also remote main during the run.
It is not a fork or implementation branch, and no reproduction commit exists.
The initial sparse checkout omitted two workspaces; adding src/App/frontend and src/Designer/development/azure-devops-mock allowed the Node 22 immutable install to exit 0 without changing the lockfile.
The existing AppContext baseline passed 9/9 before the new local test was added.
No account, real application data, backend server, database or Docker stack was needed.
Codex wrote and ran the one authorized reproduction test with the real router/provider and the repository's synthetic fixtures and mocked backend services.

**Steps to Reproduce**

1. Check out the public source commit above and install dependencies from the repository root:

   ```sh
   npx --yes --package=node@22 -- node .yarn/releases/yarn-4.18.0.cjs install --immutable
   ```

2. Save the complete test in the evidence block below at src/Designer/frontend/packages/ux-editor/src/AppContext.selectionPersistence.repro.test.tsx.
3. The test mounts the real ux-editor AppContextProvider and MemoryRouter with a valid layout=Side1 query and existing synthetic component Input.
   It verifies layout/Page initialization, calls setSelectedItem with the same component selection used by FormTree, and verifies the runtime selection before capturing the actual router URL.
4. It unmounts the tree, creates a new router/query client/provider at the captured URL, and verifies that layout Side1 and the same URL restore correctly.
   It then expects component Input to remain selected.
5. Run the exact command used in the final reproduction:

   ```sh
   npx --yes --package=node@22 -- node .yarn/releases/yarn-4.18.0.cjs workspace studio-designer-frontend test packages/ux-editor/src/AppContext.test.tsx packages/ux-editor/src/AppContext.selectionPersistence.repro.test.tsx
   ```

**Reproduction Evidence**

- **Commit showing reproduction:** none - the test is a local untracked addition, and no fork or source commit exists.
- **Expected:** after the fresh mount, selectedItem remains { type: 'component', id: 'Input' }.
- **Actual:** it becomes { type: 'page', id: 'Side1' }; the earlier runtime-selection and layout/same-URL checks pass.
- **Observed command result:** exit 1, with one new failing assertion and all nine existing tests passing.

  ```text
   Test Files  1 failed | 1 passed (2)
        Tests  1 failed | 9 passed (10)

  AssertionError: expected { type: 'page', id: 'Side1' } to deeply equal { type: 'component', id: 'Input' }
  ```

The exit 1 is the deliberately retained reproduction of the unfixed behavior, not a claim that tests pass.
The final file passed focused ESLint and Prettier checks, both exit 0.
The first run exposed a render-result variable naming lint rule; destructuring those results resolved it, and the final rerun still reproduced the same state loss.
The original Vite config-loader warnings were preserved in raw stderr; they are separate from the failing state-retention assertion.

<details>
<summary>Complete local reproduction test, so this is rerunnable without a reproduction commit</summary>

Path: src/Designer/frontend/packages/ux-editor/src/AppContext.selectionPersistence.repro.test.tsx.
SHA-256: 61c12a293e7ac2a4013b181b464753911ebdb4a44fd87789d6015cf1a3e77296.

```tsx
import React from 'react';
import type { ReactNode } from 'react';
import { act, renderHook, waitFor } from '@testing-library/react';
import { describe, expect, it, vi } from 'vitest';
import { MemoryRouter, Route, Routes, useLocation } from 'react-router-dom';
import { ServicesContextProvider } from 'app-shared/contexts/ServicesContext';
import { PreviewContext } from 'app-shared/contexts/PreviewContext';
import { createQueryClientMock } from 'app-shared/mocks/queryClientMock';
import { queriesMock } from 'app-shared/mocks/queriesMock';
import { QueryKey } from 'app-shared/types/QueryKey';
import { app, layoutSet, org } from '@studio/testing/testids';
import { AppContextProvider } from './AppContext';
import { useAppContext } from './hooks';
import { ItemType } from './components/Properties/ItemType';
import { component1IdMock, layout1NameMock } from './testing/layoutMock';

describe('AppContext selection persistence (#10955 reproduction)', () => {
  it('restores the selected component after remounting at the captured URL', async () => {
    const initialUrl = `/${org}/${app}/${layoutSet}?layout=${layout1NameMock}`;
    const { result, unmount } = renderAppContextForReproduction(initialUrl);
    const selectedComponent = { type: ItemType.Component, id: component1IdMock } as const;

    await waitFor(() =>
      expect(result.current.appContext.selectedFormLayoutName).toBe(layout1NameMock),
    );
    expect(result.current.appContext.selectedItem).toEqual({
      type: ItemType.Page,
      id: layout1NameMock,
    });

    act(() => result.current.appContext.setSelectedItem(selectedComponent));
    expect(result.current.appContext.selectedItem).toEqual(selectedComponent);
    const capturedUrl = result.current.url;
    unmount();

    const { result: remountedResult } = renderAppContextForReproduction(capturedUrl);
    await waitFor(() =>
      expect(remountedResult.current.appContext.selectedFormLayoutName).toBe(layout1NameMock),
    );
    expect(remountedResult.current.url).toBe(capturedUrl);
    expect(remountedResult.current.appContext.selectedItem).toEqual(selectedComponent);
  });
});

function renderAppContextForReproduction(url: string) {
  const queryClient = createQueryClientMock();
  queryClient.setQueryData([QueryKey.LayoutSets, org, app], [{ id: layoutSet }]);
  queryClient.setQueryData([QueryKey.FormLayoutSettings, org, app, layoutSet], {
    pages: { order: [layout1NameMock] },
  });
  queryClient.setQueryData([QueryKey.Pages, org, app, layoutSet], {
    pages: [{ id: layout1NameMock }],
  });

  const wrapper = ({ children }: { children: ReactNode }) => (
    <MemoryRouter initialEntries={[url]}>
      <Routes>
        <Route
          path='/:org/:app/:layoutSet'
          element={
            <ServicesContextProvider {...queriesMock} client={queryClient}>
              <PreviewContext.Provider
                value={{
                  shouldReloadPreview: false,
                  doReloadPreview: vi.fn(),
                  previewHasLoaded: vi.fn(),
                }}
              >
                <AppContextProvider
                  shouldReloadPreview={false}
                  previewHasLoaded={vi.fn()}
                  onLayoutSetNameChange={vi.fn()}
                >
                  {children}
                </AppContextProvider>
              </PreviewContext.Provider>
            </ServicesContextProvider>
          }
        />
      </Routes>
    </MemoryRouter>
  );

  return renderHook(
    () => {
      const appContext = useAppContext();
      const { pathname, search, hash } = useLocation();
      return { appContext, url: `${pathname}${search}${hash}` };
    },
    { wrapper },
  );
}
```

</details>

- **My findings:** the real ux-editor provider loses the selected component across a fresh mount at the captured URL, while layout restoration and runtime selection work.
  This package serves frontend major versions 9+; the test does not mount the full FormTree, handleEdit flow or property panel, run a browser refresh, or test ux-editor-v4/ux-editor-v3.
  The existing source paths suggest a persistence gap, but a complete browser outcome and editor scope still need confirmation.
  No business implementation was changed.
  On October 21, a full claim-plus-report repro-check in Claude Code accepted the published claim and this report, with all seven required checks passing; that accept covers only this provider-remount scope, not a browser refresh or the other editor versions.

**Toolkit**

- Tool: Codex with the real React provider/router, existing synthetic fixtures, Vitest, focused ESLint and Prettier; then Claude Code ran repro-check on the published claim and the full report together.
- What it produced: an auditable local remount failure (component Input becomes page Side1), nine passing controls and the full test source/output with no new dependency, and a full-package repro-check accept.
- Difficulties: the original green suite did not exercise remounting, the first test draft hit a lint naming rule, the provider-level result is narrower than a browser refresh, and the review found one copied stdout line missing its leading space.
- What changed: added one local reproduction test, corrected only its render-result naming, retained the failure and documented the exact scope and command; Claude Code restored the copied output line exactly and removed a stale pending note, and the business fix remains pending.

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
