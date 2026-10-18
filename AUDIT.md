# Split audit — K3-scallop-migration

How this repository was carved out of the pristine **K** monorepo. Regenerate the classification with [`K-audit` v1.0](https://github.com/abdh0saifelden2-debug/K-audit/tree/v1.0) — `python3 classify.py --mono K K3-scallop-migration` — and re-check the import graph with `python3 verify_repo.py --mono K K3-scallop-migration` (both run from a clone of `K-audit` against a clone of the monorepo).

## Claim cluster

the scallop instability family, migration, and channelisation.

Source: `glaciers/scallop_*.py`, `run_candidate3.py`, the scallop reports, `glaciers/tests/**` (15 files), `subglacial/**` (whole, incl. `data/`), + `general_two_clocks/closure/**` and `compressible/**`.

## Composition

| | files |
|---|---|
| traced to a monorepo file | 108 |
| byte-identical copies | 104 |
| modified (see *Edits*) | 4 |
| new (not in the monorepo) | 1 |

Source directories, by file count:

- `glaciers/` — 27
- `glaciers/figures/` — 26
- `glaciers/subglacial/` — 23
- `glaciers/tests/` — 15
- `general_two_clocks/closure/` — 7
- `(monorepo root)`/ — 3
- `general_two_clocks/compressible/` — 3
- `glaciers/subglacial/data/` — 2
- `glaciers/subglacial/moving_boundary/` — 2

## Vendored files

Copied byte-for-byte from the monorepo paths below (this is what makes the repo import-clean on its own):

- `repo root/*` (27 files)
- `closure/*` (7 files)
- `compressible/__init__.py`
- `compressible/ns.py`
- `compressible/solver.py`
- `figures/*` (25 files)
- `subglacial/*` (23 files)
- `subglacial/data/bedmap1_transect.csv`
- `subglacial/data/bushuk_raw_derived.json`
- `subglacial/moving_boundary/__init__.py`
- `subglacial/moving_boundary/stefan.py`
- `tests/*` (15 files)

## Edits

- `README.md` — rewritten to stand alone: no `../` links into sibling monorepo folders, run commands given from the repo root, and a Provenance section pointing at the archive.
- `pyproject.toml` — rewritten for this repo: `testpaths`/`pythonpath` scoped to this repo instead of all five monorepo domains, and the dependency list trimmed to the libraries this claim cluster imports.
- `requirements.txt` — rewritten for this repo: `testpaths`/`pythonpath` scoped to this repo instead of all five monorepo domains, and the dependency list trimmed to the libraries this claim cluster imports.

## Excluded files

- `subglacial/THEORY_CAVITY.md` — the 3-D cavity theory note belongs to the K2 cavity cluster (kept in the archive).

## Test-suite accounting

`tests/` carries **15 test files** (glaciers/tests (51) − 36 that went to K2); the whole monorepo has 136 test files across the five repos (78+36+15+2+2 = 133, plus the 3 excluded in K1).

## Verification

[`K-audit`](https://github.com/abdh0saifelden2-debug/K-audit/tree/v1.0) `verify_repo.py` walks the **AST import graph** of every Python file in this repo, expands each unqualified import against every `sys.path` root the file would actually see, and reports any import that resolves only outside the repository. Result:

```
OK K3-scallop-migration: no external edges
```

## Provenance

Pristine snapshot taken **before** any edit: `K-monorepo-archive.tar.gz` (SHA-256 `ef637ff55f912a5d1404f677429f9429eccc8102a8cab23cee79cf055bbf1220`). `FUTURE_WORK.md` / `PAPER_OUTLINE.md` were deliberately left in the archive.
