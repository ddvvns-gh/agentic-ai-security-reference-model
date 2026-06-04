# v18 Update Notes — AI Provenance & Supply Chain Assurance

This release implements BKL-005 and related hardening patterns while preserving the current site structure and existing page lineage.

## Index changes
- Updated title/version reference to v18.
- Renamed Box 04 from "Model, Dataset & Tool Registries" to "AI Provenance & Supply Chain Assurance".
- Added v18 Trust Chain:
  - Artefact Trust
  - Identity Trust
  - Execution Trust
  - Decision Trust
- Added three hardening principles:
  - Semantic Blast-Radius Isolation
  - State-Locked Validation
  - Memory Epoch Isolation
- Removed the Layer -4 Capability Pages link from top navigation where present.
- Added backlog references BKL-021, BKL-022 and BKL-023 where the backlog block exists.

## Capability page changes
- Box 04: Major expansion to full AI Provenance & Supply Chain Assurance.
- Box 10: Added Semantic Blast-Radius Isolation and structured agent payload boundary.
- Box 19: Added child-agent semantic containment.
- Box 22: Added Trust Chain integration and artefact-bound token scope.
- Box 25: Added Semantic Payload Inspection.
- Box 29: Added Memory Epoch Isolation and semantic memory sanitisation.
- Box 30: Added State-Locked Validation.
- Box 35: Added State-Locked Validation support for validation authority.
- Box 36: Added intent, state and semantic provenance.
- Box 40: Added memory hygiene monitoring.

## New risk references
- R-PROV-001 Untrusted Artefact Origin
- R-PROV-002 Supply Chain Dependency Corruption
- R-PROV-003 AI-Generated Artefact Trust Failure
- R-A2A-005 Semantic Payload Contamination
- R-RT-005 Unclassified Semantic Payload
- R-MEM-001 Persistent Memory Poisoning
- R-MEM-002 Stale Context Recall
- R-STATE-001 Validation Execution Race Condition
- R-EVID-005 State Provenance Loss
- R-EVID-006 Semantic Provenance Loss
- R-MON-004 Memory Hygiene Failure

## New control references
- C-PROV-001 Artefact Provenance Registration
- C-PROV-002 Cryptographic Artefact Attestation
- C-PROV-003 Dependency Relationship Mapping
- C-PROV-004 AI-Generated Artefact Verification
- C-A2A-007 Structured Agent Payload Boundary
- C-ID-007 Artefact-Bound Token Scope
- C-RT-006 Semantic Payload Classification
- C-MEM-005 Memory Epoch Isolation
- C-MEM-006 Semantic Memory Sanitisation
- C-DEC-009 State-Locked Validation
- C-EVID-007 State Provenance Capture
- C-EVID-008 Semantic Provenance Capture
- C-MON-005 Memory Hygiene Monitoring

## New metric references
- M-PROV-001 Provenance Coverage
- M-PROV-002 Attestation Coverage
- M-PROV-003 Untrusted Dependency Detections
- M-A2A-006 Semantic Payload Validation Coverage
- M-ID-006 Artefact-Bound Token Coverage
- M-RT-005 Payload Classification Coverage
- M-MEM-004 Memory TTL Compliance
- M-MEM-005 Memory Poisoning Detection Rate
- M-MEM-006 Stale Memory Reuse
- M-DEC-005 State-Lock Validation Coverage
- M-EVID-006 State Provenance Completeness
- M-EVID-007 Semantic Provenance Completeness
- M-MON-005 Memory Epoch Violations
- M-MON-006 Memory Poisoning Incidents

## Review note
This release intentionally adds references to risks, controls, metrics and evidence before creating the central library pages. That preserves the lineage from capability pages into the future repositories without requiring the full backlog remediation immediately.
