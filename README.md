# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/piposfriday-ops/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/piposfriday-ops/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

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
plays the house gauntlet. Local practice trial-0: 4 wins (depth-2, depth-3,
depth-4, nodes-100k, all by checkmate) and 2 losses (nodes-250k/500k),
practice Elo ≈ 1451 — above the 1,154 entry floor.

The readable source is `engine.py` (kept in the working folder, not
committed); `main.py` is the kit-compressed entrypoint.
