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

2026-10-14: I used issue-scout to search GitHub, narrow 400 results to 139 repositories and grade the top five with my ten-check rubric.
It accepted an automated fixture and rejected a short report as too broad, so I tightened the repository and task-boundary rules.
I also checked three course-site issues, kept two Altinn candidates and dropped a browser-title change that already had a PR.
After two 19/20 runs, I clarified that several possible fixes for one behavior do not make an umbrella issue; the next full run reached 20/20 with the same harness.

**Unit 6: One canonical voice guide, a posting guard, and scoped repository memory**

2026-10-21: With Codex, I installed the voice guard and put my Unit 2-4 rules, plus claim/question/ping rules, in one guide used by the three live skills.
The hook stopped a real `gh issue comment --help` call, and Sonnet passed both versions of the claim draft.
I changed the scout to scope-feasible and kept difficulty separate from acceptance; I also allowed a report-back window in repro-check without promising a fix date.
Codex saved local repo notes and ran the 9/9 AppContext baseline, but the posting guard could not resolve a relative --body-file path, so Claude switched to an absolute path and posted the claim once.

**Unit 7: Ship-gate manifest from the frontend CI, a real gate PASS, and a voice-guard stop on the PR**

2026-10-28: With Claude Code, I put the frontend tests, typecheck, lint with Prettier and spell:quick in ship-manifest.md; both hooks stopped the `gh pr create --help` wiring test.
The baseline checks caught missing testdata in my sparse checkout and an unused import in my reproduction test, so those setup problems had to be handled first.
The gate passed all four project checks and all six pr-precheck checks, but the voice guard then stopped the emoji attribution line in the PR body.
I had the emoji removed and the gate ran again before the PR opened; afterward I had the ship-gate hook removed, keeping the gate files and manifest.

**Unit 8: A live PR-monitor run and a draft corrected before publication**

2026-10-28: With Codex, I installed the PR-monitor and a playbook based on my voice guide; switching to an existing logged-in Claude configuration got the Sonnet 5.5 run working.
The free --state check and full run found CodeRabbit feedback on PR #21606, MERGEABLE/BLOCKED status and no human review decision, then the monitor drafted a reply.
The draft picked the wrong discard path, dismissed the local deletion fix as unrelated and made unverified local-state claims; its 3 passing summary also missed workflows waiting for approval.
Codex kept that draft local and prepared a correction, with a 14-day minimum before considering a nudge; on November 3 I approved the replies posted after the fixes reached beee7db6.

---

## Why I Chose This Issue

I chose [Altinn/altinn-studio#10955](https://github.com/Altinn/altinn-studio/issues/10955) because it is a concrete UI problem: select a component, refresh the page, and the selection disappears.
It fits my React/TypeScript experience and gives me a reason to understand how URL state and React state work together.
I found it through the course Issue Selection site and graded it with my scout in Unit 5.
The thread named blocker PR #15947, but that PR had merged on October 27, 2025.
On October 21, the issue was open and unassigned, with no claim in the thread or referencing PR among the 142 open PRs checked.

My first course-site pick was #12123.
The scout ranked it higher, but it still had a 2024 claim and maintainer permission, so I switched to #10955 under Unit 6's stricter rule.
I released the old reservation and reserved #10955 on October 21; the screenshot records that course-site choice, while the GitHub comment below records the actual claim.
The Unit 6 scope-feasible re-grade accepted both issues, rating #10955 ambitious and #12123 straightforward.
I recorded that rubric change in scan-notes.md; the earlier 20/20 belongs to the Unit 5 version.

The scope was still uncertain.
Studio uses ux-editor for v9+ apps, ux-editor-v4 for versions 4-8 and ux-editor-v3 for older apps, with local selection state in the first two.
The issue was marked for consideration, and ready-for-dev had been removed on September 25, 2026.
I asked which editor the maintainers wanted covered; with no answer by October 28, I built the ux-editor candidate and kept that limit in the PR.

I used Codex and Claude Code to investigate the issue, build and check the changes, and draft this story from my records.
Codex prepared the first source investigation and baseline tests; I reviewed the final claim wording before it went out.

Claim comment: https://github.com/Altinn/altinn-studio/issues/10955#issuecomment-6330240501 (posted 2026-10-21 18:12 PDT).
It asks about the editor scope, names the first check, promises a report within a week and discloses Codex assistance.
Both draft versions passed claim-only repro-check and the guard's Sonnet check on October 21.
Only claim-specific and repo-conventions counted at that point; the other five checks needed a reproduction report.
Codex clarified the editor names and included the possibility that I could not reproduce it.
The final thread check found no new claim or PR.
During posting, the guard stopped the relative --body-file path, so Claude used an absolute path and posted the same text once.
GitHub's stored text matched the checked draft byte for byte.
As of November 3, no maintainer has replied or assigned the issue.
On October 28, I posted the report-back through Claude Code and the guard: https://github.com/Altinn/altinn-studio/issues/10955#issuecomment-6485588852.
It gives the remount result on main c298f416, names the untested browser and older editors, and proposes the v9+ PR unless the maintainers prefer another package.

**Toolkit**

- Tool: I used issue-scout in Unit 5, then Claude Code reran it on October 21 with scope-feasible.
- What it produced: #10955 and #12123 passed, while #14892 already had work covering it.
  The re-grade called #10955 ambitious and #12123 straightforward.
- Difficulties: the scout allowed an old claim that Unit 6 did not allow, and a course reservation did not settle GitHub availability or editor scope.
- What changed: I replaced one-bounded-task with scope-feasible, added live difficulty notes and confirmed the switch to #10955, with the scope question left open for the maintainer.

---

## Understanding the Issue

**Problem Description**

The issue is easy to describe: I select a component in the form editor, but refreshing the page loses that selection.
The requested change keeps track of the selected component without changing its ID, saved layout or submitted data.

**Expected Behavior**

The URL should remember the component I selected.
Opening that URL again should select the same component, with the page, tree highlight and properties panel agreeing.
The existing layout parameter should keep working.

**Current Behavior**

Before the fix, AppContext read the page from layout in the URL but kept later component selections in React state.
Codex tested this on 0a62afac023248918e345457044a72c6deda8052 by selecting Input and remounting the real provider at the captured URL.
The page came back as Side1, but the selected item became that page instead of Input.
The same test still failed on October 28 at main c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6, where the selection files were unchanged.

There was also a second copy to handle.
FormItemContext held the edited item used by the tree and properties panel, so restoring AppContext alone would not be enough.
The remount test confirmed the provider failure; it did not check a real browser refresh, the full editor route or the other editor versions.

**Affected Components**

- `ux-editor/src/AppContext.tsx`: holds selectedItem and reads the URL.
- `ux-editor/src/containers/DesignView/FormTree/FormTree.tsx`: updates both selection copies and highlights formItemId.
- `ux-editor/src/containers/FormItemContext.tsx`: holds the edited item and handles discard on mount/page changes.
- `ux-editor/src/components/Properties/ComponentConfigPanel/ComponentConfigPanel.tsx`: clears selectedItem during render when it has no edited item.
- `ux-editor/src/AppContext.test.tsx`: covers provider selection; the separate local remount test is included below and was removed after its after-fix run without being committed.
- `UiEditor.tsx`: chooses ux-editor, ux-editor-v4 or ux-editor-v3 by frontend version; v4 has a similar state problem, but remains outside this fix.

The ux-editor paths above are under src/Designer/frontend/packages/.

**Toolkit**

- Tool: I used Codex to trace the source, read the thread and check the repo's AGENTS.md and CONTRIBUTING.md.
- What it produced: the three editor entry points and local repo notes, followed by the two-copy selection flow above.
- Difficulties: reading a state setter did not prove a browser outcome, and the old issue did not specify today's editor-version split.
- What changed: I asked about the editor scope and kept source reasoning separate from the remount result.
  Claude Code rechecked main c298f416 and the updated repo rules on October 28, adding FormItemContext and ComponentConfigPanel to the explanation.

---

## Reproduction Process

**Environment Setup**

macOS 27.2 arm64; Node 22.23.3 selected through npx; committed Yarn 4.18.0; React 19.2.8; React Router 7.18.2; Vitest 5.0.1; Testing Library React 16.3.2; jsdom 30.1.1.
For this reproduction my source checkout was public Altinn/altinn-studio main at 0a62afac023248918e345457044a72c6deda8052; a read-only API check confirmed that this was also remote main during the run.
It was not a fork or implementation branch at that point, and no reproduction commit exists.
The initial sparse checkout omitted two workspaces; adding src/App/frontend and src/Designer/development/azure-devops-mock allowed the Node 22 immutable install to exit 0 without changing the lockfile.
The existing AppContext baseline passed 9/9 before the new local test was added.
No account, real application data, backend server, database or Docker stack was needed.
Codex wrote and ran the one authorized reproduction test with the real router/provider and the repository's synthetic fixtures and mocked backend services.
The npx form below no longer selects Node 22 on this Mac: it printed v22.23.4 at 18:22 PDT on October 28, Homebrew installed Node 26.13.0 at 19:34, and by 00:19 on October 29 it printed v26.13.0, as it still did on November 3.
To rerun these steps now, put a real Node 22 first on PATH, check `node --version`, and call `node .yarn/releases/yarn-4.18.0.cjs` directly.

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

- **Commit showing reproduction:** none - the test was a local untracked addition and was never committed, so its complete source is included below.
- **Expected:** after the fresh mount, selectedItem remains { type: 'component', id: 'Input' }.
- **Actual:** it becomes { type: 'page', id: 'Side1' }; the earlier runtime-selection and layout/same-URL checks pass.
- **Screenshots/logs:** no screenshot, because this ran as a test without a browser; the command exited 1, with one new failing assertion and all nine existing tests passing.

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

- Tool: Codex wrote and ran the real-provider/router test with existing fixtures, then checked lint and formatting; Claude Code ran repro-check on the claim and report together.
- What it produced: Input became page Side1 after remount, while all nine existing controls passed.
  The report includes the full test and output, and the full-package check accepted it.
- Difficulties: the green baseline had no remount case, the first test hit a naming rule, and one copied stdout line lost its leading space.
  The result still covered less than a browser refresh.
- What changed: Codex fixed the test naming and kept the failing assertion; Claude restored the exact output and removed an outdated pending note.
  This was the Unit 6 reproduction, before the implementation below.

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
  In that order React logs its "Cannot update a component while rendering a different component" warning from the existing render-time clear.
  The initial test required that warning; the local review follow-up removes that requirement so fixing the warning later will not break the behavior test.
- `FormItemContext`'s page-change effect only awaits `handleSave()` when an item is being edited.
  Why: with nothing to save, the await still moved `handleDiscard()` past the restore effect, which then cleared the restored item; `handleSave()` without an item does nothing.
- The URL tests went into a new `describe` in `AppContext.test.tsx` that swaps the file-wide `useSearchParams` mock for the real hook; `testing/mocks.tsx` gained an optional `search` for `AppRouter` and `renderWithProviders`.
- The reproduction command now reports `Tests 15 passed (15)`, not 10, because `AppContext.test.tsx` has five new tests; the reproduction file itself was unchanged (same SHA-256) for that run.
- The manual browser reload was not run: a local Studio needs a signed-in session, and the browser rules for this work exclude authentication, so the PR evidence is the before/after test output instead of a screenshot.

Review follow-up, October 28, local and uncommitted on top of c1e6c182:

- Codex reproduced the stale URL after a successful deletion through the real delete button, providers and router.
  FormItemTitle now clears component only in the successful explicit-deletion callback, preserving layout and unrelated parameters with replace.
  Putting that write in generic handleDiscard was rejected because that function also runs during page changes and could overwrite their URL update.
- The hook test helper now forwards search, with a regression that previously read null instead of Input.
- The late-pages test retains the Input panel, selection and no-save checks, but no longer requires React's warning and restores its targeted console spy in finally.
- The new FormItemTitle tests require no restoration after deletion and remount, and no query/selection change or save when deletion is cancelled.
  Draft PR #21442 remains open and now overlaps FormItemTitle.tsx; the PR's Follow-ups say this URL cleanup should follow the same condition if that draft lands.
- At that October 28 checkpoint these edits were uncommitted; they were pushed on November 3 as beee7db6, with the change below.

Review follow-up, November 3, published as beee7db6:

- FormItemTitle's URL write moved before the awaited preview refresh.
  Why: `setSearchParams` builds on the params of the render that started the callback, so a write after the await would undo a page change made during the refresh.
  Sol found this in review, and a new regression requires the parameter to be gone before the refresh finishes.
- Two cases Sol raised stay as they are and are listed under the PR's Risk: deleting a whole page or group leaves the parameter, and deleting a component removes it even when a different component was open.

**Toolkit**

- Tool: Claude Code ran my installed plan-check against the live thread on October 28, in the same session that wrote the drafts.
- What it produced: run 1 failed thread-and-conventions because the comment skipped "Blocked by #15947"; runs 2-4 passed all seven checks.
- Difficulties: the skill still had Path Review wording and expected posted reports/plans, while this phase kept them local.
  The writer also graded the drafts, so this was not an independent check.
- What changed: the drafts added the merged blocker, adjacent PR #21442 and the typecheck problem with its planned resolution.
  I kept the rubric and procedure unchanged and recorded those course-wording gaps.

---

## Testing Strategy

The published fix is two commits on branch fix/10955-keep-selected-component, based on main c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6: c1e6c182606974e8f1d29b6e97cbfe8d45bfdc37 and, for the review follow-up, beee7db6d0b52bbe064d1ea92d28a82b0ffcc1cc.
Items 1 to 6 ran on main and c1e6c182, item 7 on the uncommitted follow-up, and item 8 on the files committed as beee7db6.
Items 1 to 6 ran on October 28 between 18:22 and 19:05 PDT in fresh login shells with Yarn 4.18.0 and Vitest 5.0.1, through the npx command that printed Node 22.23.4 at 18:22, before Homebrew installed Node 26 at 19:34; those runs did not print their own version.
The full output and file hashes are saved locally, with published-commit and working-tree results separated.

1. Original failure, with the reproduction command from Reproduction Process and the test file unchanged (same SHA-256):
   - Before, on main: exit 1, `Tests 1 failed | 9 passed (10)`, `expected { type: 'page', id: 'Side1' } to deeply equal { type: 'component', id: 'Input' }`.
   - After, on c1e6c182: exit 0, `Tests 15 passed (15)`; the count grew because AppContext.test.tsx gained five tests.
2. Real editor state: a new FormItemContext test mounts the real AppContextProvider, FormItemContextProvider and properties panel at `?component=Input&layout=Side1`.
   The Input settings heading appears, selectedItem stays Input and no layout save is sent, also when the pages load after the layouts.
3. Neighbor behavior covered by the initial new tests: selecting a component writes `component` and keeps an unrelated parameter; selecting another page or closing the page in the same event removes `component` and keeps the page change; P1 -> P2 -> P1 restores page P1; an ID missing from the selected layout is not restored; a discarded component is not restored again during the same mount.
   Those discard tests did not check deletion followed by a remount, which the review regression below now covers.
   Renaming, adding a page and selecting a group use the same AppContext setter as the page change, but I did not add a separate test for each.
4. Without the source change, 8 of the 10 new tests fail; the other two are controls that already passed.
5. Repository checks from ship-manifest.md, all exit 0 on c1e6c182: the Designer frontend suite (10853 passed, 5 skipped), typecheck, ESLint (0 errors, 3 existing warnings) with Prettier, and `yarn spell:quick`.
   On main the same suite had 1 failure, my reproduction, and typecheck failed only on that untracked file's unused `React` import.
6. Not run: a real browser reload, which needs a signed-in local Studio, and anything in ux-editor-v4 or ux-editor-v3; hosted CI is reported separately in Pull Request.
7. Review follow-up: before the fixes, the helper query regression failed with null instead of Input, and the deletion regression failed because component=Input remained in the URL (the five existing FormItemTitle tests passed).
   With the local fixes, the final frontend suite returned `Test Files 1544 passed | 1 skipped (1545)` and `Tests 10856 passed | 5 skipped (10861)`.
   Typecheck, lint (0 errors, the same 3 schema-editor warnings), Prettier and spell:quick (8 changed files checked) all exited 0 on that working tree.
   The three added tests cover initial hook query parameters, successful deletion with query preservation and no restore after remount, and cancelled deletion without a save or query change.
   That run started at 20:17 PDT through the same npx command, after the Node 26 install, and did not print its version, so item 8 is the result I rely on.
8. Final follow-up, November 3: the regression for the URL write before the preview refresh failed first with `expected 'component=Input&layout=Side1' to be 'layout=Side1'`, then passed once the write moved; that focused pair ran through the npx command, which printed v26.13.0 that day.
   With Node 22.22.3 first on PATH and printed by the run, the full frontend suite, which includes that regression, returned `Test Files 1544 passed | 1 skipped (1545)` and `Tests 10857 passed | 5 skipped (10862)`.
   Typecheck, lint (0 errors, the same 3 warnings), `codestyle:check` and `yarn spell:quick` all exited 0.
   Hosted CI at beee7db6 still waits for maintainer approval, so none of this is a hosted result.

**Toolkit**

- Tool: Claude Code ran the reproduction, the new tests with and without the source fix, and the four manifest checks, saving the output.
- What it produced: the reproduction failed on c298f416 and passed on c1e6c182, eight new tests failed without the fix, and all four project checks passed on the branch.
- Difficulties: the checkout lacked testdata and scripts, spelling needed typos and hunspell, and late page data broke the first restore.
  On November 3, the supposed Node 22 command also turned out to run Node 26.
- What changed: Claude added the missing folders and spelling tools, kept the exclusion table empty and changed the restore to read the URL.
  After its unchanged after-fix run, I approved removing the local reproduction file whose unused import failed typecheck.
  The November 3 checks were rerun with Node 22.22.3 first on PATH and its version printed.

---

## Implementation Notes

**2026-10-28**

During the initial research and planning stage, nothing had been implemented; Claude Code handled the checkout updates, runs and tracing.
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
Later on October 28, I authorized Codex to fix two CodeRabbit Minor findings and its test nit locally, including corresponding tests and checks, while withholding commit, push, PR edits and comments.
The helper and deletion regressions failed before their fixes; the final working tree passed 10856 frontend tests with 5 skipped, typecheck, lint, Prettier and spell:quick.
The deletion fix belongs to the successful explicit-delete path, so generic discard during page changes still avoids writing the URL.
Codex updated the plan and evidence, left the existing React warning itself outside this follow-up, and at that checkpoint only prepared a Unit 8 playbook draft.
The remote PR remains at c1e6c182, with no human maintainer reply and major fork workflows still awaiting approval.
At 22:27 PDT, after I separately authorized installation and one full monitor run, Codex installed the official files unchanged and ran the free state check and the full Sonnet pass.
The default Claude configuration was not logged in; its failed startup attempts used zero tokens, and the existing configuration selected by cl --which then completed one actual Sonnet 5.5 drafting call.
The monitor classified the PR as feedback-in, but its reply suggested the generic discard path and dismissed the local deletion-path fix as unrelated, so Codex retained the original output and prepared a separate corrected draft for my review.
The settings, source and tests remained unchanged during the monitor run, and no response or nudge was posted.

**2026-11-03**

With my approval, Claude Code picked up the local follow-up and ran a Sol review through Codex.
Sol found that writing the URL after the awaited preview refresh could undo a page change, so the write moved before the await and gained a regression; Sol approved after two rounds.
Claude Code also found that the npx command for Node 22 now ran the host Node 26, so it reran the five checks with Node 22.22.3 first on PATH, and they passed with 10857 tests and 5 skipped.
The follow-up went out as beee7db6, the PR description was updated to match, and I approved the wording of the three thread replies before they were posted.
CodeRabbit accepted the fixes after reading the code, without running the tests, and withdrew its last finding; all three threads are resolved.
The issue and PR still have no human maintainer reply, and the main workflows are still waiting for approval.

**Toolkit**

- Tool: I used Claude Code for the initial implementation and tests, then Codex and Claude Code for the review follow-up, with commits on my fork after approval.
- What it produced: c1e6c182 changed the two providers, their tests and the router helper, with ten new tests; beee7db6 contains the November 3 follow-up.
- Difficulties: late page data exposed the render-time clear and the empty-save delay, and ESLint rejected an `import()` type in the test.
- What changed: the restore reads the URL and updates both selection copies, the page effect skips an empty save, and the test uses vi.importActual without that annotation.
  The plan and deviations record the changes.

---

## Pull Request

**PR Link:** https://github.com/Altinn/altinn-studio/pull/21606

**PR Description:** opened 2026-10-28 from hskl18:fix/10955-keep-selected-component at c1e6c182 into main, titled "fix(designer): keep the selected component after reloading the form editor", with the repository's Summary, Evidence, Risk and Follow-ups sections and Closes #10955.
The PR now points to beee7db6, and its description was updated on November 3 to match.
Summary: selecting a component in ux-editor (v9+ apps) puts its ID in a component query parameter, AppContext seeds the selection from it and drops it in the same URL update as a page change, FormItemContext restores the edited item once, so the tree and properties panel follow, and deleting a component removes the parameter; ux-editor-v4 and ux-editor-v3 are unchanged, and the scope question stays open.
Evidence: the remount reproduction went from `1 failed | 9 passed` on main to `15 passed` on c1e6c182, 8 of the 10 new tests fail without the change, and at beee7db6 on Node 22.22.3 the full frontend suite (10857 passed, 5 skipped), typecheck, lint, `codestyle:check` and spell:quick pass; hosted CI has not run, and there is no browser screenshot because I had no signed-in local Studio.
Risk and Follow-ups list the stale parameter for a missing ID or a deleted page or group, removal of the parameter when a different component was open, Back/Forward not reselecting, ComponentConfigPanel's render-time clear when the pages load late, the narrower autosave await, the untouched older editors, and draft PR #21442.
Notes for reviewers says Claude Code traced the flow, wrote the initial change and tests, ran the final checks and drafted the description, that Codex prepared and reviewed the follow-up, and that I approved the scope and the fixes; it also gives Sol's result.

**Maintainer Feedback:**

- 2026-10-28: none yet; my report-back on the issue and the PR have no maintainer reply.
  At opening, the main CI workflows were waiting for maintainer approval (`action_required`), so hosted CI has not run.
- 2026-10-28, later check at the same published head c1e6c182: CodeRabbit, a bot, left [a stale-URL finding after deletion](https://github.com/Altinn/altinn-studio/pull/21606#discussion_r4408104199), [a missing search forwarding finding](https://github.com/Altinn/altinn-studio/pull/21606#discussion_r4408104210), and a nit asking not to require React's warning in the late-pages test.
  Codex verified all three and prepared local fixes and tests with my authorization; they have not been committed, pushed or replied to, and the two review threads remain unresolved on GitHub.
  Designer unit tests, Playwright, Spell check, CodeQL and Lint PR remain action_required.
  The Labeler and Approve PR workflows and CodeRabbit check succeeded, but those results are not a human approval or proof that the blocked workflows passed.
  No human maintainer reply has arrived.
- 2026-10-28, 22:27 PDT: the PR-monitor read the same published head as feedback-in and drafted a response to CodeRabbit's round.
  Codex checked the draft against the local fix and kept it unpublished because its proposed generic-discard change and its claim that FormItemTitle changes were unrelated were wrong for this fix.
  A separate corrected response is ready for my review; no review reply or nudge has been sent.
- 2026-11-03: I addressed CodeRabbit's round in beee7db6 and replied on [the deletion thread](https://github.com/Altinn/altinn-studio/pull/21606#discussion_r4452494265), [the search-forwarding thread](https://github.com/Altinn/altinn-studio/pull/21606#discussion_r4452494555) and [a new thread on FormItemTitle](https://github.com/Altinn/altinn-studio/pull/21606#discussion_r4452616820).
  The deletion fix lives in FormItemTitle's delete-success callback, not the generic discard CodeRabbit suggested, and the reply explains why.
  All three threads are resolved, and CodeRabbit withdrew its last finding; this is still bot feedback.
  At beee7db6, Designer unit tests, Playwright, Spell check, CodeQL and Lint PR remain action_required, the review decision is REVIEW_REQUIRED, and no human maintainer has replied.

**Status:** Awaiting review; the PR is open at beee7db6, not merged, and needs human review and fork-workflow approval.

**Toolkit**

- Tool: Claude Code opened the PR through ship-gate and the voice guard; Codex later ran PR-monitor, and Claude Code arranged the November 3 Sol reviews through Codex.
- What it produced: four project checks and six pr-precheck checks passed before PR #21606 opened.
  The monitor drafted a reply, and Sol approved beee7db6 after two review rounds.
- Difficulties: the sparse checkout hid the PR template, the guard stopped an emoji, the monitor needed a logged-in configuration and chose the wrong discard path, and the Node 22 command later ran Node 26.
  The monitor's check summary also missed blocked workflows.
- What changed: I had the CI-status line added and the emoji removed before the gate reran, then had its hook removed after opening while keeping its files.
  Codex kept both reply drafts local and checked the code and Actions API; I approved the November 3 replies against beee7db6 after checks on a real Node 22.

---

## Learnings and Reflections

**Technical Skills Gained**

The main thing I took from this is that one selection on screen can live in more than one place in the code.
AppContext chose the panel, while FormItemContext held the edited item and tree selection.
Both had to be restored together.

I also had to pay attention to when the URL changes.
React Router 7.18.2 builds setSearchParams updates from the last render, so two writes in one click can undo each other.
The later review found the same risk across an await during deletion.
Even awaiting a save with nothing to save changed the effect order and cleared the restored item.

The useful test pattern was to use the real router and providers, capture the URL, then remount at it.
Checking the new tests without the source fix helped show what they actually caught.
The setup mattered too: sparse-checkout folders, the Node version and spelling tools all affected whether the project checks could run.
I also worked through Altinn's fork workflow, PR template and CI approval process.

**Challenges Overcome**

- I changed issues after finding the old claim on #12123, even though the scout had accepted it.
- Without a signed-in Studio, I used the provider remount as narrower evidence and kept the missing browser check visible.
- The late-pages test caught a first fix that looked fine in the simpler cases, so Claude changed the restore source and skipped the empty save.
- Some failures came from my setup: missing testdata, an unused import and a body-file path the guard could not read.
  The guard also stopped the emoji in the PR description, and plan-check caught the missing explanation of blocker #15947.
- The monitor drafted a reply that chose the wrong discard path and missed blocked workflows in its summary.
  Codex checked that against the code and Actions API before any response went out.

**What I'd Do Differently Next Time**

- Run the full checks as soon as I add a test, and print `node --version` in each evidence run.
  The same npx command later used Node 26, so I cannot treat the command text as proof of the version.
- Add the different-data-arrival-order test earlier; that case changed the design.
- Check early whether a local test app can support a browser run and screenshot.
- Spend more time reviewing the AI-written description before approving it, and keep the publishing agent's task narrow after it edited a local notes file outside its assigned scope.
- Report progress earlier than the last day of the window, leaving time for the maintainer to steer the scope.

---

## Resources Used

- [Altinn/altinn-studio#10955](https://github.com/Altinn/altinn-studio/issues/10955): the issue and its one maintainer-side comment, "Blocked by #15947", which I had to address in my plan.
- [Altinn/altinn-studio#9335](https://github.com/Altinn/altinn-studio/issues/9335): the umbrella issue that lists "the current selected element should be passed as a query param" for the UI editor, which supported using a query parameter.
- [Altinn/altinn-studio#15947](https://github.com/Altinn/altinn-studio/pull/15947): the merged blocker that put the layout set in the editor's route.
- [CONTRIBUTING.md](https://github.com/Altinn/altinn-studio/blob/c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6/CONTRIBUTING.md) and the [PR template](https://github.com/Altinn/altinn-studio/blob/c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6/.github/pull_request_template.md) at c298f416: fork-based PRs, Conventional Commits titles, `yarn spell:quick`, and the four description sections.
- [designer-frontend-unit-tests.yml](https://github.com/Altinn/altinn-studio/blob/c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6/.github/workflows/designer-frontend-unit-tests.yml): the CI job my ship-manifest checks come from.
- [scripts/spellcheck/README.md](https://github.com/Altinn/altinn-studio/blob/c298f416ecc5dd1bceaccbd6be18cc42f9ad17d6/scripts/spellcheck/README.md): what `yarn spell:quick` checks and which tools it needs.
- React Router 7.18.2's installed `useSearchParams` source in node_modules, which showed that the functional update starts from the last render's params.
- [Draft PR #21442](https://github.com/Altinn/altinn-studio/pull/21442): neighboring work on selection after deletes that I checked my change against.
- [codepath/ai301-unit7-starter](https://github.com/codepath/ai301-unit7-starter) and its skill/INSTALL.md: the ship-gate install, the wiring test and what each stop means.
- [codepath/ai301-unit8-starter](https://github.com/codepath/ai301-unit8-starter): the PR-monitor files I installed unchanged and the playbook template.
