# XDV Cross-Domain Scheduler
Version: 0.1.1
Status: active-split
Language: Dust Programming Language (DPL)

## Specification Alignment
- Primary: XDV-012 (Cross-Domain Scheduler)
- Reference: XDV-082 (Cross-Domain Scheduler Reference)

## Purpose
`xdv-cds` is the deterministic arbitration engine for K/Q/Phi scheduling in XDV.
It provides:
- policy-driven deterministic arbitration,
- replay-stable ordering keys,
- starvation and fairness constraint validation.

## Scope Implemented in 0.1.1
- Deterministic arbitration API with policy plug-ins:
  - round-robin, priority, EDF, coherence-aware, domain-fair.
- Replay-stable ordering:
  - deterministic order key generation,
  - replay match/mismatch validation.
- Fairness enforcement helpers:
  - starvation detection,
  - fairness skew validation,
  - combined scheduler constraint validator.

## Public Surface
Core module: `src/cds.ds`

Key APIs:
- `arbitrate_next_domain(...)`
- `schedule_tick_with_policy(...)`
- `schedule_tick_replay(...)`
- `compute_replay_order_key(...)`
- `validate_starvation_constraints(...)`
- `validate_fairness_constraints(...)`
- `validate_scheduler_constraints(...)`

Version APIs:
- `xdv_cds_interface_version_major()`
- `xdv_cds_interface_version_minor()`
- `xdv_cds_interface_version_patch()`
- `xdv_cds_arbitration_api_version()`
- `xdv_cds_replay_api_version()`
- `xdv_cds_fairness_api_version()`

## Repository Layout
- `src/`: implementation, stable interface, tests
- `docs/`: architecture and contract docs
- `tests/`: standalone test suite placeholders
- `State.toml`: workspace manifest
- `changelog.md`: release notes

## Build
`cargo run --manifest-path dust/Cargo.toml -- check xdv-cds/src`

## Integration Notes
- `xdv-kernel` consumes `xdv_cds_interface_version_*` from this project.
- Arbitration and fairness decisions are deterministic and replay-compatible by construction.
