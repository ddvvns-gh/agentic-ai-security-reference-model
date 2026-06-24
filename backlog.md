# backlog.md

Working backlog for the Agentic AI Security & Governance Reference Model.
Last refreshed: 2026-06-24. Scope: the reference-model artefact (repo) + an optional delivery view.
Westpac-internal programme/org actions (exec owner, funded team, 3LoD rhythm) are intentionally **out of scope** here — see the source reviews in `docs/reviews/` for those.

External validation: an independent enterprise/AI-security architect review (`docs/reviews/02`, `03`, dated 2026-06-17) rated the model design ≈8.5/10 ("coherent, sane, grounded in mid-2026 standards, in places ahead"), with deficiencies that are "overwhelmingly *unfinished*, not *wrong*." The items below fold the high-value, model-actionable callouts into our backlog.

---

## Done (integrity baseline)
- 51/51 boxes at gold standard; single ID convention; **0 broken links repo-wide**.
- Vendor wording removed; stale renumbering text purged; housekeeping complete.
- `architecture.html` threat-coverage matrix: stale pre-renumbering bracket numbers corrected (e.g. Output Commitment [33], Memory Governance [32], Policy/Evaluator Hub [42], HITL [40]).

## Now — content phase (highest priority)
1. **Populate detail-tier libraries for prioritised boxes** (not all 51 at once): author real Risk/Control/Metric/Evidence content over the existing honest placeholders, using the gold template (control objective, design, enforcement point, I/O, test method, failure mode, residual risk, regulatory mapping).
2. **Fill the ~23 governance placeholder pages** under `governance/`.
3. **Add metric targets/thresholds.** Metric IDs exist; targets largely don't — define them.

## Model-completion backlog
4. **Assign an accountable owner (RACI) per prioritised box.** A box with no owner is not a control. (Review §4.1.4 / §3.1.3.)
5. **Even out depth across all 51 boxes** — apply the full expansion template everywhere (most are now gold; keep parity as content lands).
6. **Publish the draft Prodspec schema** (box 08) and the evidence/decision-lineage schema (box 43) — flagged as foundational / "instrument first."

## Model-strengthening callouts (from review — proposed for commit)
7. **Feasibility tiering — Standard / Engineering / Frontier(R&D).** Tag each capability; explicitly mark **box 35 (Autonomous Risk Scoring)** and **box 41 (Constitutional Evaluation)** — plus reliable semantic memory-poisoning detection and full intent-provenance — as *emerging/experimental*, not mature controls. (Review §4.2.11 / §3.1.4.)
8. **Current-vs-target heatmap.** Add a vendor-neutral *Have / Partial / Gap* overlay per box so the model can drive a roadmap rather than read as all-target-state. (Review §4.1.3 / §3.1.2.) *(Proposal — deferred by Val: complex; revisit once the model has no content gaps and the backlog permits.)*
9. **Anchor boxes to the wire protocols & identity standards.** Reference **MCP** and **A2A** in boxes 09/10, **OTel-GenAI** in box 46, and **SPIFFE/SPIRE, OAuth-for-agents, NIST NCCoE identity** in boxes 10/22/25. (Currently near-absent in the pages.) (Review §3.3 / §3.1.5.)
10. **Threat-framework crosswalks.**
    - (a) **MITRE ATT&CK (Enterprise) + ATLAS technique mapping** — map each *risk* to the technique IDs it represents and each *control* to the techniques it mitigates. ATLAS for AI-native techniques (prompt injection, model/memory poisoning); ATT&CK Enterprise for the post-foothold blast radius (valid accounts, execution, lateral movement, exfiltration, persistence). Implement as a `technique(s)` field in the risk and control detail templates (authored alongside content), plus a consolidated ATT&CK-Navigator-style crosswalk view. Anchors on the SecOps boxes (28, 34, 46, 47) and gives the risk/control libraries real detection-engineering / SOC weight. **(Val: high priority — ranks above the CoSAI/SAIF crosswalk.)**
    - (b) **CoSAI / Google-SAIF crosswalk** alongside the existing OWASP/NIST/ATLAS mapping — cheap credibility win for assurance reviewers. (Review §3.3.)
11. **Name the agent-specific detection layer** (inline prompt-firewall / Model-Armor-class, MCP-server scanning, agent inventory discovery) in boxes 47/48, not just generic XDR/SIEM/SOAR. (Review §3.3.)
12. **Strengthen recovery/reconciliation after compensation** (box 34 follow-on): how dependent-system state is reconciled after a compensating action, since many agent actions are irreversible. (Review §4.2.12.)
13. **Make economic-DoS a first-class security control** — connect FinOps runtime limits (boxes 02/31) to the decision-routing gateway, not just cost reporting. (Review §4.2.9.)
14. **Note the data-estate dependency** for boxes 11/29 (assume governed classification/lineage upstream); flag as a precondition. (Review §4.2.10.)
15. **Size the operating-model / human-factors load** — control owners, evaluators, approvers, IR, assurance — so the model isn't silently assuming a large standing operation. (Review §4.2.13.)

## Hygiene / presentation
16. **"Gold-Standard Capability Governance Pack" wording leaks into capability page titles** (header `<span>` on all gold pages). Reviewer flags this as a process artefact in the capability name — decide on cleaner header wording and apply across pages. (Review §1 / §3.1.6.) *(Logged per your call; not yet changed.)*
17. **Verify the ambiguous `Evidence [51]`** reference in the architecture threat matrix (left unchanged; confirm it means box 51 / assurance vs box 43 / evidence).
18. **Ship a clean "governance edition"** separate from the working repo when presenting to a governance/exec audience (process notes now under `docs/process/`). (Review §1 / §3.1.6.)

## Optional delivery view — 7 component workstreams (reviewer's decomposition)
A risk-sequenced grouping of the 51 boxes for delivery (vs. the 9 reading-order bands). Useful as an alternative lens; not a change to the model.

- **C1 · Identity & Execution Trust** — boxes 22, 24, 25, 26, 27
- **C2 · Policy Contract & Enforcement** — 08, 09, 16, 41, 42
- **C3 · Telemetry, Evidence & SecOps** — 43, 46, 47, 48
- **C4 · Supply-Chain & Provenance** — 04, 05, 06, 07
- **C5 · Runtime Data/Tool/Memory/Cost** — 28, 29, 30, 31, 32, 33
- **C6 · SDLC Validation & Release** — 10, 12, 14, 15, 17, 18
- **C7 · Governance, Accountability & Resilience** — 01, 02, 03, 11, 13, 34–40, 44, 45, 49, 50, 51

Suggested sequence (spine first): **C1 + C2 + C3 → C5 + C4 → C6 + C7 → frontier**, pulling **output-commitment (33)** and **FinOps limits (31)** forward as high-leverage. (Review §4–5.)

---

## Provenance
- `docs/reviews/02-Security-Reference-Model-Evaluation.md` — standalone evaluation.
- `docs/reviews/03-AI-Security-Strategy-Pivot-Recommendation.md` — pivot/sequencing recommendation.
- `current_state.md` — authoritative build status.
