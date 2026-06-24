# Site Integrity Audit & Cleanup Plan

**Date:** 2026-06-22
**Author:** Claude (integrity custody) — for Val to review and commit
**Scope:** Full repo `agentic-ai-security-reference-model` (published site + working files)

Per project working model, this report separates **[CORRECTNESS]** assertions (Claude's job to make and defend) from **[DIRECTION]** decisions (Val's to commit). Nothing here is treated as decided. No site files have been changed — this is assessment + proposal only.

---

## 1. Verdict

The core model is structurally sound: **51 box pages exist (01–51), the renumbering is fully complete** (all old-numbered files confirmed gone), and the **26 governance artefact pages are all present**. The published surface (`index.html`, `architecture.html`) is internally consistent on the box model itself.

However, there is **one serious integrity defect and a layer of housekeeping debris**:

- **[CORRECTNESS] 623 of 1,057 internal links from the box pages are broken (59%).** 47 of 51 box pages link to control / risk / evidence / metric detail pages that do not exist. The `evidence/` and `metrics/` directories don't exist at all.
- The public homepage itself links to two missing directories and exposes the internal working view.
- Multiple stray/obsolete files (old entry point, archives, `.DS_Store`, empty dirs, completed process notes) clutter the repo.

This is **not** a regression in the box model — it's an unfinished build-out of the detail tier underneath it, plus accumulated working cruft.

---

## 2. Integrity findings  [CORRECTNESS]

### P0 — Broken detail-tier links (the headline issue)

The 51 box pages each link out to per-capability **controls**, **risks**, **evidence**, and **metrics** detail pages. Counts:

| Target dir | Broken links | Directory status |
|---|---:|---|
| `metrics/` | 189 | **does not exist** |
| `controls/` | 175 | exists, 10 detail pages, **none match** referenced names |
| `risks/` | 144 | exists, 10 detail pages, **none match** referenced names |
| `evidence/` | 115 | **does not exist** |
| **Total** | **623 of 1,057** | 47 / 51 box pages affected |

Two compounding problems:

1. **Missing directories.** `evidence/` and `metrics/` are referenced ~300 times but don't exist. Every such link is dead.
2. **Naming mismatch.** The 10 existing files in `controls/` use short uppercase codes (`C-A2A-007.html`); box pages reference long lowercase slugs (`c-a2a-007-structured-agent-payload-boundary.html`). They don't resolve to each other. **All 10 existing control pages are orphaned** — not linked by any box page. Same pattern in `risks/`.

So the detail tier is effectively a stub: a handful of sample pages under one naming scheme, with the box pages pointing at a different (larger, unbuilt) scheme.

### P1 — Public homepage points at missing dirs and the internal view

- `index.html` (public, v18) links to `controls/`, `risks/`, `evidence/`, `metrics/` as top-level nav. `evidence/` and `metrics/` are broken; `controls/`/`risks/` resolve only to near-empty index pages.
- `index.html` contains an **"Open Working View" button linking to `theindex.html`** — the internal working view.

**[CORRECTNESS] This contradicts the repo's own `integrity_validation_v2.json`**, which asserts `index_contains_working_view_public_link: false`. Either the validation is stale or the link was re-added after. Flagging the discrepancy; the *direction* call (should the public page expose the working view?) is Val's.

### P2 — Competing entry points

| File | Title / role | Assessment |
|---|---|---|
| `index.html` | Public homepage (v18) | Canonical public entry |
| `architecture.html` | Rich 51-box model (v18) | Canonical, clean |
| `theindex.html` | "…Reference Architecture **v18**" — working view | Internal; keep but mark/segregate |
| `index_old.html` | "…**v17**" | **Obsolete, fully orphaned** — archive or delete |

### Governance tier (expected, not a defect)

24 of 26 governance artefact pages are still the ~5.6 KB **"Placeholder page for future expansion"** stub. Only `enterprise-commitment-threshold-matrix.html` and `risk-scoring-policy.html` carry real content (`threshold-matrix.html` is partial). This matches the stated project goal ("26 governance artefact pages being filled in from placeholders") — listed here for completeness, not as a fault.

---

## 3. Housekeeping / stray-file inventory

| Item | What it is | Proposed action |
|---|---|---|
| `index_old.html` | v17 obsolete homepage, orphaned | Archive then delete |
| `DELETE_FILES_FOR_RENUMBERING.txt` | To-do list for renumbering — **all listed files confirmed already gone** | Delete (task done) |
| `current_Archive.zip` (418 KB) | Repo snapshot archive | Move out of repo / delete |
| `slides/ciso_agentic_ai_html_slides.zip`, `pages/AI_Reference_Model_Control_Risk_Libraries_v1.zip` | Zips duplicating live folders | Remove from repo |
| `slides/robots` | Mislabeled file — actually a **zip archive**, not robots.txt | Delete or rename |
| 5 × `.DS_Store` | macOS cruft (root, `pages/`, `slides/`, `reconciliation/`, library) | Delete + add to `.gitignore` |
| Empty dirs: `capabilities/ overlays/ service-domain/ data/ assets/` | Scaffolding, no files; `assets/` referenced by nothing | Delete or add `.gitkeep` if intentional |
| `pages/agentic_update_externalized_controls_identity_mesh/index.html` | Orphan using **old box numbering** (box-13/14/32/42…), broken links | Archive/delete — superseded |
| `pages/AI_Reference_Model_Control_Risk_Libraries_v1/` (+ zip) | Library snapshot duplicating `controls/`+`risks/` | Decide canonical source, then dedupe |
| ~12 root process notes: `FIX-NOTES.md`, `L2-GOLD-STANDARD-UPDATE-NOTES.md`, `EXECUTIVE-LANDING-UPDATE-NOTES.md`, `DEPLOYMENT_CHECKLIST.md`, `V18-RELEASE-NOTES.md`, `architecture_html_*` (2), `architecture_*_audit.md` (2), `integrity_*` (4), `numbering_validation.*` (2), `PACKAGE_MANIFEST.md`, `current_state.md`, `backlog.md` | Working/maintenance artefacts in repo root | Move to a `docs/` or `_process/` folder |

`robots.txt` (real one), `README.md`, `CHANGELOG.md`, `Fractal-Invariants.md`, `PROJECT-INSTRUCTIONS.md`, `canonical_box_inventory.md` stay at root.

---

## 4. Proposed cleanup plan (phased)

Claude executes file edits; **Val runs all git**. Each phase is independently committable.

**Phase 0 — Safe housekeeping (no risk, no direction needed).** Delete the 5 `.DS_Store` files and add a `.gitignore` (`.DS_Store`, `*.zip`); delete obsolete `DELETE_FILES_FOR_RENUMBERING.txt`; rename/remove the mislabeled `slides/robots`. → Claude can do immediately on Val's go.

**Phase 1 — Entry-point hygiene.** Archive `index_old.html` (v17) and the stale `pages/agentic_update_externalized_controls_identity_mesh/` orphan out of the live tree. Resolve the `theindex.html` public-link question (see Decision A). → Needs Decision A.

**Phase 2 — Repo root tidy.** Move ~12 process/audit notes into `docs/process/`. Decide whether `current_Archive.zip` and folder zips belong in the repo at all. → Needs Decision B.

**Phase 3 — The real work: detail-tier link integrity.** This is the substantive fix and needs a direction call (Decision C) before building. Options range from "build the ~620 missing detail pages" to "collapse links to anchors within existing pages" to "stub-generate placeholders matching the referenced slugs." → Needs Decision C.

**Phase 4 — Verification.** Re-run the link checker to confirm 0 broken internal links; confirm box count = 51, governance = 26; regenerate an honest `integrity_validation.json` reflecting actual state. → Claude, after each phase.

---

## 5. Decisions needed from Val  [DIRECTION]

**A. Working view exposure.** Should the public `index.html` keep the "Open Working View → `theindex.html`" button, or is the working view internal-only (matching what `integrity_validation_v2.json` claims)?

**B. Archives & process notes.** OK to (i) move root process/audit `.md`/`.json` into `docs/process/`, and (ii) remove `*.zip` snapshots from the repo (they're recoverable via git history)?

**C. Detail tier — the big one.** How should the 623 broken control/risk/evidence/metric links be resolved?
  - *Option C1 — Build out:* author real detail pages for all referenced slugs (largest effort; most complete site).
  - *Option C2 — Generate matching stubs:* auto-create placeholder pages at the exact referenced paths (fast; kills all broken links; honest "in progress" content). Mirrors how governance placeholders already work.
  - *Option C3 — Collapse links:* rewrite box pages so controls/risks render as in-page sections/anchors instead of links to separate files (no detail tier).
  - *Option C4 — Reconcile naming:* if detail pages are meant to be the 10 existing short-code files, decide the canonical scheme and rewrite the box-page links to match.

  Claude's correctness recommendation: **C2 now** (immediately eliminates 623 broken links with honest placeholders, consistent with the governance pattern), then **C1 incrementally** as content is authored. This is a *narrowing* of the existing placeholder convention, not a new exception. Val commits the direction.

---

## 6. What was NOT changed

No site files were modified during this audit. The only filesystem touch was a throwaway access-test file (created and deleted during the access check). The renumbering, the 51 box pages, and the 26 governance pages were left exactly as found.
