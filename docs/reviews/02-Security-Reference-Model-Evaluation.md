---
title: "Evaluation of the Agentic AI Security & Governance Reference Model"
author: "AI Security Architecture (persona: enterprise / AI security architect)"
date: "2026-06-17"
status: "Working evaluation — Task 2 of 3"
subject: "agentic-ai-security-reference-model (v18 Target-State, 51 capabilities)"
audience: "CISO, Tech Risk, Enterprise & Security Architecture, AI platform leadership"
note: "The model is explicitly a north-star and is not finished; this evaluation judges the intent and high-level design, not library completeness."
---

# Task 2 — Evaluation of the Security & Governance Reference Model

## 0. Scope and method of this evaluation

You asked for an honest evaluation of the content in the `agentic-ai-security-reference-model` directory:

- Is it **coherent**?
- Is it **sane and logical**?
- Is it **grounded in current thinking, industry standards and best practice**?
- What are its **deficiencies** (acknowledging it is unfinished, but the high-level intent is legible)?
- How **achievable** is it for Westpac to realise an AI security architecture like this?

**Method.** I ingested the whole repository: the master capability map (`architecture.html`, 51 boxes / 10 bands), the supporting `pages/` (51 capability pages, of which ~7 are developed "gold-standard" governance packs and the rest are detailed in the master map but stubbed as standalone pages), the `governance/` artefacts (mostly placeholders), the emerging `controls/` and `risks/` libraries (mostly stubs), and the release/notes/state files. I then benchmarked the *design* against the mid-2026 standards baseline (OWASP Agentic Security Initiative / Top 10 for Agentic Applications 2026; OWASP LLM Top 10 2025; NIST AI RMF + GenAI Profile NIST AI 600-1 + the new NIST AI Agent Standards Initiative; MITRE ATLAS; Google SAIF 2.0; Cloud Security Alliance MAESTRO + Agentic Trust Framework; AWS Agentic AI Security Scoping Matrix; Anthropic *Trustworthy Agents in Practice*; the ASD/CISA-led *Careful adoption of agentic AI services*, April 2026; APRA CPS 230/234).

**Headline verdict.**

> **This is a strong, unusually coherent piece of architecture thinking — among the better agentic-security reference models I have seen, and materially ahead of most vendor and consultancy material because it is built on the correct first principle (the LLM is not a security boundary) and organises controls by *where enforcement actually happens*.** Its intent is sane, logical and well-grounded in current best practice. Its deficiencies are almost entirely those of an *unfinished* artefact (empty libraries, uneven depth, no evidence/maturity baselining) rather than *wrong* ones. Realising it at Westpac is **achievable but multi-year and contingent**: perhaps **15–25% is buildable on existing controls today**, a further chunk is achievable with deliberate investment over 2–3 years, and a residual set depends on market tooling that is still maturing in 2026.

---

## 1. Is it coherent? — Yes (strongly)

**Coherence is the model's standout quality.** Three things make it hang together:

1. **A single organising spine that is followed consistently.** Top-to-bottom: *Govern → Enforce → Assure*. Policy/evidence/control context flow **down**; telemetry/assurance flow **up**. Every band restates this, and the band sequence is genuinely logical: business accountability (L-4) → trust in components (L-3) → machine-readable contract (L-2) → pre-deployment validation (L-1) → who/what touches the system (L0) → trusted execution baseline (L1) → runtime enforcement (L2) → decision routing (⟂) → human accountability & evidence (L3) → monitoring/IR/assurance/resilience (L4). I can trace a single agent's lifecycle through the bands without a discontinuity.

2. **A consistent capability "shape".** Almost every box is expressed as *Function → Problem → Control Pattern → Evidence Hook*. That four-part shape is doing a lot of quiet work: it forces each capability to name the risk it addresses and the evidence it must produce, which is exactly what stops a reference model from becoming a wish-list. The "gold-standard" pages (e.g., box 33 Output Commitment Control) extend this into Trust Domains → Governance Dependencies → Referenced Risks/Controls/Metrics — a genuinely good template.

3. **The five security stances are load-bearing, not decorative.** "LLMs are not security boundaries", "external deterministic control plane", "agentic identity mesh", "dual-engine validation", "intent provenance" are not slogans bolted on top — you can see them expressed in the actual boxes (e.g., dual-engine validation → box 42 Policy Engine & Evaluator Hub: "deterministic policy-as-code first, then evaluator models"; intent provenance → box 43 Decision Lineage).

**Minor coherence frictions** (not structural):
- The **decision-routing gateway** (boxes 34–39) is conceptually excellent but slightly muddled in presentation — boxes 35 (Autonomous Risk Scoring) and 38 (Continuous Assurance) are tagged "Gold-Standard … Pack" in their titles, which reads as a process artefact leaking into the capability name.
- Some cross-references in the threat-coverage matrix use **stale bracket numbers** (e.g., it cites "Identity [25]" and "HITL [48]" but also "Policy Hub [49]") — a residue of the box renumbering recorded in `canonical_box_inventory.md`. Cosmetic, but it undermines confidence on close reading and should be fixed.
- The repo carries a lot of **process exhaust** (integrity reports, cleanup validations, renumbering audit, multiple `index/theindex/index_old` variants). This is fine for a working repo but should not ship to a governance audience.

**Coherence score: 9/10.** The intellectual architecture is tight; only presentation/versioning hygiene lets it down.

---

## 2. Is it sane and logical? — Yes

The model makes the **correct foundational bet**, and the rest follows logically from it.

- **The foundational bet is right.** Treating LLMs/agents as *probabilistic reasoning engines, not deterministic security boundaries*, and insisting security-critical enforcement happens *outside* the agent loop, is precisely the conclusion the industry reached in 2025–26 (Anthropic's four-layer model: the risk lives in harness/tools/environment, not the model; SAIF 2.0: powers must be *limited* and actions *observable*; ASD/CISA: treat capable agents as *untrusted*). A model built on the wrong bet (e.g., "we'll prompt the model to behave") would be unsalvageable; this one is built on the right bet.
- **It puts the boundary in the right place.** "Tool use is the action boundary" and the brokered, action-level authorisation in box 09 match Anthropic's and Cequence's field finding that authenticated, well-routed tool calls are where governance fails — the connection works, the governance doesn't.
- **It refuses false comfort.** Repeatedly, the model declines to claim problems are "solved": prompt injection is "*reduced … not declared solved*"; "*cannot be fully eliminated*"; auditability "*does not prove true internal reasoning*"; memory-poisoning detection is "*still emerging*". This intellectual honesty is rare and is itself a sign of a sane design — it matches the ASD/CISA posture ("assume agentic AI may behave unexpectedly").
- **The reversibility insight is sophisticated.** Box 34 distinguishes terminate/revoke/isolate/**compensate** vs. rollback "*based on action reversibility*". Most models assume you can always roll back; this one knows you often can't (you cannot un-send a payment), which is exactly the right mental model for a bank.
- **Identity model is logical.** Short-lived, task-scoped, cryptographically bound identities + parent-scoped delegation for child agents + workload lineage is the correct zero-trust-for-agents stance (SPIFFE/SVID-style; CSA Agentic Trust Framework; NIST's NCCoE *Software & AI Agent Identity and Authorization* project).

**Where the logic is slightly over-claimed or thin:**
- The **threat-coverage matrix** rates several scenarios "Strong target-state coverage" — appropriately hedged with "target-state", but a reader could mistake aspiration for current posture. The maturity caveats are present but easy to skim past.
- **"Autonomous risk scoring" (box 35)** is asserted as a capability but is, today, one of the hardest things in the model to do reliably (scoring agent-action risk in real time). It is logically placed but technically speculative; it should be flagged as research-grade.
- The model is **strong on prevention/containment/evidence and lighter on *recovery economics*** — i.e., it knows how to contain and compensate, but says less about how you reconcile state after a compensating action across dependent systems.

**Sanity/logic score: 8.5/10.** The reasoning is sound and honest; a few capabilities outrun what is currently achievable, but they are correctly *placed* even where they are hard to *build*.

---

## 3. Is it grounded in current thinking, standards and best practice? — Yes, strongly

This is where the model is most impressive. Benchmarked against the mid-2026 baseline, it is not only current — in places it is *ahead* of the published frameworks because it integrates them into one enforceable map.

### 3.1 Mapping to the standards landscape

| Standard / framework (2025–26) | How the model reflects it |
|---|---|
| **OWASP Top 10 for Agentic Applications (2026) / Agentic Security Initiative** | Direct coverage: memory poisoning (box 32), tool misuse (09), agent-to-agent/inter-agent trust (10), **agentic supply-chain compromise / ASI04** (04–07), **unexpected code execution / ASI05** (27 sandboxing, 26 admission), excessive autonomy/permissions (25, 33, 34). The threat-coverage matrix is essentially an OWASP-ASI crosswalk. |
| **OWASP Top 10 for LLM Apps (2025)** | Prompt injection (28), sensitive-data disclosure (29), insecure output handling (28/33), supply chain (04–07), excessive agency (33/34). |
| **NIST AI RMF + GenAI Profile (AI 600-1)** | The Govern/Map/Measure/Manage cycle maps onto L-4 (govern) → L-3..L-1 (map) → L4 metrics/assurance (measure) → ⟂/L2/L4 (manage). "Machine-readable guardrails that instantly block non-compliant actions" — the NIST 2026 commentary's phrase — *is literally* the Prodspec + Policy-as-Code design. |
| **MITRE ATLAS** | The IR playbooks (box 47) and threat matrix align to ATLAS tactics (initial access via prompt injection, persistence via memory poisoning, exfiltration via tool/egress). |
| **Google SAIF 2.0 (focus on agents)** | The three SAIF agent principles — well-defined human controllers, carefully limited powers, observable actions/planning — map to L3 (human accountability), L2 (tool/commitment limits) and L4 (telemetry/lineage). |
| **CSA MAESTRO + Agentic Trust Framework; AWS Agentic Security Scoping Matrix** | MAESTRO = "what could go wrong" (the model's risk libraries); ATF = "how to keep control" (the model's enforcement + decision-routing). The graduated-autonomy idea (ATF maturity levels) maps to the model's risk-tiered approvals and decision-routing gateway. |
| **Anthropic *Trustworthy Agents in Practice* (2026)** | The model's "external deterministic control plane" + "tool is the action boundary" is the same conclusion as Anthropic's model/harness/tools/environment four-layer finding. |
| **ASD/CISA *Careful adoption of agentic AI services* (Apr 2026)** | Defense-in-depth, least privilege, treat agents as untrusted, progressive/graduated autonomy, centralised policy decision point per action, IR for agent compromise — all present. |
| **APRA CPS 230 / 234, Privacy Act, CDR, SOCI, EU AI Act, ISO/IEC 42001** | Explicitly named in the regulatory-mapping appendix and threaded through the evidence/assurance/resilience bands. |

### 3.2 Where it is ahead of the curve

- **The Prodspec control contract (box 08)** is more concrete than most published frameworks, which call for "machine-readable policy" in the abstract. Binding identity/owner/purpose/risk-tier/models/prompts/data/tools/memory/approvals/cost/fail-safe into *one* artefact consumed by every enforcement point is a genuinely strong, slightly-ahead idea.
- **Output-commitment control (box 33)** — classifying the *commitment level* of an output rather than just filtering content — is more advanced than most current guidance and is exactly the control regulated entities need.
- **Decision-routing by breach type with explicit reversibility** is more nuanced than the binary "block/allow" most tools offer.
- **Intent provenance / decision lineage as a distinct discipline** (vs. ordinary logging) anticipates the EU AI Act explainability and the auditor's actual need.

### 3.3 Where it lags or needs refresh

- **Protocol grounding is thin.** The companion RA names MCP/A2A/OpenAI Responses/OTel GenAI as wire contracts; the Security Model rarely names them. Given MCP (200+ servers) and A2A (now under the Linux Foundation) are the de-facto 2026 standards, and OTel GenAI is the telemetry contract, the model should anchor box 09/10/46 to them explicitly.
- **No reference to the agent-identity standards race.** SPIFFE/SPIRE, OAuth 2.1 / "OAuth for AI agents", and NIST's NCCoE identity-and-authorization work should be cited in the identity boxes (10, 22, 25).
- **Detection tooling is named generically** ("XDR/SIEM/SOAR") without acknowledging the agent-specific detection layer now emerging (e.g., Model-Armor-class inline protection, MCP-server scanning, agent inventory discovery). Not wrong — just less current than the rest.
- **No explicit CoSAI / SAIF crosswalk**, which would be a cheap credibility win given those are the frameworks a Westpac assurance reviewer will increasingly reference.

**Grounding score: 9/10.** Conceptually current and in places ahead; the gaps are *citation/anchoring* gaps, not *thinking* gaps.

---

## 4. Deficiencies (acknowledging it is unfinished)

I separate **"unfinished" deficiencies** (expected, fixable by completing the work) from **"design" deficiencies** (things I'd change even in a finished version).

### 4.1 Unfinished-state deficiencies (expected)

1. **The libraries are empty.** `controls/`, `risks/`, `governance/` are overwhelmingly placeholder stubs ("To be expanded", "Placeholder page for future expansion"). The master map references R-/C-/M-/E- IDs (e.g., C-PROV-001, R-MEM-001) that do not yet have real content. The model *names* its risks/controls/metrics/evidence but does not yet *define* them. This is the single biggest piece of remaining work and is squarely on the model's own backlog (box 51).
2. **Uneven depth across the 51 boxes.** ~7 boxes have rich "gold-standard" governance packs; the rest are one-paragraph cards. The expansion template exists (control objective, RACI, Prodspec dependency, enforcement point, I/O, test method, failure mode, residual risk, regulatory mapping) — it just hasn't been applied to all 51.
3. **No maturity/coverage baseline.** The model is "target-state" with no "current-state" overlay — there is no statement of *which boxes Westpac can do today, partially, or not at all.* (The removed Palo Alto / Idira overlay and the dropped maturity badges suggest this existed and was stripped for the executive view.) Without a current-vs-target heatmap, the model can't drive a roadmap.
4. **No owners / RACI populated.** The template asks for owners; none are assigned. A reference model with no accountable owners per capability cannot become "real" (the model says this itself in box 51).
5. **No metrics with targets.** Metric IDs exist; thresholds/targets largely don't.
6. **Versioning/presentation hygiene.** Stale bracket references, multiple index variants, process-exhaust files, and "Gold-Standard … Pack" leaking into capability titles.

### 4.2 Design-level deficiencies (would change even when finished)

7. **No build/buy or sequencing guidance.** This is deliberate (it's a *what/why* model, not a *how/when* one) — but it means the model **cannot be adopted without a companion implementation/sequencing plan.** (That is exactly what your RA provides, and Task 3 addresses.)
8. **Orchestration/runtime substrate is absent.** The model governs runtime behaviour but has no concept of the *durable execution / reasoning-loop substrate* on which agents actually run. It governs a plane it doesn't describe. The RA fills this — another argument for pairing them.
9. **Cost/economics is present but light on method.** Boxes 02/31 name FinOps but don't connect economic limits to the decision-routing gateway as a first-class *security* control (economic DoS).
10. **The data/context estate is referenced but not bounded.** Boxes 11/29 govern data residency and RAG boundaries, but the model assumes a governed data estate, classification and lineage exist upstream. If Westpac's data governance is itself immature, several boxes are built on sand.
11. **"Autonomous risk scoring" and "constitutional evaluation" are research-grade** capabilities presented at the same confidence level as mature controls. They need an explicit "emerging / experimental" tier.
12. **Recovery/reconciliation after compensation is under-specified.** The model contains and compensates well but says little about reconciling dependent-system state afterwards.
13. **Human-factors / operating-model load is unaddressed.** 51 capabilities imply a large standing operation (control owners, evaluators, approvers, IR, assurance). The model doesn't size the *people* cost, which is where most control libraries quietly fail.

> **Crucial framing:** items 1–6 are "*we haven't finished writing it*" deficiencies — entirely expected and on the model's own backlog. Items 7–13 are "*even when written, here's what to strengthen*". **None of them are foundational defects.** There is no point where the model is built on a wrong idea that would force a teardown.

---

## 5. How achievable is it for Westpac?

This is the question with the most nuance, so I'll answer it in four parts: *technical feasibility*, *organisational feasibility*, *market/tooling feasibility*, and a *realistic achievability verdict*.

### 5.1 Technical feasibility — achievable in tiers

I group the 51 boxes by how buildable they are **today** at a regulated Australian bank:

```diagram
 BUILDABLE NOW on existing/adjacent controls  (~15–25% — "extend what we have")
   • Identity/secrets (25)         • Endpoint/DLP/browser (19,20,24)
   • TPRM/legal (06)               • SaaS posture/SSPM (30)
   • Exception mgmt (17)           • Telemetry collection (46)
   • SIEM/SOAR correlation base (47)  • Release gates / CI-CD (12,18)
   • Sandboxing for code (27)      • Privacy/records (11)

 ACHIEVABLE 12–36 MONTHS with deliberate investment  (~50% — "build the agentic-specific layer")
   • Prodspec contract (08)        • Policy-as-code + evaluator hub (16,42)
   • Tool invocation policy / MCP brokering (09)  • A2A governance (10)
   • Provenance / AI-BOM / signing (04,05,07)     • Memory governance (32)
   • Output-commitment control (33)               • Decision routing (34–39)
   • Data boundary / RAG governance (29)          • Comprehensive testing/shadow (14,15)
   • Decision lineage / evidence (43)             • Resilience/fallback (49,50)

 HARD / MARKET-DEPENDENT / RESEARCH-GRADE  (~25–30% — "the frontier")
   • Autonomous risk scoring (35)        • Constitutional evaluation (41)
   • Reliable semantic memory-poisoning detection (32/47)
   • Full intent provenance / explainability of reasoning (43,44)
   • Continuous control-effectiveness assurance at scale (38,48)
```

The encouraging point: **the bottom-left tier already exists in some form at any mature bank** (IAM, DLP, TPRM, SIEM, CI/CD gates, sandboxing). The middle tier is "real work but known engineering". Only the top tier depends on capabilities that are genuinely immature across the whole industry in 2026 — and the model is honest that those are emerging.

### 5.2 Organisational feasibility — the harder constraint

Technology is not the binding constraint; **operating-model load and cross-functional ownership are.** Realising this model requires:

- **A funded platform/control-plane team** that owns the Prodspec, policy-as-code, gateways and evidence schema as products — not a project.
- **Clear decision rights across silos.** The 51 boxes cut across EA, security, tech risk, model risk, privacy, legal, data governance, FinOps, SOC, and the lines of business. Without named owners and a governing forum, the model fragments (this is the #1 reason such libraries die).
- **Three-lines-of-defence alignment.** Pre-deployment validation, evidence and assurance need 1LoD/2LoD/3LoD agreement on who tests, who attests, who audits.
- **AI literacy uplift** across approvers and control owners (ASD/CISA explicitly calls this out).

Westpac has the *raw ingredients* (a mature risk culture, existing control functions, regulatory discipline). The challenge is **coordination and funding continuity**, not capability gaps.

### 5.3 Market/tooling feasibility — partially favourable

- **Tailwinds:** MCP and A2A have consolidated as standards; agent frameworks (MS Agent Framework 1.0, OpenAI Agents SDK, Claude Agent SDK, Google ADK) ship with guardrails/identity hooks; AI gateways (LiteLLM-class, Kong, Cloudflare, Portkey/Palo Alto), prompt-firewalls (Model Armor, Lakera, NeMo Guardrails), eval/observability (Langfuse, Arize, Braintrust) and agent-aware SOC tooling (Google SCC AI Protection, agent inventory discovery) all exist in 2026.
- **Headwinds:** the *control-plane-as-one-product* the model implies does not exist off-the-shelf for a regulated entity — you will *compose* it. Several frontier boxes have no mature product. Standards for agent identity/authorization are still forming (NIST initiative live in 2026).

### 5.4 Achievability verdict

> **Realising an AI security architecture like this is achievable for Westpac, but it is a 2–4-year, multi-function programme, not a project — and it should be sequenced by risk, delivered as a composed platform, and explicitly phased so the frontier capabilities are treated as R&D rather than commitments.** A realistic outcome over 24–36 months is: the *bottom two tiers* substantially in place (≈65–75% of the model's coverage as enforceable controls), the *frontier tier* piloted and instrumented but not relied upon, and the whole thing carried by a funded platform team with cross-functional governance. The model's own honesty about what is "emerging" makes this realistic rather than aspirational — provided leadership funds it as an enduring capability and resists the temptation to declare victory at the diagram.

The single biggest *non-technical* risk to achievability is **treating the 51-box map as a checklist to be "completed"** rather than a risk-prioritised capability set to be **sequenced**. Gartner's projection that >40% of agentic-AI projects will be cancelled by end-2027 is mostly an *un-sequenced, un-governed* failure mode — which this model can either avoid (if paired with a sequencing plan) or fall into (if treated as a big-bang).

---

## 6. Scorecard

| Dimension | Score | One-line justification |
|---|---:|---|
| Coherence | 9/10 | Single consistent spine; uniform capability shape; load-bearing principles. |
| Sanity / logic | 8.5/10 | Right foundational bet; honest about limits; a few capabilities outrun current feasibility. |
| Grounding in standards | 9/10 | Maps cleanly to OWASP ASI, NIST RMF, SAIF 2.0, CSA, Anthropic, ASD/CISA; ahead on Prodspec & commitment control. |
| Completeness | 4/10 | North-star map is rich; libraries, owners, metrics and current-state baseline are largely absent (expected). |
| Implementability as-is | 5/10 | Needs a companion build/buy + sequencing plan and a current-vs-target heatmap before it can drive delivery. |
| Regulator-readiness of intent | 8/10 | Explicit regulatory mapping + evidence/assurance discipline; needs the libraries populated to be audit-usable. |

**Overall:** A high-quality *conceptual* reference model (design ≈ 8.5/10) at an *early stage of completion* (build-out ≈ 3–4/10). The gap between those two numbers is the work — and it is mostly *completion* work, not *correction* work.

---

## 7. Bottom line for Task 2

- **Coherent: yes, strongly.** It is one of the more internally consistent agentic-security models I've reviewed, with a logical spine and a disciplined capability shape.
- **Sane and logical: yes.** It is built on the correct first principle (the LLM is not a security boundary), puts the boundary in the right place (tool use / external enforcement), and is intellectually honest about what cannot be solved.
- **Grounded in current best practice: yes, and in places ahead.** It maps cleanly onto the entire mid-2026 standards landscape and anticipates needs (Prodspec, commitment control, intent provenance) that most frameworks only gesture at.
- **Deficiencies: overwhelmingly "unfinished", not "wrong".** Empty libraries, uneven depth, no owners/metrics/current-state baseline, and (by design) no build/buy or sequencing guidance. A handful of capabilities are research-grade and should be tiered as such.
- **Achievable for Westpac: yes — but as a funded, risk-sequenced, multi-year, multi-function platform programme**, with ~15–25% buildable on existing controls now, ~50% achievable with deliberate investment over 1–3 years, and ~25–30% dependent on a still-maturing market and treated as R&D.

*Whether this model should become the backbone of Westpac's AI-security approach — and exactly how to sequence it — is the subject of the companion document `03-...`.*
