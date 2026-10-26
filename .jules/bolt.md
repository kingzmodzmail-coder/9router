
## 2024-05-18 - Optimized TimeAgo Component
**Learning:** React components that use `setInterval(..., 1000)` inside `useEffect` can cause significant background re-rendering when rendered in lists (like in RecentRequests tables). This triggers unnecessary React cycles even when the visible text ("10m ago", "2h ago") only changes every minute or hour.
**Action:** Replace fixed 1-second intervals with adaptive timeouts based on the current age of the timestamp. When less than a minute old, update every second; when less than an hour, update every minute; otherwise update every hour or day. This significantly reduces main-thread activity for long lists of relative timestamps while maintaining perceived real-time accuracy.
