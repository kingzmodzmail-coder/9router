## 2025-05-18 - Missing Memoization in List Views
**Learning:** I searched the codebase and found exactly zero uses of `React.memo()`. This means that long lists, tables (like `UsageTable`), and complex iterating views are currently experiencing O(N) re-renders when a single item changes (e.g. toggling an accordion row).
**Action:** When optimizing performance in lists or tables, look for missing `React.memo` around rows or complex list items to change O(N) renders into O(1).
