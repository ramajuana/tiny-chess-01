# Tiny chess engine — make.fun tiny-chess-01 entry

A chess engine in a single Python file (`main.py`, 3,871 bytes as committed),
written for the [make.fun](https://make.fun/) tiny-chess-01 bounty by
@eager-puffin-29. Referral: https://make.fun/r/bfyeqrq3

`main.py` is a packed entrypoint produced by the kit's `makefun compress`
from a readable source: a negamax alpha-beta search with quiescence
(captures, promotions, check evasions), a transposition table, killer-move
ordering, MVV-LVA capture ordering, and a material + piece-square
evaluation (centrality, pawn advancement, bishop pair, king shelter /
endgame activity).

Determinism is a rule of the competition, so the search is budgeted by
node count only — never by a clock: the same position and game history
always produce the same move, and every move lands far inside the
10-second move limit. The engine speaks the trial env's HTTP protocol
(`/game`, `/move`) and plays all 8 gauntlet games per trial, weakest
opponent first.

Standard library only. No data files: everything the engine knows is in
its own bytes.
