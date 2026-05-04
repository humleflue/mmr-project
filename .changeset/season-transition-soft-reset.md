---
"api": patch
---

Restore season-transition handling on the v3 match calc. The first match a
player plays in a new season is now flagged `IsPreviousSeasonRating` on the
calculator request, and its recorded delta is forced to 0 so the leaderboard
doesn't show a phantom swing on transition. Whole-season recalc now resets
each affected player to their most recent prior-season rating snapshot
(rather than absolute defaults) before replaying, so the previous-season
input reaches the calculator unchanged.
