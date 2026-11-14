# tiny-chess-engine

A 4,096-byte Python chess engine for make.fun `tiny-chess-01`.

0x88 board, negamax with transposition table, killers, MVV-LVA ordering,
quiescence, null-move pruning, late-move reductions, check extensions and
mate-distance pruning. Tapered material + piece-square evaluation with pawn
structure and passed-pawn bonuses. Fixed node budget (80,000 nodes/move),
no clock, no randomness — fully deterministic.

`main.py` is the packed entrypoint (packed with the kit's `makefun compress`).

## Revision: search budget 40k → 80k

The budget was raised from 40,000 to 80,000 nodes per move and the entry
re-packed with `makefun compress`. Practice trial-0 at 80k (same six
openings, same opponents) scored 2 wins, 1 draw, 3 losses — Elo 1,191 on
the kit's anchor scale, inside the noise of the 40k mean (1,159) and above
the 1,154 practice floor for the final. Wall time 752 s of the 1,800 s
limit; slowest single move 5.4 s of the 10 s limit. The trial harness's
summary script was fixed in the same pass: it read win/draw/loss counters
that this trial's state file never writes, so it reported Elo 0 — the
points now come from the games list itself.
