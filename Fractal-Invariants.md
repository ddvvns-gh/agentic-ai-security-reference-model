# Fractal Invariants — the shared spine of UETF and the Agentic AI Security Reference Model

**Status:** canonical · shared reference · v1.0 (June 2026)

## Purpose

The **Unified Entity Trust Fabric (UETF)** and the **Agentic AI Security & Governance Reference Model** are deliberately **one fractal system**: an abstract authority model (UETF) and its operational/security instantiation (the reference model). This file is the **coherence contract** between them.

Rules of use:

- **Both projects cite this file.** A copy lives in each repo and the two copies must stay identical.
- **What holds for one tree holds for all.** Any change to an invariant below must be propagated to *both* trees; the human commits the change, and the AI contributor treats cross-tree propagation as a standing check on every change to either side.
- **"Narrower" is the validation point.** A construct in either tree is correct only if it is a strict, narrowing application of these invariants — never a widening exception.

---

## The invariants

**I1 — Entity is the primitive.** Every actor *and* every resource is an entity with its own tree (four node-types — Entity → Persona → Identity → Account). There is no special "resource" type. An **Entity is anything that can hold or be held to a contract** (a distinct locus of accountability); an **Identity** is the smallest *authority*-bearing unit, an **Entity** the smallest *accountability*-bearing unit; decompose only to the atomic component (smallest unit with its own identity + entitlements). An **agent** is not a separate primitive — it is an application-Entity holding a runtime self-authoring entitlement via a model-edge. *UETF:* the homogeneous entity graph. *Ref model:* every agent, workload, human, service, and target is an entity.

**I2 — Self-similarity (one rule at every scale).** The same authority rule applies at every tier and across every boundary. A child grant can only be **narrower** than its parent grant; widening is impossible by construction.

**I3 — Open boundary.** No entity is a closed system; edge connectivity has no natural end (up the governance/charter chain, out to peers, down to dependents). A boundary is a *scope of attention*, not closure. Eliding unseen edges is safe because they obey the same rule ("…" = more of the same).

**I4 — Entitlement is an edge; ownership is holding governance personas.** Authority to act is an edge between two entity-trees (account-to-account / port-to-port). Ownership = one entity holding another's governance personas; it **connects** trees, it never **absorbs** them — the owned entity stays its own complete tree.

**I5 — Four governance personas (separation of powers).** *Optimisation* (the ends/purpose — where AI alignment lives; closes the world to the entity's scope), *Policy* (the permitted means — translates charter + inherited restrictions + purpose into "what may be done"; the legislature / 2nd-line compliance / moral compass; tightens within the floor, never loosens), *Control* (execution &amp; structure — mints grants and shapes the tree within Policy's rules), *Operational Integrity* (assurance — verifies fit and conduct, detects breach; a witness, not an oracle, bounded by requisite variety). Ends → permitted means → execution → assurance: four mutually-checking branches, all floored by the charter. Cross-persona use is **entity-mediated**; lateral persona↔persona edges are forbidden.

**I6 — Contracts are the universal edge algebra.** Every relationship is a contract: scoped, conditional, observable, and revocable, carrying attenuation as caveats. Not a one-shot token — a living governance relationship.

**I7 — Fractal attenuation.** Verify one edge up, narrow down; monotonic. Across entity boundaries the safe rule is **intersection**: what B may do on A's behalf = (B's own authority) ∩ (A's attenuation), never B's alone; this propagates downstream (strictly fewer permissions per hop) and defeats the confused deputy.

**I8 — The blast-radius rule.** The universal enforcement key is **(impact × certainty) → precedence → posture**. Impact tiers T0 Informational / T1 Operational / T2 Consequential / T3 Critical (computed, not declared; charter sets floors; owner may raise not lower; re-scored per invocation; action tier = MAX over the activated subgraph). Precedence is impact-first: ≥T2 → Pause & Escalate regardless of certainty; else hard → Terminate/Contain; else soft → Evaluate/Yield. This rule keys attenuation depth (hop-by-hop low / end-to-end high), enforcement locus (token-offline low / fabric-live + state-locked high), and Integrity posture (witness low / enforce-escalate high). *Ref model:* realised as the Decision Routing Gateway (Hard/Soft/High-impact).

**I9 — Full-depth revocation.** Two flavours on one chain: *dependency* revocation (an ancestor stops supplying / stops re-minting) and *override/jurisdictional* revocation (a charter-level authority terminates even where it never granted). Revocations carry **provenance** on the bitemporal lineage, or "override" becomes an unaudited backdoor.

**I10 — Charter is the outermost boundary of self-determination.** It bounds the recursion but does not terminate it (governance continues beyond it — open boundary). It is **amendable only by an external authority, never by the entity itself** — so the entity can adapt without self-capture.

**I11 — No orphans.** Every created entity has an owner vested at genesis. "Unowned" must **never** default to sovereign; self-sovereignty is reserved for intrinsically self-existent entities. A spawned agent with no owner is a bug, not a free agent.

**I12 — Genesis, provenance, and a bitemporal substrate.** Each entity has a root of trust (self- or other-attested) and a chain-of-title. On a bitemporal (valid-time + transaction-time) substrate: **authorise** = traverse-now, **validate** = traverse-vs-state-snapshot (state-locked), **govern** = constrain-traversal, **reconstruct/lineage** = replay-traversals.

---

## Scope note (carried from the red-team)

These invariants govern **objectives and authority** — who sets a mandate, who may change it, whether actions stay within it, and how authority narrows and is withdrawn. They make goal-hijack (an objective locus relocating outside its granted bound) **detectable**; they are **not** a solution to inner/deceptive alignment. Inferring intent from behaviour is the probabilistic (soft) axis and is least certain exactly where stakes are highest. Claimed as governance, not as solved alignment.
