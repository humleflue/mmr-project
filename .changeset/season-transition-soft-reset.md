---
"api": patch
---

Restore the season-transition soft reset for v3 match calculations. The
first match a player plays in a new season is now flagged
`IsPreviousSeasonRating` on the call to the MMR calculator, which collapses
the player's mu 2/3 toward the default and resets sigma. The recorded delta
for that first-of-season match is also forced to 0 so the leaderboard
doesn't show a phantom swing on transition.

Whole-season recalculation now resets each affected player to their most
recent rating from a prior season (rather than absolute defaults), so the
soft reset has the correct input on replay. Without this, replaying a
season collapsed every player toward the new-player baseline regardless of
their prior skill.
