# Interface Contract
Project: XDV Cross-Domain Scheduler
Specification: XDV-012 / XDV-082
Forge: XdvCds

## Versioning
- Interface version: 0.1.0
- Arbitration API version: 1
- Replay API version: 1
- Fairness API version: 1
- Stability tier: frozen_normative

## Contract Rules
- Arbitration must be deterministic for identical inputs.
- Policy plug-ins may adjust weighting/priority, but must not introduce randomness.
- Tie-breaking is replay-stable.
- Fairness and starvation checks return deterministic status codes.

## Public Files
- `src/cds.ds`
- `src/cds_interface.ds`

## Key Public APIs
- `set_scheduler_policy(...)`
- `arbitrate_next_domain(...)`
- `schedule_tick_with_policy(...)`
- `schedule_tick_replay(...)`
- `compute_replay_order_key(...)`
- `validate_starvation_constraints(...)`
- `validate_fairness_constraints(...)`
- `validate_scheduler_constraints(...)`

## Stable Version APIs
- `xdv_cds_interface_version_major()`
- `xdv_cds_interface_version_minor()`
- `xdv_cds_interface_version_patch()`
- `xdv_cds_arbitration_api_version()`
- `xdv_cds_replay_api_version()`
- `xdv_cds_fairness_api_version()`
