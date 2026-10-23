## 2024-05-20 - [Deferred Value for Large Filtering]
**Learning:** Using `useDeferredValue` is highly effective for debouncing search input in React when filtering a very large list of DOM nodes (like a catalog of hundreds of models). It prevents the UI from freezing by deferring the heavy re-render.
**Action:** Always consider `useDeferredValue` when a user input drives a heavy filter over a large static or semi-static list in a modal or dropdown.
