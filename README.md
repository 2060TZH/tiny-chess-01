# tiny-chess-01

[![competition](https://img.shields.io/badge/competition-tiny--chess--01-blue)](https://make.fun/competitions/tiny-chess-01)
[![entry](https://img.shields.io/badge/entry-main.py-green)](https://github.com/2060TZH/tiny-chess-01/blob/master/main.py)
[![make.fun](https://img.shields.io/badge/built%20with-make.fun-orange)](https://make.fun/r/zfzt2mbb)

A compact chess engine in 4 KB of Python, built for the
[make.fun](https://make.fun/competitions/tiny-chess-01) competition
**tiny-chess-01**: build the strongest chess engine in 4 KB of Python.

Built with make.fun — enter at https://make.fun/r/zfzt2mbb

## The entry

`main.py` (3,952 bytes) is an original alpha-beta engine:

- 0x88 board, alpha-beta search with quiescence, transposition table,
  iterative deepening under a fixed 30,000-node budget per move
  (about 1.2 s per move, well under the 10 s limit)
- PeSTO tapered evaluation (middlegame/endgame interpolation, tables
  symmetrized to 32 squares per piece to fit 4 KB) plus null-move
  pruning (R=2, no null move in check or in pawn-only positions)
- deterministic: the search runs to a fixed node budget, never a clock,
  and makes no model calls
- Python 3.13 standard library only; talks only to the environment over
  HTTP at `$MAKEFUN_ENV_URL` (`POST /game`, `/move`, `/resign`)

Round 3 (2026-11-17): the evaluation was switched from sunfish PSTs to
PeSTO (tapered MG/EG) and null-move pruning was added. Local practice
trials (6 games each): PeSTO alone tied v1 at 6.0/12; PeSTO + NMP scored
4.5/6 on trial-0 (~1545) and 2.5/6 on trial-1, 7.0/12 overall (~1364),
the best 12-game total so far (v1: 6.0/12).

Round 2 (2026-11-17): the node budget was reverted from 50,000 to
30,000 after the 50,000-node version and a PVS variant both scored
below the practice floor on the 6-game practice trial (997 and 1099),
while the 30,000-node version scored 1364.

`engine.py`, the readable source `main.py` is packed from, is kept out of
this repository so the entry tree stays under the 8,192-byte cap.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

## License

GPL-3.0-only. See `LICENSE`.
