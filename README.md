# escrow-kit

`escrow-kit` is a compact Solidity repository for blockchain tooling, centered on this goal: Model escrow release, refund, timeout, and invariant scenarios.

## Use Case

The point is to make a small domain rule concrete enough that a reader can change it and immediately see what broke.

## Escrow Kit Review Notes

The first comparison I would make is `proof depth` against `settlement risk` because it shows where the rule is most opinionated.

## Highlights

- `fixtures/domain_review.csv` adds cases for event finality and nonce pressure.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/escrow-kit-walkthrough.md` walks through the case spread.
- The Solidity code includes a review path for `proof depth` and `settlement risk`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## Code Layout

The implementation keeps the scoring rule plain: reward signal and confidence, preserve slack, penalize drag, then classify the result into a review lane.

The Solidity checks add a pure review lens and Foundry coverage.

## Run The Check

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Regression Path

The same command runs the local verification path. The highest-scoring domain case is `recovery` at 221, which lands in `ship`. The most cautious case is `edge` at 133, which lands in `watch`.

## Future Work

The fixture set is small enough to audit by hand. The next useful expansion is malformed input coverage, not extra surface area.
