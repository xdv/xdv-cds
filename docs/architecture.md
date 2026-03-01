# Architecture

`xdv-cds` is split into two layers:
1. Stable interface surface (`src/cds_interface.ds`)
2. Deterministic scheduling implementation (`src/cds.ds`)

## Deterministic Arbitration Pipeline
1. Validate policy support.
2. Apply deterministic policy weighting/priority boost.
3. Compute replay-stable ordering keys.
4. Resolve ties deterministically.
5. Return domain decision + replay key.

## Policy Plug-In Behavior
Supported policy IDs:
- `POLICY_ROUND_ROBIN`
- `POLICY_PRIORITY`
- `POLICY_EDF`
- `POLICY_COHERENCE_AWARE`
- `POLICY_DOMAIN_FAIR`

Plugins are deterministic transforms and do not introduce stochastic behavior.

## Replay-Stable Ordering
- `compute_replay_order_key(...)` generates stable ordering keys.
- `schedule_tick_replay(...)` validates expected vs actual decisions using replay keys.

## Fairness and Starvation
- `detect_starvation(...)` and `validate_starvation_constraints(...)` identify wait-time risks.
- `validate_fairness_constraints(...)` enforces bounded skew across domains.
- `validate_scheduler_constraints(...)` combines starvation and fairness validation.
