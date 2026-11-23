# Design — tiny-chess-01
One-file chess engine, <=4,096 bytes of Python, stdlib only.
main.py = lzma(XZ, preset 9) + base85 of the golfed source, exec'd.
Board: 120 squares; side to move is uppercase, board rotates
180 degrees and swaps case after each move. Full legal move
generation (castling, en passant, promotions), perft-verified.
Search: negamax + alpha-beta, TT, PVS, null-move pruning, LMR,
check extensions, killers; quiescence with in-check evasions.
Deterministic: fixed 24,000 nodes/move, no clock; games replay
exactly. Eval: material + file-symmetric PSTs, tapered king
table by phase. Ordering: TT, MVV-LVA, promotions, killers, PST.
Revision (2026-11-23): knight PST centre (d4/e4/d5/e5) 20 -> 25.
Self-play vs previous build, cap 1,500 nodes, 6 openings x 2
colours: W2 D8 L2, score 0.500 — not worse, so the change is kept.
Packed size unchanged: main.py is 3,955 bytes.
