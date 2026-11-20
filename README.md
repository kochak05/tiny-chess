[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/kochak05/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/kochak05/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01)

# tiny-chess

A small chess engine in 4 KB of Python. It plays the env's games over
HTTP (`$MAKEFUN_ENV_URL`), one move at a time.

How it plays: a 10x12 mailbox board, legal move generation for all the
rules (castling, en passant, promotion, check evasion), alpha-beta with
iterative deepening to a fixed 60,000-node budget, quiescence over
captures and check replies, a transposition table, MVV-LVA ordering,
and an evaluation of material plus piece-square terms. No clock, no
randomness: the same position always gives the same move, so a replay
matches the live trial.

`main.py` is the whole engine (4,058 bytes): a short unpacker that
decompresses an lzma payload and runs it. Standard library only.

Run it with the env up:

    MAKEFUN_ENV_URL=http://127.0.0.1:18080 MAKEFUN_TRIAL_SEED=test0 python3 main.py
