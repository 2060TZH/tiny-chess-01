# tiny-chess-01

[![competition](https://img.shields.io/badge/competition-tiny--chess--01-blue)](https://make.fun/competitions/tiny-chess-01)
[![entry](https://img.shields.io/badge/entry-main.py-green)](https://github.com/2060TZH/tiny-chess-01/blob/master/main.py)
[![make.fun](https://img.shields.io/badge/built%20with-make.fun-orange)](https://make.fun/r/zfzt2mbb)

A compact chess engine in 4 KB of Python, built for the
[make.fun](https://make.fun/competitions/tiny-chess-01) competition
**tiny-chess-01**: build the strongest chess engine in 4 KB of Python.

Built with make.fun — enter at https://make.fun/r/zfzt2mbb

## The entry

`main.py` (3,762 bytes) is an original alpha-beta engine:

- 0x88 board, alpha-beta search with quiescence, transposition table,
  iterative deepening under a fixed 50,000-node budget per move
  (about 2 s per move, well under the 10 s limit)
- piece-square evaluation (tables follow sunfish, used under GPL-3.0-only
  with credit; the search, move generation and driver are original)
- deterministic: the search runs to a fixed node budget, never a clock,
  and makes no model calls
- Python 3.13 standard library only; talks only to the environment over
  HTTP at `$MAKEFUN_ENV_URL` (`POST /game`, `/move`, `/resign`)

`engine.py`, the readable source `main.py` is packed from, is kept out of
this repository so the entry tree stays under the 8,192-byte cap.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

## License

GPL-3.0-only. See `LICENSE`.
