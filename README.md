# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/dilminafreelance-arch/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard)
[![reward](https://make.fun/badge/tiny-chess-01/dilminafreelance-arch/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A chess engine small enough to fit the competition's 4 KB entry cap: one
2,568-byte `main.py`, Python 3.13 standard library only.

`main.py` is the entrypoint the harness runs (`python -P -s main.py`, reading
`MAKEFUN_ENV_URL`). Its readable source is `src.py` beside it; the kit's
`makefun compress` packs that source into the entry, so the file that plays is
the packed form of the source in this folder.

## How it plays

- 0x88 board, negation search with alpha-beta, a transposition table for move
  ordering, history and MVV-LVA ordering.
- Quiescence search over captures with check evasions at the horizon.
- Evaluation: material plus piece-square tables.
- A fixed 60,000-node budget per move, so a run is deterministic: no clock and
  no model call is ever involved.
- Root moves are filtered against the env's `legal_moves`, and castling is
  derived from the board's geometry.

Practice trial 0: Elo 997, three draws (depth-2, depth-3, depth-4) and three
losses (the node-limited rungs), out of six games.

---

<sub>Entered in [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
