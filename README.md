# tiny-chess-engine

A 4,096-byte Python chess engine for make.fun `tiny-chess-01`.

0x88 board, negamax with transposition table, killers, MVV-LVA ordering,
quiescence, null-move pruning, late-move reductions, check extensions and
mate-distance pruning. Tapered material + piece-square evaluation with pawn
structure and passed-pawn bonuses. Fixed node budget (40,000 nodes/move),
no clock, no randomness — fully deterministic.

`main.py` is the packed entrypoint (packed with the kit's `makefun compress`).
