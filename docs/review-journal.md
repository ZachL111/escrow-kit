# Review Journal

The review surface for `escrow-kit` is deliberately narrow: one fixture, one scoring rule, and one local check.

The local checks classify each case as `ship`, `watch`, or `hold`. That gives the project a small review vocabulary that matches its blockchain tooling focus without claiming live deployment or external usage.

## Cases

- `baseline`: `event finality`, score 151, lane `ship`
- `stress`: `nonce pressure`, score 200, lane `ship`
- `edge`: `settlement risk`, score 133, lane `watch`
- `recovery`: `proof depth`, score 221, lane `ship`
- `stale`: `event finality`, score 140, lane `ship`

## Note

A future change should add new cases before it changes the scoring rule.
