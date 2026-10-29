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
**Pull Request:** https://github.com/Altinn/altinn-studio/pull/21606

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

**Unit 7: Ship-gate manifest from the frontend CI, a real gate PASS, and a voice-guard stop on the PR**

2026-10-28: With Claude Code, I wrote ship-manifest.md for Altinn/altinn-studio with four checks from the Designer frontend CI workflow and CONTRIBUTING.md (Vitest, typecheck, ESLint with Prettier, and yarn spell:quick), and both hooks stopped the `gh pr create --help` wiring test.
On main, typecheck failed only on my untracked reproduction test and three schema suites failed until my sparse checkout got its testdata folder, so I fixed the setup and kept the exclusion table empty.
On my branch the gate passed all four checks and all six pr-precheck checks, and I added the one line it asked for, that hosted CI had not run.
When the PR opened, the voice guard stopped the body's emoji attribution line, so it was removed and the hook ran the gate again, which passed.

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
GitHub stored the comment byte-identical to the checked draft.
As of October 28, no maintainer has replied or assigned the issue.
I posted my one-week report of findings that day through Claude Code with the voice guard active: https://github.com/Altinn/altinn-studio/issues/10955#issuecomment-6485588852.
It reports the remount result on main c298f416, says I had not checked a real browser reload or the older editors, and says I would open a PR for ux-editor (v9+) only unless the maintainers prefer another package.

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
On October 28 the selection files were unchanged on main c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6, and the same test still failed the same way.
The editor also keeps a second copy of the selection in FormItemContext, which the tree highlight and the properties panel read, and that copy is not restored either.
This is a provider/remount result, not a full browser refresh or a verification of every editor version.

**Affected Components**

- src/Designer/frontend/packages/ux-editor/src/AppContext.tsx: URL-derived page initialization and local selectedItem state.
- src/Designer/frontend/packages/ux-editor/src/containers/DesignView/FormTree/FormTree.tsx: sets both selection copies and highlights formItemId.
- src/Designer/frontend/packages/ux-editor/src/containers/FormItemContext.tsx: holds the edited component (formItemId and formItem) and discards it on mount and on every page change.
- src/Designer/frontend/packages/ux-editor/src/components/Properties/ComponentConfigPanel/ComponentConfigPanel.tsx: clears selectedItem during render when formItem is missing.
- src/Designer/frontend/packages/ux-editor/src/AppContext.test.tsx: existing baseline tests for provider selection behavior.
- src/Designer/frontend/packages/ux-editor/src/AppContext.selectionPersistence.repro.test.tsx: the new local, uncommitted remount reproduction; its complete source is included below.
- ux-editor-v4 has similar state; UiEditor.tsx chooses between the three editor packages by frontend version, so the target package needs scope confirmation.

**Toolkit**

- Tool: scoped source orientation with Codex, the issue thread, applicable AGENTS.md files and CONTRIBUTING.md.
- What it produced: the three active-editor entry points above and a short CLAUDE.local.md importing the repository's own root guidance.
- Difficulties: a React state setter alone does not prove the actual browser-refresh outcome, and the issue predates the current editor-version split.
- What changed: separated the source hypothesis from runtime evidence and made the version choice an explicit question in the claim draft.
  On October 28, Claude Code rechecked this against main c298f416 and the rewritten CONTRIBUTING.md and PR template, and added FormItemContext and ComponentConfigPanel once tracing showed that the tree and properties panel read a second copy of the selection.

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

Observed: `AppContextProvider` loses a component selection across a fresh mount at the same URL.

Traced cause in `ux-editor` (source reading; the provider part is confirmed by the reproduction):

- `AppContext.tsx` keeps `selectedItem` in `useState`, initialized from the `layout` query parameter as a page, and `setSelectedItem` only updates that state, so a component ID never reaches the URL.
- The UI has a second copy of the selection.
  `FormItemContext.tsx` keeps `formItemId` and `formItem` in `useState`, and its page-change effect calls `handleDiscard()` on mount and whenever the selected page changes.
- `FormTree.handleSelect` sets both copies: `handleEdit(getItem(layout, id))` and `setSelectedItem({ type: Component, id })`.
- The tree highlights `selectedId={formItemId}` from `FormItemContext`.
- `Properties.tsx` chooses the panel from `AppContext.selectedItem`, but `ComponentConfigPanel.tsx` reads `formItem` from `FormItemContext` and calls `setSelectedItem(undefined)` during render when `formItem` is missing.

Inference that the planned tests will check: restoring only `AppContext.selectedItem` would turn the reproduction green, but in the real editor `ComponentConfigPanel` would clear it on its first render because `formItem` is still empty, and the tree would stay unhighlighted.
Both copies have to be restored, and `formItem` has to be available in the same render in which the properties panel first shows the component.

Two constraints from the current code shape the fix:

- React Router 7.18.2's `setSearchParams` builds a functional update from the params of the last render (`nextInit(new URLSearchParams(searchParams))`).
  Five handlers set both the page and a non-component selection in one event: `DesignView.handleClickAccordion`, `DesignView.handleAddPage`, `PageGroupAccordion.handleSelectGroup`, `EditPageId.handleSaveNewName` and `useAddPageToGroup`.
  If both calls wrote the URL, the second write would undo the first.
- `FormItemContext`'s page-change effect saves the current `formItem` before discarding it, using a mutation bound to the previous page name.
  A restored item must therefore never be in place before that effect runs for the page it was restored on, or the restore would send an unintended save.

**Proposed Solution**

Candidate, limited to `ux-editor` (v9+ apps) until a maintainer confirms the scope.

1. `AppContext.tsx` stores the selected component ID in a `component` query parameter next to `layout` (name to be confirmed).
   - `selectedItem` starts as that component when the parameter is present, otherwise as today.
   - `setSelectedItem` writes the parameter when it receives a component, with `replace`, so component clicks do not add Back steps.
   - Non-component selections do not write the URL.
   - The `setSelectedFormLayoutName` that `AppContext` exposes changes `layout` and removes `component` in one functional `setSearchParams` update that keeps the other parameters and sorts them as `useSearchParamsState` does.
     The five handlers above then make one URL write each, and a component from an earlier page cannot be restored on top of a later page selection, for example after P1 -> P2 -> P1.
2. `FormItemContext.tsx` restores the edited item once, for the component read from the URL when the editor mounts.
   - When nothing is being edited and `selectedItem` is a component found in the selected layout (`useFormLayout(selectedFormLayoutName)` and `getItem`), it provides that item as `formItemId` and `formItem` in the same render.
   - It commits the item with the existing `handleEdit` in an effect declared after the page-change effect.
   - The tree highlight and the properties panel then follow the existing code paths.
   - A missing, deleted or invalid component ID is not restored, so today's `ComponentConfigPanel` fallback clears the selection and shows the page panel.

Not changing:

- `ux-editor-v4`, `ux-editor-v3` and the shared hooks `useSearchParamsState` and `useSelectedFormLayoutName`; v4 also imports the latter.
- Group selection, page persistence beyond the existing `layout` parameter, preview links, saved layouts and component IDs.
- Live re-selection on Back and Forward: `selectedItem` is read from the URL only on mount, as today.
- Dependencies, `ComponentConfigPanel`'s fallback, and the reproduction test's assertions.

Alternatives not chosen:

- Restoring only in `AppContext`: it passes the provider test but is undone by `ComponentConfigPanel` in the real UI.
- Writing the URL from every `setSelectedItem` call or from an effect: the render-time params in React Router lose the page change in the five handlers above.
- Changing the shared hooks: this reaches `ux-editor-v4` without agreement.
- Fixing all three editors: the scope question in my claim is still unanswered.
- `localStorage`: the issue asks for the URL, which also makes the selection shareable.

**Implementation Plan**

1. Before coding, re-check the thread, linked PRs and main.
   If a maintainer has answered the scope question, follow that answer; if not, build only this `ux-editor` candidate and say in the PR description that the scope question is still open.
   Then create a fork and a branch from current main, as CONTRIBUTING.md asks of contributors outside the team.
2. `src/Designer/frontend/packages/ux-editor/src/AppContext.tsx`: add the `component` parameter, the initial component selection, the URL write in `setSelectedItem` for components, and the single-update `setSelectedFormLayoutName`.
3. `src/Designer/frontend/packages/ux-editor/src/containers/FormItemContext.tsx`: add the one-time restore of the URL component from the selected layout, ordered after the page-change effect.
4. `src/Designer/frontend/packages/ux-editor/src/AppContext.test.tsx` and `containers/FormItemContext.test.tsx`: move the remount reproduction in as a regression test and add the neighbor cases from Validation.
   Rerun the untracked reproduction file unchanged as evidence and save that output for `test_evidence.md`.
   That file fails typecheck (unused `React` import), so after that run, move it from the checkout to the Trash, as the user approved on 2026-10-28; copies stay in unit7-drafts and unit6-drafts, and the regression test in `AppContext.test.tsx` keeps covering the case.
5. Run the manifest checks and `yarn spell:quick`, then check a real browser reload in a local Studio, if that run is authorized and a v9 test app is available.
   Save the before and after output in `test_evidence.md`.
6. Write `pr_draft.md` with the repository's Summary, Evidence, Risk and Follow-ups sections, `Closes #10955` and an AI-assistance note.
   Use a Conventional Commits title such as `fix(designer): keep the selected component after reloading the form editor`.
   Record any deviation from this plan here and in the PR description.

Deviations, the same as in plan.md:

Recorded 2026-10-28 PDT while building commit c1e6c182606974e8f1d29b6e97cbfe8d45bfdc37.

- FormItemContext reads the component ID to restore from the `component` query parameter, not from `selectedItem`, and the restore sets both copies (`handleEdit` and `setSelectedItem`).
  Why: a test that loads the pages after the layouts showed `ComponentConfigPanel` clearing `selectedItem` during render before the page name could be checked, so a restore keyed on `selectedItem` never ran.
  In that order React logs its "Cannot update a component while rendering a different component" warning once, from the existing render-time clear; the test asserts it.
- `FormItemContext`'s page-change effect only awaits `handleSave()` when an item is being edited.
  Why: with nothing to save, the await still moved `handleDiscard()` past the restore effect, which then cleared the restored item; `handleSave()` without an item does nothing.
- The URL tests went into a new `describe` in `AppContext.test.tsx` that swaps the file-wide `useSearchParams` mock for the real hook; `testing/mocks.tsx` gained an optional `search` for `AppRouter` and `renderWithProviders`.
- The reproduction command now reports `Tests 15 passed (15)`, not 10, because `AppContext.test.tsx` has five new tests; the reproduction file itself was unchanged (same SHA-256) for that run.
- The manual browser reload was not run: a local Studio needs a signed-in session, and the browser rules for this work exclude authentication, so the PR evidence is the before/after test output instead of a screenshot.

**Toolkit**

- Tool: my installed plan-check, run on October 28 by Claude Code in the same session that drafted plan.md and plan-comment.md, against the live #10955 thread.
- What it produced: run 1 rejected the package (six checks passed; thread-and-conventions failed because the comment ignored the thread's "Blocked by #15947" note), and runs 2 to 4 accepted with all seven required checks passing.
- Difficulties: the skill still expects a posted Unit 2 reproduction report and a plan comment that will be posted, while Units 6 and 7 keep both local, and its rubric still mentions Path Review house rules; the session that wrote the drafts also graded them, so the accept is not independent.
- What changed: the drafts now say #15947 merged, name the adjacent draft PR #21442, the typecheck blocker and how it gets resolved, and split long sentences; I left the rubric and procedure unchanged and recorded the classroom wording as gaps.

---

## Testing Strategy

The fix is commit c1e6c182606974e8f1d29b6e97cbfe8d45bfdc37 on branch fix/10955-keep-selected-component, based on main c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6.
Every command ran on October 28 in a fresh login shell with Node 22.23.4, Yarn 4.18.0 and Vitest 5.0.1; the full output is in my local test_evidence.md.

1. Original failure, with the reproduction command from Reproduction Process and the test file unchanged (same SHA-256):
   - Before, on main: exit 1, `Tests 1 failed | 9 passed (10)`, `expected { type: 'page', id: 'Side1' } to deeply equal { type: 'component', id: 'Input' }`.
   - After, on c1e6c182: exit 0, `Tests 15 passed (15)`; the count grew because AppContext.test.tsx gained five tests.
2. Real editor state: a new FormItemContext test mounts the real AppContextProvider, FormItemContextProvider and properties panel at `?component=Input&layout=Side1`.
   The Input settings heading appears, selectedItem stays Input and no layout save is sent, also when the pages load after the layouts.
3. Neighbor behavior covered by the new tests: selecting a component writes `component` and keeps an unrelated parameter; selecting another page or closing the page in the same event removes `component` and keeps the page change; P1 -> P2 -> P1 restores page P1; an ID missing from the selected layout is not restored; a discarded (for example deleted) component is not restored again.
   Renaming, adding a page and selecting a group use the same AppContext setter as the page change, but I did not add a separate test for each.
4. Without the source change, 8 of the 10 new tests fail; the other two are controls that already passed.
5. Repository checks from ship-manifest.md, all exit 0 on c1e6c182: the Designer frontend suite (10853 passed, 5 skipped), typecheck, ESLint (0 errors, 3 existing warnings) with Prettier, and `yarn spell:quick`.
   On main the same suite had 1 failure, my reproduction, and typecheck failed only on that untracked file's unused `React` import.
6. Not run: a real browser reload, which needs a signed-in local Studio, and anything in ux-editor-v4 or ux-editor-v3; hosted CI is reported separately in Pull Request.

**Toolkit**

- Tool: Claude Code ran the reproduction, the new tests with and without the source change, and the four ship-manifest commands in fresh login shells, on main and on the branch, and saved the raw output.
- What it produced: the reproduction going from red on c298f416 to green on c1e6c182, eight new tests that fail without the fix, all four manifest checks passing on the branch, and on main a typecheck failure caused only by my untracked test.
- Difficulties: three schema-model suites failed with ENOENT because my sparse checkout lacked src/Designer/testdata, yarn spell:quick needed scripts/ plus typos and hunspell, and a test that loads the pages after the layouts showed my first restore losing the selection.
- What changed: added src/Designer/testdata and scripts/ to the sparse checkout and installed typos 1.51.1 (the CI version) and hunspell, kept the manifest's exclusion table empty, changed the restore to read the URL, and left the reproduction file unchanged; with my approval it was removed from the checkout after its after-fix run instead of having its import edited.

---

## Implementation Notes

**2026-10-28**

Nothing is implemented yet; today was research and planning, with Claude Code doing the checkout updates, runs and tracing.
It backed up my untracked reproduction test, fast-forwarded my local upstream main checkout from 0a62afac to c298f416, reinstalled with the immutable lockfile and reran the reproduction, which failed the same way.
Tracing the whole selection flow showed a second copy of the selection in FormItemContext, which ComponentConfigPanel clears when it is empty, so restoring only AppContext would pass my test without fixing the editor.
It also showed that React Router's setSearchParams builds on the params of the last render, so writing the URL from both the page setter and the selection setter in one click would lose one update; the plan therefore writes the URL once per action.
A search found draft PR #21442, which changes when deleting a component clears the selection; it is for #12679 and touches FormItemTitle.tsx, not the files in my plan.
Claude Code ran my installed plan-check on plan.md and plan-comment.md four times: run 1 rejected the comment for not addressing the thread's "Blocked by #15947" note, and runs 2 to 4 accepted after the drafts added that #15947 merged in 2025, a known typecheck blocker, and my decision to remove the local reproduction file after its after-fix run.
The ship-manifest.md draft takes its four checks from the frontend CI workflow; running them on main found the typecheck problem in my untracked test and a missing testdata folder in my sparse checkout.
Later that evening, with my approval for each step, Claude Code posted the report-back, installed the ship-gate and ran its wiring test, installed typos and hunspell, created my fork hskl18/altinn-studio and built the fix on branch fix/10955-keep-selected-component.
The first version restored the component in FormItemContext from selectedItem, but a new test that loads the pages after the layouts showed ComponentConfigPanel clearing selectedItem first, so the restore now reads the ID from the URL and sets both copies.
The same test exposed that FormItemContext's page-change effect awaited a save even with nothing to save, which delayed its discard past the restore; it now only awaits when an item is open.
After commit c1e6c182 the unchanged reproduction passed (15 passed), I had it moved to the Trash because its unused import fails typecheck, and the new tests fail on main (8 of 10) and pass on the branch.
I did not check a real browser reload, because that needs a signed-in local Studio.
The ship-gate passed on the branch, and after the voice guard stopped the emoji attribution line in the description, PR #21606 opened at 19:18 PDT with the hook's second gate pass; hosted CI was waiting for maintainer approval.

**Toolkit**

- Tool: Claude Code, which edited AppContext.tsx and FormItemContext.tsx, wrote the tests with Vitest and Testing Library, and committed on my fork's branch after each step I approved.
- What it produced: commit c1e6c182, which changes two source files, their two test files and the test router helper, with ten new tests.
- Difficulties: the first restore design passed every test except the one where the pages load after the layouts, which exposed both ComponentConfigPanel's render-time clear and an awaited no-op save; ESLint also rejected an `import()` type in the test.
- What changed: the restore reads the component ID from the URL and sets both selection copies, the page-change effect skips the empty save, the test uses `vi.importActual` without the type annotation, and plan.md and Solution Approach record all of it as deviations.

---

## Pull Request

**PR Link:** https://github.com/Altinn/altinn-studio/pull/21606

**PR Description:** opened 2026-10-28 from hskl18:fix/10955-keep-selected-component at c1e6c182 into main, titled "fix(designer): keep the selected component after reloading the form editor", with the repository's Summary, Evidence, Risk and Follow-ups sections and Closes #10955.
Summary: selecting a component in ux-editor (v9+ apps) puts its ID in a component query parameter, AppContext seeds the selection from it and drops it in the same URL update as a page change, and FormItemContext restores the edited item once, so the tree and properties panel follow; ux-editor-v4 and ux-editor-v3 are unchanged, and the scope question stays open.
Evidence: the remount reproduction went from `1 failed | 9 passed` on main to `15 passed` on the branch, 8 of the 10 new tests fail without the change, and the full frontend suite, typecheck, lint, Prettier and spell:quick pass locally; hosted CI had not run, and there is no browser screenshot because I had no signed-in local Studio.
Risk and Follow-ups list the stale parameter for a missing ID, Back/Forward not reselecting, ComponentConfigPanel's one-time render warning when the pages load late, the narrower autosave await, and the untouched older editors.
Notes for reviewers says Claude Code traced the flow, wrote the change and tests, ran the checks and drafted the description, and that I approved the scope and each step.

**Maintainer Feedback:**

- 2026-10-28: none yet; my report-back on the issue and the PR have no maintainer reply.
  At opening, the main CI workflows were waiting for maintainer approval (`action_required`), so hosted CI has not run.

**Status:** Awaiting review

**Toolkit**

- Tool: the ship-gate, run by hand on my branch and again through its hook when Claude Code ran `gh pr create` in a fresh session, together with my voice guard.
- What it produced: `ship-gate: PASS` with all four manifest checks and all six pr-precheck checks passing, a voice-guard stop on the first PR attempt, and PR #21606 after the second attempt.
- Difficulties: the gate found no PR template because my sparse checkout leaves out .github, pr-precheck wanted the local checks and the hosted CI state in the description, and the voice guard rejected the emoji in the attribution line.
- What changed: I added the local-checks and hosted-CI line to the description, removed the emoji attribution line and kept the AI disclosure in Notes for reviewers, and the hook ran the whole gate again before the PR opened.

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
