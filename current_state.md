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

## ID conventions (open item for standardisation)
- Two conventions coexist: older `c-<dom>-NNN` (most of the original 38 boxes) and `<dom>-cNN` (Box 33 gold reference and all boxes built/upgraded since). Standardisation is a pending direction decision; no functional impact.

## Governance artefacts
- 26 shared governance artefact pages present under `governance/`.
- Substantive: Enterprise Commitment Threshold Matrix, Risk Scoring Policy (Threshold Matrix partial). The remaining ~23 are placeholder stubs awaiting authoring.

## Known cleanup backlog (not yet done)
- Phase 0 housekeeping: `.gitignore` + remove `.DS_Store`, delete obsolete `DELETE_FILES_FOR_RENUMBERING.txt`, archive `index_old.html` and the stale `pages/agentic_update_externalized_controls_identity_mesh/` orphan (its 46 broken links are the only ones left in the repo), move process notes to `docs/`.
- Public `index.html` exposes the working view (`theindex.html`) and is the one decision still open from the audit.

## Next
- Author real content into the highest-priority detail-tier placeholders, capability by capability.
- Begin filling the ~23 governance placeholder pages.
- Resolve the ID-convention and working-view-exposure decisions.

## Provenance
See `SITE-INTEGRITY-AUDIT-AND-CLEANUP-PLAN.md` for the full audit that established this baseline.
