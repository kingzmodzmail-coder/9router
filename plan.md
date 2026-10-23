1. **Goal**: Identify and implement a measurable performance improvement in `ModelSelectModal.js`.
2. **Issue**: `ModelSelectModal.js` manages a large list of models, aliases, and combinations. The search feature updates state `searchQuery` on every keystroke, which cascades down to filter and render a very large list of DOM nodes. This creates input lag, blocking the main thread during typing (a common React performance issue for large lists).
3. **Solution**: Use `useDeferredValue` to debounce the heavy rendering of the search results, keeping the input fast.
    - Import `useDeferredValue` from `react` in `src/shared/components/ModelSelectModal.js`.
    - Create a deferred version of `searchQuery`: `const deferredSearchQuery = useDeferredValue(searchQuery);`.
    - Update all dependent memos (`parsedQuery`, `filteredCombos`, `filteredGroups`, etc.) to use `deferredSearchQuery` instead of `searchQuery`. This allows the text input to update at 60fps while the expensive filter/render operations happen in the background without blocking the UI.
4. **Impact**: Prevents typing lag when filtering the large model catalog, a very noticeable speed improvement on low-end devices and large model sets. Measurement: typing into the search box will be significantly smoother (no UI blocking).
5. **Code Changes**: Edit `src/shared/components/ModelSelectModal.js` to add `useDeferredValue`.
6. **Pre-commit Instructions**: Run the verification step for tests and formatting, log the journal.
7. **Submit**: Create PR with title "⚡ Bolt: [performance improvement]" and required description.
