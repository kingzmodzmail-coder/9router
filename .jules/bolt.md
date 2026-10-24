## 2023-10-24 - Memoize table cells
**Learning:** In highly complex and interactive data grids with grouped views, frequent re-renders caused by row expansion/collapse can significantly degrade client rendering performance. Un-memoized child components (like `ValueCells` or `SortIcon`) will unnecessarily re-render whenever the parent orchestrator updates its layout state.
**Action:** Always wrap simple prop-based presentational components inside list/table bodies with `React.memo` or `memo` to avoid re-rendering entire grids when a single row interaction occurs.
