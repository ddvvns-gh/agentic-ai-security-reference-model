---
title: "Should Westpac pivot its AI security approach toward the Agentic AI Security & Governance Reference Model? — Recommendation, preconditions and sequencing"
author: "AI Security Architecture (persona: enterprise / AI security architect)"
date: "2026-06-17"
status: "Strategic recommendation — Task 3 of 3"
audience: "CISO, CTO/Chief Architect, Tech Risk & Model Risk, AI platform leadership, EA leadership"
companions:
  - "01-Reference-Architecture-vs-Security-Reference-Model.md"
  - "02-Security-Reference-Model-Evaluation.md"
---

# Task 3 — Should this become Westpac's AI security direction, and how?

## 0. The question, precisely

You asked four linked questions:

1. Should this model be the **rough outline of what you pivot the organisation's AI security approach toward**?
2. What would you need to **change or update** to take that route?
3. What would need to be **true** to adopt this as the right overarching AI security architecture?
4. Or would you **break it into component pieces and run at those** — and how would you **sequence** it?

My answer in one paragraph:

> **Yes — adopt it as the *organising framework* (the "north-star map" and shared language) for Westpac's agentic-AI security, but do *not* adopt it as a programme to "build all 51 boxes". The right move is to ratify the model as the reference taxonomy, pair it with your Agentic Control Plane RA as the build/run plane, and then decompose it into ~7 risk-prioritised component workstreams that you sequence by risk-reduction-per-dollar — not by diagram order.** The model is strong enough to be the backbone of your *thinking*; it is not, and was never meant to be, a delivery plan. The pivot is therefore "framework yes, big-bang no, component-sequenced delivery yes."

This document explains the *why*, the *preconditions* (what must be true), the *changes needed*, the *component breakdown*, and a *concrete sequencing*.

---

## 1. Should you pivot toward it? — Yes, as the framework; with three caveats

### 1.1 The case *for* making it the backbone

1. **It is built on the correct first principle** (the LLM is not a security boundary) and is grounded in the entire mid-2026 standards landscape (OWASP ASI, NIST AI RMF + GenAI Profile, SAIF 2.0, CSA MAESTRO/ATF, Anthropic, ASD/CISA, APRA CPS 230/234). Pivoting toward it is pivoting toward where the industry and the regulators are going — not toward a bet.
2. **It is the assurance/governance half you are currently missing.** Your existing AI-security artefacts (the Options Paper / Portkey, the Abstraction-vs-Native strategy, the ACP RA) are strong on the *gateway and control-plane build*, but — as your own reviews found — thin on supply-chain provenance, pre-deployment validation, decision routing, output-commitment, evidence/lineage, agentic SecOps and resilience. **This model is precisely those missing halves, already organised.**
3. **It gives the whole organisation one shared language.** Today "AI control plane" means different things in different documents (your Options-Paper review identified *three* meanings of "hybrid" and an overloaded "control plane"). A ratified 51-capability taxonomy ends that ambiguity: every paper, vendor pitch and audit finding can be mapped to a box.
4. **It is regulator-shaped.** The explicit CPS 230/234, Privacy Act, CDR, SOCI, EU-AI-Act, NIST, ISO 42001 mapping and the evidence-first discipline are exactly what 2LoD/3LoD and APRA will ask for. Adopting it pre-empts a lot of audit friction.
5. **It is honest.** A model that says "cannot be fully eliminated", "still emerging", "target-state" will survive scrutiny far better than one that over-claims.

### 1.2 The three caveats (why "framework yes", not "programme yes")

- **Caveat A — it is unfinished.** Libraries, owners, metrics and a current-state baseline are missing (Task 2 §4). You are adopting a *map*, then doing the survey.
- **Caveat B — it has no build/buy or sequencing.** It deliberately doesn't tell you how or when. You must supply that (this document + the RA).
- **Caveat C — adopting it as a 51-box checklist is the failure mode.** Big-bang control libraries collapse under their own operating-model weight. The pivot must be to *sequenced components*, not to "complete the model".

### 1.3 The recommendation

> **Ratify the Security Model as Westpac's reference taxonomy and assurance overlay for agentic AI; ratify the ACP RA as the build/run plane; join them at the Prodspec and the four protocols; and deliver against them through ~7 risk-sequenced component workstreams.** Treat the model as a *living standard you govern*, not a *project you finish*.

---

## 2. What would need to be *true* to adopt it (preconditions)

These are the conditions that must hold for this to be the *right* overarching architecture rather than shelfware. I've grouped them and flagged Westpac's likely current state (best-guess from the ingested material — validate each).

| # | What must be true | Why it matters | Likely current state |
|---|---|---|---|
| P1 | **Executive mandate + a single accountable owner** for agentic-AI security (a named exec, not a committee) | A cross-silo model with no owner fragments | Probably **partial** — split across CISO/EA/Tech Risk |
| P2 | **Funded, enduring platform team** (control plane as a product, not a project) | Every box needs a long-lived owner | Likely **gap** — funded as initiatives |
| P3 | **Cross-functional decision rights** across EA, security, tech risk, model risk, privacy, legal, data gov, FinOps, SOC, LOBs, with a governing forum (DA/TAC-equivalent) | 51 boxes cut across all of these | **Partial** — forums exist, AI scope unclear |
| P4 | **A governed data/context estate** (classification, lineage, catalogue) for boxes 11/29 to consume | Several boxes assume this upstream | **Validate** — may itself be immature |
| P5 | **An agent registry + shadow-AI discovery** so "every agent is governed" is true, not assumed | The model presumes registration | Likely **gap** |
| P6 | **Three-lines-of-defence agreement** on who tests/attests/audits agentic controls | Evidence/assurance bands need this | **Partial** |
| P7 | **A decision on the control-plane build/buy posture** (own-the-centre vs vendor-hosted) consistent with the sovereignty principle | Your Options-Paper review flagged the Palo Alto SCM tension | **Open / contested** |
| P8 | **Acceptance that frontier boxes (35, 41, full intent-provenance) are R&D**, not commitments | Prevents over-promising to regulators | **Needs stating** |
| P9 | **AI literacy uplift** for approvers and control owners | ASD/CISA explicitly require it | **In progress** |
| P10 | **Tolerance for a 2–4-year horizon with risk-sequenced delivery** | It is a programme of capability, not a quarter's work | **Leadership decision** |

> **The most important preconditions are P1, P2 and P3.** If you cannot secure an accountable exec owner, an enduring funded team, and cross-functional decision rights, then *do not* adopt the full model — adopt only the top 2–3 components (§4) and revisit. Everything else can be sequenced; these three are load-bearing.

---

## 3. What would need to change / be updated to take this route

### 3.1 Changes to the model itself (make it adoptable)

1. **Populate the libraries for the prioritised boxes only** (not all 51 at once) using the existing expansion template: control objective, RACI, Prodspec dependency, enforcement point, I/O, test method, failure mode, residual risk, regulatory mapping.
2. **Add a current-state-vs-target heatmap.** Overlay each box with *Have / Partial / Gap* against existing Westpac controls. (The stripped Palo Alto / Idira / maturity overlay suggests this once existed — bring back a *vendor-neutral* version.) Without this, no roadmap is possible.
3. **Assign an accountable owner to every prioritised box.** A box with no owner is not a control.
4. **Tier the capabilities by feasibility** — *Standard / Engineering / Frontier(R&D)* — so leadership and regulators see what is committed vs. exploratory.
5. **Anchor the boxes to the four protocols** (MCP, A2A, OpenAI Responses, OTel GenAI) and the **identity standards** (SPIFFE/SPIRE, OAuth-for-agents, NIST NCCoE identity work) so the security model and the RA speak the same wire language.
6. **Fix the hygiene:** stale bracket references, "Gold-Standard Pack" leaking into capability names, multiple index variants, process-exhaust files. Ship a clean governance edition separate from the working repo.

### 3.2 Changes to the surrounding strategy/documents (make it consistent)

7. **Reconcile the document estate.** Re-scope the *Options Paper / Portkey* as RA **Layer 6 (model gateway)** + Security-Model **boxes 28/30/31** — *not* "the AI control plane" (per your own review). Map the *Abstraction-vs-Native* strategy onto the model's "external deterministic control plane" stance. One taxonomy, consistently applied.
8. **Resolve the sovereignty/build-buy posture (P7)** explicitly, because it determines how you build half the boxes. Decide where vendor-hosted management planes are acceptable and where a self-hostable shell is mandatory; record deviations with sign-off.
9. **Pair the two artefacts formally** (Task 1 §8): Security Model = assurance overlay; RA = build plane; joined at the Prodspec and protocols. Publish them together.

### 3.3 Changes to operating model (make it stick)

10. **Stand up the platform team and governing forum (P1–P3).**
11. **Define the 3LoD operating rhythm** for agentic controls (who validates pre-deployment, who attests, who audits, how often).
12. **Instrument from day one** — telemetry (box 46) and evidence schema (box 43) are foundational, not late; everything else produces evidence into them.

---

## 4. Component decomposition — break it into pieces and run at those

**Yes, decompose it.** A 51-box big-bang is the failure mode. I would collapse the 51 boxes into **seven coherent component workstreams**, each independently fundable, independently valuable, and each owning a clear slice of the model. They are designed so that early components are *prerequisites/enablers* for later ones.

```diagram
 ╭─────────────────────────────────────────────────────────────────────╮
 │ C1 · IDENTITY & EXECUTION TRUST       boxes 25,26,27,22,24           │
 │      short-lived agent identity, secrets, admission, sandboxing      │
 ├─────────────────────────────────────────────────────────────────────┤
 │ C2 · POLICY CONTRACT & ENFORCEMENT    boxes 08,09,16,42,41           │
 │      Prodspec + policy-as-code + tool invocation + evaluator hub     │
 ├─────────────────────────────────────────────────────────────────────┤
 │ C3 · TELEMETRY, EVIDENCE & SECOPS     boxes 46,47,43,48              │
 │      structured telemetry, decision lineage, agentic threat det/IR   │
 ├─────────────────────────────────────────────────────────────────────┤
 │ C4 · SUPPLY-CHAIN & PROVENANCE        boxes 04,05,06,07             │
 │      model/data/tool provenance, signing, AI-BOM, TPRM              │
 ├─────────────────────────────────────────────────────────────────────┤
 │ C5 · RUNTIME DATA/TOOL/MEMORY/COST    boxes 28,29,30,31,32,33       │
 │      prompt+output inspection, RAG boundary, SaaS, FinOps, memory,   │
 │      output-commitment control                                      │
 ├─────────────────────────────────────────────────────────────────────┤
 │ C6 · SDLC VALIDATION & RELEASE        boxes 12,14,15,17,18,10       │
 │      testing regime, shadow eval, exception mgmt, release gate, A2A  │
 ├─────────────────────────────────────────────────────────────────────┤
 │ C7 · GOVERNANCE, ACCOUNTABILITY &     boxes 01,02,03,11,13,40,44,45, │
 │      RESILIENCE                            34–39,49,50,51            │
 │      workforce hub, exec GRC, HITL/dual-control, decision routing,   │
 │      explainability/appeal, resilience, assurance backlog           │
 ╰─────────────────────────────────────────────────────────────────────╯
```

Why these seven (and not the ten bands): the bands are a *reading order*; the components are a *delivery order*. Each component is a fundable product with one accountable owner, a clear protocol/standard anchor, and a measurable risk-reduction outcome. They also map cleanly onto your RA layers (C1→L3, C2→L1/L7, C3→L4, C5→L6, etc.), so the same teams build both planes.

### Component ↔ RA-layer ↔ standard anchor

| Component | RA layer(s) | Primary standard anchor | Headline risk reduced |
|---|---|---|---|
| C1 Identity & Execution Trust | L3, L1 | SPIFFE/SPIRE, OAuth-for-agents, NIST NCCoE identity | Identity sprawl, privilege abuse, rogue child agents |
| C2 Policy Contract & Enforcement | L1, L7 | Prodspec + OPA/Rego; MCP | Ungoverned tool use, excessive agency |
| C3 Telemetry, Evidence & SecOps | L4 | OTel GenAI; MITRE ATLAS | Blindness; no IR; no audit defence |
| C4 Supply-Chain & Provenance | (L0 foundation) | OWASP ASI04; G7 AI-SBOM; SLSA | Poisoned models/tools/MCP servers |
| C5 Runtime Data/Tool/Memory/Cost | L5, L6 | OWASP LLM Top 10; SAIF 2.0 | Data leakage, prompt injection, memory poisoning, economic DoS, unauthorised commitments |
| C6 SDLC Validation & Release | L1/L2 | NIST RMF Measure; ASD/CISA graduated autonomy | Unvalidated agents in prod |
| C7 Governance, Accountability & Resilience | L1, L4 | CPS 230; EU AI Act; ISO 42001 | Unaccountable decisions; outage; no recourse |

---

## 5. Sequencing — how I would run at them

The sequencing principle is **risk-reduction-per-dollar, with enablers first**. Three "spine" components (C1, C2, C3) must come first because everything else produces evidence into C3, enforces via C2, and authenticates via C1. Then you fan out by risk.

```diagram
 PHASE 0  (0–3 mo)   RATIFY & BASELINE
   • Ratify the model as the taxonomy; pair with RA; assign exec owner (P1)
   • Stand up platform team + governing forum (P2,P3)
   • Current-vs-target heatmap across all 51 boxes (3.1 #2)
   • Pick the first agents/use-cases to govern (highest-risk in-flight)

 PHASE 1  (3–9 mo)   THE SPINE  — C1 + C2(core) + C3(core)
   • C1: short-lived agent identity, secrets, admission, sandbox
   • C2: Prodspec v1 + policy-as-code + tool-invocation brokering (MCP)
   • C3: OTel GenAI telemetry + decision-lineage/evidence schema
   OUTCOME: every governed agent is identifiable, contract-bound, brokered,
            observable, and producing evidence.  (Maps to RA Phase 1.)

 PHASE 2  (9–18 mo)  CONTAINMENT & TRUST  — C5(core) + C4 + C3(SecOps)
   • C5: prompt/output inspection, RAG boundary, output-commitment control,
         FinOps runtime limits, memory governance
   • C4: provenance/signing/AI-BOM/TPRM for models, tools, MCP servers
   • C3: agentic threat detection + IR playbooks into the SOC; shadow-AI discovery
   OUTCOME: agents are contained, commitments are gated, supply chain is
            trusted, and adversarial behaviour is detectable.

 PHASE 3  (18–30 mo) VALIDATION & ACCOUNTABILITY  — C6 + C7(core)
   • C6: testing regime, shadow/simulation eval, release gate, A2A governance,
         exception management
   • C7: HITL/dual-control, decision-routing gateway, explainability/appeal,
         resilience/fallback (CPS 230 fail-state), exec GRC/workforce hub
   OUTCOME: nothing reaches prod unvalidated; high-impact actions are
            human-accountable; control plane has a risk-tiered fail-state.

 PHASE 4  (30 mo+)   FRONTIER & OPTIMISE  — research-tier boxes
   • Autonomous risk scoring (35), constitutional evaluation (41),
     semantic memory-poisoning detection, continuous control-effectiveness
   • Treated as R&D / piloted, instrumented, not relied upon until proven
```

### Why this order (the logic)

- **C1/C2/C3 first** because they are *enablers*: you cannot meaningfully do supply-chain trust, containment, validation or accountability for agents you can't identify, contract, broker or observe. This also aligns with your RA's Phase-1 (identity + gateway + OTel) — so you build *both planes with the same first move*.
- **C5 + C4 next** because, once observable, the highest *residual* risks are runtime (data leakage, injection, unauthorised commitment, cost runaway, memory poisoning) and supply-chain (poisoned components). This is where you get the biggest risk-reduction-per-dollar after the spine.
- **C6 + C7 third** because validation gates and accountability/resilience are essential but depend on the spine and containment existing first (you can't gate on tests you can't run, or route decisions you can't observe). C7's CPS 230 fail-state and exec GRC are where you *close the regulatory loop*.
- **Frontier last and ring-fenced** so you never commit to a regulator on a capability the whole industry is still inventing.

### Sequencing guardrails

- **Pull two things forward out of "natural" order:** *output-commitment control (box 33)* and *FinOps runtime limits (box 31)*. Both are in Phase 2 deliberately — they are unusually high-leverage *business* controls (unauthorised commitments; economic DoS) and cheap relative to their risk reduction. Don't let them drift to Phase 3+.
- **Instrument before you enforce.** Stand up telemetry/evidence (C3) in Phase 1 even though detection/IR matures in Phase 2 — you want the data from day one.
- **Govern a thin slice end-to-end before going wide.** Pick 1–3 real high-risk agents in Phase 0 and take them through *all* components at low maturity, rather than building one component to high maturity across all agents. End-to-end-thin beats deep-and-narrow for proving the model and for learning the operating-model cost.
- **Every phase must produce evidence and a heatmap update.** The model's own discipline ("evidence over assertion") applies to the programme itself.

---

## 6. Decision summary — the four questions answered

1. **Should this be the rough outline you pivot toward?**
   **Yes — as the *organising framework and assurance overlay*, paired with your RA as the build plane.** It is coherent, current, regulator-shaped, and it is the half you're missing. But adopt it as a *living standard you govern*, not a *project to complete*.

2. **What would you change/update?**
   Populate libraries (prioritised boxes only), add a current-vs-target heatmap, assign owners, tier capabilities by feasibility, anchor to the four protocols + identity standards, fix hygiene, reconcile the surrounding document estate (Options Paper/Portkey, Abstraction-vs-Native), resolve the sovereignty/build-buy posture, and stand up the platform team + governing forum (§3).

3. **What would need to be true to adopt it?**
   The ten preconditions in §2 — above all **P1 (exec owner)**, **P2 (funded enduring team)**, **P3 (cross-functional decision rights)**, plus **P4 (governed data estate)**, **P5 (agent registry/shadow-AI discovery)** and **P7 (resolved sovereignty posture)**. If P1–P3 can't be met, adopt only the top 2–3 components and revisit.

4. **Component pieces or whole? How sequenced?**
   **Decompose into seven components** (§4) and sequence **spine-first, then containment/trust, then validation/accountability, then frontier** (§5): C1+C2+C3 → C5+C4 → C6+C7 → frontier. Govern a thin end-to-end slice first; pull output-commitment and FinOps forward; instrument before enforcing; update the heatmap every phase.

---

## 7. Risks of the pivot, and how to manage them

| Risk | Likelihood | Mitigation |
|---|---|---|
| Treated as a 51-box checklist → operating-model collapse | High | Component decomposition + sequencing (§4–5); govern thin slices |
| No enduring funding → stalls after the spine | High | Fund as a product (P2); tie each phase to a regulatory/risk outcome |
| Over-promising frontier boxes to APRA | Medium | Feasibility tiering (§3.1 #4); ring-fence frontier as R&D (P8) |
| Document/taxonomy fragmentation continues | Medium | One ratified taxonomy; re-map Options Paper & strategies onto it (§3.2) |
| Data-estate immaturity undermines data boxes | Medium | Validate P4 early; if immature, sequence a data-governance dependency in |
| Sovereignty/build-buy left unresolved → rework | Medium | Resolve P7 before Phase 1 build decisions |
| Frontier capabilities never mature → trust erodes | Low–Med | Don't depend on them; layered defence means they're additive, not load-bearing |

---

## 8. The one-page recommendation

> **Pivot toward the model as Westpac's agentic-AI security *framework and assurance overlay*, paired with the Agentic Control Plane RA as the *build/run plane*, joined at the Prodspec and the four protocols. Do not run it as a 51-box programme. Ratify it, baseline current-vs-target, secure an accountable exec owner and a funded platform team, then deliver through seven risk-sequenced components — spine first (identity, policy contract, telemetry/evidence), then containment and supply-chain trust, then validation and accountability/resilience, with the frontier capabilities ring-fenced as R&D. Govern a thin, real, high-risk slice end-to-end before going wide, and make the programme itself live by the model's own rule: evidence over assertion.**

This is achievable for Westpac over 2–4 years as a funded, multi-function capability — and doing it this way is also the strongest available defence against the most common failure mode (the un-sequenced, un-governed agentic programme that gets cancelled). The model is good enough to be the backbone. The discipline is in *sequencing it*, not *completing it*.

*Companion analyses: `01-...` (RA vs. Security Model, with 12 recommended RA uplifts) and `02-...` (standalone evaluation of the Security Model).*
