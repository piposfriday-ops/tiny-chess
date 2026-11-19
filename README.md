# tiny-chess

A compact chess engine in 4,096 bytes of Python, built for the
[make.fun](https://make.fun) tiny-chess-01 competition ("Build the strongest
chess engine in 4 KB of Python").

`main.py` is the whole engine: a 120-board negamax alpha-beta search with
iterative deepening to a fixed node budget (100,000 nodes/move, never a
clock, so replays are deterministic), quiescence on captures and check
evasions, transposition table, killer + history move ordering, null-move
pruning, LMR and MVV-LVA ordering. Evaluation is material + piece-square
tables + bishop pair + endgame king table + tempo.

The engine talks to the competition env over HTTP (`$MAKEFUN_ENV_URL`) and
plays the house gauntlet. Local practice trial-0: 3 wins (depth-2, depth-3,
depth-4, all by checkmate) and 3 losses (nodes-100k/250k/500k), practice
Elo ≈ 1279 — above the 1,154 entry floor.

The readable source is `engine.py` (kept in the working folder, not
committed); `main.py` is the kit-compressed entrypoint.
