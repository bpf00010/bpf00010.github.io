# Linux enterprise directory optimization

**Environment:** Statler College IT · 100 Ubuntu workstations  
**Outcome:** Domain login latency reduced from **60 seconds to 10 seconds**, approximately an 83% reduction.

## The problem

Slow domain logins created a recurring delay across the Ubuntu workstation fleet. The optimization focused on SSSD's directory lookup behavior: search scope, nested group resolution, and caching.

## Tuning approach

| Area | Change | Purpose |
| --- | --- | --- |
| Directory search scopes | Narrowed the scope of directory searches | Reduce unnecessary lookup work |
| Group nesting depth | Tuned nested group traversal | Limit resolution overhead while preserving required memberships |
| Caching | Tuned cached identity and group information | Reduce repeated directory lookups |

These settings interact: reducing search scope or nesting depth too aggressively can exclude required identities or groups, while cache choices affect how quickly directory changes become visible. The final configuration needs to preserve access requirements as well as improve login speed.

## Result

The reported login duration fell from 60 to 10 seconds across an environment of 100 Ubuntu workstations. Exact SSSD settings, directory layout, and measurement conditions were not supplied, so this page avoids presenting guessed values as the production configuration.

## Verification evidence to retain

A reproducible comparison should record cold- and warm-cache login timings, confirm required nested group memberships, and verify that access changes propagate as expected. Sanitized configuration excerpts and timing records can substantiate the result without exposing the directory structure.
