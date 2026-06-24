# current_state.md

Authoritative project status for the Agentic AI Security & Governance Reference Model.
Last updated: 2026-06-24.

## Model shape
- 51 sequential boxes across 9 layers (L-4 → L4), contiguous partition:
  L-4: 1–3 · L-3: 4–7 · L-2: 8–11 · L-1: 12–18 · L0: 19–23 · L1: 24–27 · L2: 28–39 · L3: 40–45 · L4: 46–51.
- Gold-standard reference: **Box 33 — Output Commitment Control** (pattern: Risk → Threshold → Control → Metric → Evidence).

## Box pages — gold standard
- **51 / 51 boxes at gold standard.** All carry the full structure: trust domains, governance dependencies, linked Risks → Controls → Metrics → Evidence tables, assurance model, scenarios, maturity ladder and regulatory alignment.
- Legacy long-form template fully retired (was Boxes 37, 42, 45, 50).
- Legacy "canonical shell" pages fully retired (was Boxes 7, 9, 10, 11, 13, 14, 16, 17).
- Stale renumbering artefacts removed: "Box 30 Alignment / full-depth alignment" footers and labels retargeted to Box 33; "numbering reconciliation" and "Box NN Expansion" shells removed.

## Detail tier (controls / risks / metrics / evidence)
- Four libraries populated: `controls/`, `risks/`, `metrics/`, `evidence/` (the latter two created during build-out).
- Every box-referenced detail page exists. Pages authored to gold standard are full; the remainder are **honest placeholders** carrying real ID, name, description, type/consumer and a back-link to the parent box, with a "detail to be authored" scaffold.
- **Live tier: 0 broken internal links** across all box pages, detail libraries, `index.html` and `architecture.html` (~862 pages).

## ID convention — standardised
- **Single scheme across all 785 detail pages: `<type>-<domain>-<NNN>`** (e.g. `c-occ-001`, `r-a2a-006`, `m-pac-003`, `e-bvm-002`); displayed codes `C-OCC-001` etc.
- The newer `<dom>-cNN` scheme (Box 33 reference and 18 other boxes) was migrated to this convention; 359 files renamed, all references and displayed codes updated.
- One collision resolved: Box 10's `a2a` risk/evidence items bumped to `r-a2a-006` / `e-a2a-004` to avoid clashing with Box 22's `r-a2a-005` / `e-a2a-003`. No duplicate codes remain.

## Governance artefacts
- 26 shared governance artefact pages present under `governance/`.
- Substantive: Enterprise Commitment Threshold Matrix, Risk Scoring Policy (Threshold Matrix partial). The remaining ~23 are placeholder stubs awaiting authoring.

## Housekeeping — done
- Added `.gitignore`; removed all `.DS_Store`; deleted obsolete `DELETE_FILES_FOR_RENUMBERING.txt`.
- Deleted obsolete `index_old.html` (v17) and the stale `pages/agentic_update_externalized_controls_identity_mesh/` orphan (held the last 46 broken links).
- Moved process/audit notes to `docs/process/`.
- Fixed stale "42 boxes" → "51 boxes" in `theindex.html`.
- **Result: 0 broken internal links across the entire repository.**

## Vendor / legacy-duplicate cleanup — done
- Deleted 10 orphaned legacy control pages (`C-A2A-007` … `C-RT-001`) carrying "Palo Alto" vendor wording, and the 10 matching orphaned legacy risk pages (`R-*`).
- Deleted the orphaned `pages/AI_Reference_Model_Control_Risk_Libraries_v1/` snapshot folder and its `.zip`.
- Rebuilt `controls/index.html` and `risks/index.html` as consistent library indexes.
- **No "Palo Alto" / "idira" vendor wording remains in the live tier.**

## Operational decisions — resolved
- Working view (`theindex.html`) is **internal-only**: the public "Open Working View" link was removed from `index.html`. The file is retained but not linked publicly.
- In-repo `.zip` snapshots (`current_Archive.zip`, slides zip) and the mislabeled `slides/robots` archive removed.
- ID convention standardised on `<type>-<domain>-<NNN>` (see above).

## Content phase — in progress
- **Authoring order: L2 (Model Layer, boxes 28–39) first**, then spine-first (C1→C2→C3) per the delivery sequence in `backlog.md`. (Authoring order ≠ delivery order — deliberate.)
- Detail-tier pages are authored to audit-grade depth (control objective/statement/design/I-O/test/failure/regulatory; risk scenario/rating/controls/residual; metric definition/formula/target; evidence field-schema), fully cross-linked, with draft ATT&CK/ATLAS mapping on risk pages (backlog 10a preview).
- **L2 (Model Layer, boxes 28–39) detail tier COMPLETE — 12 / 12 capabilities authored (~198 detail pages).** Box 35 (Autonomous Risk Scoring) tagged Frontier/emerging throughout (backlog item 7).
- 0 broken links maintained throughout.

## Next (content phase)
- Begin the spine per the delivery sequence: C1 (Identity & Execution — boxes 22, 24, 25, 26, 27) → C2 (Policy Contract — 08, 09, 16, 41, 42) → C3 (Telemetry/Evidence/SecOps — 43, 46, 47, 48).
- Then remaining layers (L-4, L-3, L-2, L-1, L0, L1, L3, L4) capability by capability.
- Fill the ~23 governance placeholder pages.

## Provenance
See `SITE-INTEGRITY-AUDIT-AND-CLEANUP-PLAN.md` for the full audit that established this baseline.
