# Scallop migration — the constructive result, and channelisation

The **scallop** cluster: the instability family that turns the two-clocks
closure failure into a *positive* morphological prediction — a damped,
downstream-migrating wall mode that K-theory cannot produce — plus the
channelisation consequences (R-channel nucleation) and the Bushuk et al. (2019)
field comparison.

The two-clocks *observation* and closure benchmarks live in
**`K1-two-clocks-theory`**; the cavity DNS and the real-bed/field validation
pipeline live in **`K2-subglacial-cavity`** (same monorepo split — see
Provenance).

## What was found so far

**The scallop (the constructive result)**
- **[VERIFIED/DERIVED, RESULT 14 + 22 + 23]** The scallop is a *damped,
  downstream-migrating* mode `s = −β + i·ω_mig`: no autonomous growth
  (smoothing-limited), `K²` curvature ansatz falsified, and migration
  `∝ U^{0.5–0.8}` is a **parity-symmetry break no K-theory closure can produce**
  (keystone control measured on GPU). Verdicts generalized across amplitude
  `a₀/λ ∈ [0.05, 0.40]` and drive up to `U = 6`
  ([`REPORT_SCALLOP_MIGRATION.md`](REPORT_SCALLOP_MIGRATION.md), Fig 56).
- **[VERIFIED directional]** Scallop reattachment melt is a phase-locked opening
  source that deterministically selects R-channel nucleation sites
  ([`REPORT_CHANNEL.md`](REPORT_CHANNEL.md),
  [`REPORT_CHANNEL_Z0.md`](REPORT_CHANNEL_Z0.md), Figs 49, 50b); shedding-edge
  **[NULL]** made conclusive ([`REPORT_SHEDDING.md`](REPORT_SHEDDING.md), Fig 51).
- **[FALSIFIED]** the `(a/λ)²` amplitude closure (Fig 59); the `K²` curvature
  ansatz (RESULT 22); 3-D scallop geometry **[NULL — closed]** (§D.7).
- **[VERIFIED]** Candidate 3 (roughness feedback)
  ([`REPORT_CANDIDATE3.md`](REPORT_CANDIDATE3.md)).

## What remains a HYP

- **The field test of RESULT 14** is the open step: compute
  `I_obs = τ·c_mig/λ` on a real scallop train (Bushuk et al. 2019 is the
  candidate dataset) — the single step that moves RESULT 14 from a discovery
  *in the framework* to a discovery *about the world* (`scallop_field_test.py`
  is ready, Fig 58; `scallop_bushuk_raw.py` / `bushuk_fig3_digitize.py` digitize
  the published figure).
- Whether the amplitude-family verdicts survive 3-D unsteady drive (the 3-D
  geometry check closed NULL, but the *migration* parity break has only been
  measured in 2-D).

## What is pending

- Running `scallop_field_test.py` against the digitized Bushuk scallop train.
- GPU re-runs of the keystone control on a CUDA device.
- Coupling the verified migration law into the cavity solver of
  `K2-subglacial-cavity` (the two clusters share the same `subglacial/` library).

## Contents

- `scallop_*.py` (20 scripts) — amplitude band/closure/harmonics, battery sweep,
  branch solver adapter, channel feedback + z₀ robustness, drive cut, field test,
  forcing probe, G1 populations, k-theory control, moving-boundary check, probe,
  shedding, sublayer convergence.
- `scallop3d_probe.py` — the 3-D geometry probe (§D.7, NULL-closed).
- `run_candidate3.py` — Candidate 3 runner (Roughness feedback).
- `bushuk_fig3_digitize.py`, `scallop_bushuk_raw.py` — Bushuk et al. (2019) figure
  digitization / raw-array handling.
- `subglacial/` — the cavity/scallop library, vendored whole (`flow.py`,
  `flow3d.py`, candidates 1–4, Stefan/moving-boundary, `data/`).
- `closure/`, `compressible/` — vendored leaf solver dependencies from the theory
  cluster (see `AUDIT.md`).
- `figures/` — Figs 49–51, 56, 58–59. `tests/` — 15 test modules.

## Quick start

```bash
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
python scallop_amplitude_harmonics.py
python run_candidate3.py
python -m pytest            # 111 passed, 1 skipped
```

> **Note on figures:** some tests re-derive figure JSONs (`figures/58_*`), which
> rewrites them with float-level last-digit noise. `git checkout -- figures/`
> restores the committed values; the pristine copies are also in the archive.

## Provenance

Split out of the **K** monorepo, partitioned by claim cluster:

| repository | claim cluster |
|---|---|
| `K1-two-clocks-theory` | observation, two-clocks theory, closure benchmarks |
| `K2-subglacial-cavity` | cavity DNS, real-bed validation, field-analysis validation |
| `K3-scallop-migration` *(this repo)* | scallop instability family, channelisation |
| `K4-swirl-vortex` | atmospheric vortex application |
| `K5-ocean-probes` | ice–ocean double diffusion |

The pristine monorepo was snapshotted **before** any edit:
`K-monorepo-archive.tar.gz`, SHA-256
`3c30c68b4d4287787af00539b2cbe75a47dc0536491ec0d1b17a0f61d80b5304`
(`K-monorepo-archive.sha256`). The cross-repo claim ledger (`FUTURE_WORK.md`)
and paper outline are deliberately **not** copied here — they live only in that
archive. [`AUDIT.md`](AUDIT.md) records the full split audit: every vendored
file, every edit, and the AST verification result.
