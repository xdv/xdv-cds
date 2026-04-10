# Changelog

## 0.1.1 - XDV-012 / XDV-082 Deterministic Arbitration Milestone
- Replaced placeholder scheduler logic in `src/cds.ds` with deterministic arbitration core.
- Added policy plug-in architecture for:
  - round-robin,
  - priority,
  - EDF,
  - coherence-aware,
  - domain-fair policies.
- Implemented replay-stable ordering support:
  - `compute_replay_order_key(...)`,
  - decision packing/unpacking,
  - replay validation path.
- Implemented fairness and starvation validators:
  - starvation detection,
  - fairness skew checks,
  - combined scheduler constraint validation.
- Added stable CDS API version markers:
  - arbitration/replay/fairness API version functions.
- Replaced placeholder tests in `src/cds_tests.ds` with deterministic behavior tests.
- Updated interface surface in `src/cds_interface.ds` with namespaced version methods.

## 0.1.0 - Sector Split Baseline
- Created standalone project from `xdv-kernel/sector/xdv_cds`.
- Copied source module and tests into `src/`.
- Added stable interface file: `src/cds_interface.ds`.
- Added initial docs and interface contract.
- Added LICENSE copied from `xdv-os/LICENSE`.
