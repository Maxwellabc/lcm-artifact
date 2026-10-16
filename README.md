# Anonymous Local Harmonic Centrality Minimization Artifact

Complete source code and reproducibility materials for **Sharper Approximation
and Certified Search for Local Harmonic Centrality Minimization**. Author
information is withheld for double-blind review.

## Download and reproduce

The source is distributed as one complete archive (not a GitHub source-tree
checkout):

1. Download [lcm-artifact.zip](lcm-artifact.zip).
2. Check its [SHA256 checksum](lcm-artifact.zip.sha256).
3. Extract the archive and read `ARTIFACT_README.md` in the extracted directory.
4. Check the file hashes against the included `ARTIFACT_MANIFEST.json` using
   `python3 scripts/verify_artifact_manifest.py --strict` before adding data.

The [file manifest](ARTIFACT_MANIFEST.json) lists all 186 packaged files. The
archive contains Python source, tests, locked dependencies, acquisition and
verification scripts, target lists, frozen result logs, vector-figure scripts,
and anonymous paper source/PDF. Raw graphs, private records, credentials,
development environments, and prior Git history are excluded.

From the extracted directory:

```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements-lp-lock.txt
.venv/bin/python -m unittest discover -s tests -v
.venv/bin/python scripts/audit_structural_bounds.py
```

Use Python 3.9 for the locked environment. Data-dependent checks also require
following `data/README.md` to acquire and hash-check the inputs.

## Source map (inside the archive)

| Component | Path |
|---|---|
| Exact budget profile | `lcm/profile.py` |
| Baselines, local search, and certified hybrid | `lcm/algorithms.py` |
| Cut certificates | `lcm/flow.py` |
| Historical BlockMatch | `blockmatch/algorithm.py` |
| Integer-weight BlockMatch | `blockmatch/exact.py` |
| Independent original-graph objective | `lcm/objective.py` |
| Low-degree exact-optimum verification | `scripts/verify_blockmatch_real_graph_audit.py` |
| Marginal-floor audit | `scripts/audit_structural_bounds.py` |
| Reproduction guide | `ARTIFACT_README.md` |
| Claims and evidence | `paper/CLAIM_EVIDENCE.md` |
| Reference audit | `notes/REFERENCE_AUDIT_2026-10-15.md` |

## Evidence and limits

The frozen primary study has 198 target-budget cells. A separate, explicitly
exploratory low-degree study has 48 cells, 3,239 independently enumerated
feasible sets, and 240 verified method outputs. BlockMatch reaches the optimum
in 47/48 cells and overlap search in 48/48; the failure case is retained.
The integer theorem audit covers 49,152 coverage-system cardinality cells and
1,293 directed-graph cardinality cells. There are 13 unit tests.

Numerical results were reproduced from a fresh extraction using the locked
workspace environment; this was not a fresh dependency installation. The
subsequent code-link-only paper update was rebuilt separately and checked for
identical text on all 12 pages. Full details and scope are in the audit records.

## Third-party terms

Materials are provided for review and reproduction. This repository makes no
new general software license grant. Third-party materials retain their terms;
see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). Raw graphs and the unlicensed
predecessor source repository are not redistributed.
