# Escrow Kit Walkthrough

I use this file as a small checklist before changing the Solidity implementation.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | event finality | 151 | ship |
| stress | nonce pressure | 200 | ship |
| edge | settlement risk | 133 | watch |
| recovery | proof depth | 221 | ship |
| stale | event finality | 140 | ship |

Start with `recovery` and `edge`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

`recovery` is the optimistic case; use it to make sure the scoring path still rewards strong signal.
