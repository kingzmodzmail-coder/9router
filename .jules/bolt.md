## 2024-03-24 - Intl instantiation is slow
**Learning:** `new Intl.NumberFormat()` and `new Intl.DateTimeFormat()` are surprisingly expensive to instantiate in JS compared to regular operations (can take ~0.1-1ms per instantiation). If used inside a `map` or render function for hundreds of items (like in a usage table), it creates a measurable CPU bottleneck and delays rendering.
**Action:** Always extract `Intl.NumberFormat`, `Intl.DateTimeFormat`, and `Intl.DisplayNames` initializations to top-level module constants rather than creating them inline in functions or components.
