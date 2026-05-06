# escrow-kit

`escrow-kit` is a focused Solidity codebase around model escrow release, refund, timeout, and invariant scenarios. It is meant to be easy to inspect, run, and extend without a hosted service.

## Escrow Kit Walkthrough

I would read the project from the outside in: command, fixture, model, then roadmap. That keeps the blockchain tooling idea grounded in files that can be checked locally.

## Reason For The Project

This project keeps the domain idea close to the tests. That makes it useful as a reference implementation, a small experiment, or a starting point for a more specialized tool.

## How It Is Put Together

The design is intentionally direct: parse or construct a signal, score it, classify it, and verify the expected branch. This makes the repository useful for studying blockchain tooling behavior without needing a service or database unless the language project itself is SQL. The Solidity project uses Foundry tests and pure contract functions so invariants are cheap to exercise.

## Data Notes

`pressure` is the first example I would inspect because it lands on the `review` path with a score of 113. The broader file also keeps `degraded` at -5 and `recovery` at 244, which gives the model a useful low-to-high spread.

## Capabilities

- Uses fixture data to keep event replay changes visible in code review.
- Includes extended examples for invariant checks, including `recovery` and `degraded`.
- Documents settlement rules tradeoffs in `docs/operations.md`.
- Runs locally with a single verification command and no external credentials.
- Stores project constants and verification metadata in `metadata/project.json`.

## Getting It Running

Clone the repository, enter the directory, and run the verifier. No database server, cloud account, or token is required.

## Check The Work

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/audit.ps1
```

The audit command checks repository structure and README constraints before it delegates to the verifier.

## Where Things Live

- `src`: primary implementation
- `test`: language test directory
- `fixtures`: compact golden scenarios
- `examples`: expanded scenario set
- `metadata`: project constants and verification metadata
- `docs`: operations and extension notes
- `scripts`: local verification and audit commands
- `foundry.toml`: Foundry project configuration

## Tradeoffs

The examples cover useful edges, not every edge. A larger version would add malformed-input tests, richer reports, and deeper domain parsers.

## Possible Extensions

- Add a short report command that prints the score breakdown for a single scenario.
- Add malformed input fixtures so the failure path is as visible as the happy path.
- Split the scoring constants into a typed configuration object and validate it before use.
- Add one more blockchain tooling fixture that focuses on a malformed or borderline input.

## Command Examples

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

This runs the language-level build or test path against the compact fixture set.
