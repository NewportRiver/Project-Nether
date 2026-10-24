# NETHER Development Plan v0.1
Date: 2026-10-24
Owner: Newport River Company
Stage: Proposal — implementation requires approval and security review.

## Phase 0 — Discovery and threat modeling (week 1)
- Inventory host interfaces, reverse proxy, existing listeners and firewall policy.
- Choose isolated VM/DMZ and define explicit permitted traffic paths.
- Establish data minimization, retention (default 30 days), access control and incident response.
- Document assets, trust boundaries and rollback procedure.
**Gate:** Security review approves network diagram and no production lateral paths.

## Phase 1 — Lab-only portal (week 2)
- Deploy OpenCanary in a dedicated VM/container within an isolated virtual network.
- Start with simulated SSH, FTP and HTTP; avoid conflicting real services.
- Generate controlled local test traffic and validate logs and uptime.
- Deny outbound connections by default; prohibit access to host, LAN and RFC1918 destinations.
**Gate:** Isolation tests pass, no external exposure.

## Phase 2 — Telemetry and dashboard (weeks 3–4)
- Normalize events into versioned schema: event_id, UTC timestamp, sensor_id, service, src_ip, dst_port, event_type, session_id, raw_reference.
- Mask secrets and limit personal data; implement configurable retention.
- Add collector with queue, PostgreSQL storage, read-only API and audit trail.
- Build Observatory timeline, service heatmap, alert filters and emergency stop.
**Gate:** 95% of controlled test events ingested in 10 seconds; no lost events in restart test.

## Phase 3 — Nether Warden (weeks 5–6)
- Build offline log analysis with local LLM or deterministic rules fallback.
- Classify common scanner activity, summarize sessions, correlate repeated indicators.
- Cite original event IDs in each conclusion and provide confidence estimates.
- Require human approval for any proposed defensive changes.
**Gate:** Warden cannot modify firewall, run shell commands, or contact attacker endpoints.

## Phase 4 — Extended decoys (weeks 7–8)
- Evaluate Cowrie in a separately hardened and restricted VM.
- Implement synthetic filesystem and fake non-sensitive credentials only.
- Validate rate limiting, resource quotas, and egress restrictions.
**Gate:** Red-team isolation and failure-mode tests pass.

## Phase 5 — Controlled exposure (after review)
- Consider dedicated public IP or carefully scoped NAT rules for decoy services.
- Document legal/privacy posture, ISP terms and operational contacts.
- Monitor continuously and maintain a one-action kill switch.
**Gate:** Explicit owner authorization, security approval and rollback test.

## Engineering backlog
1. NET-001: Threat model and network boundaries.
2. NET-002: VM/DMZ architecture and firewall policy.
3. NET-003: Lab OpenCanary proof of concept.
4. NET-004: Telemetry event schema and collector.
5. NET-005: PostgreSQL retention and audit controls.
6. NET-006: Observatory dashboard.
7. NET-007: Warden classification and evidence links.
8. NET-008: Cowrie isolated evaluation.
9. NET-009: Isolation, resilience and security test suite.
10. NET-010: Deployment runbook, kill switch and release gate.

## Release principles
- Default private/lab-only; never expose automatically.
- No production routes or shared privileged credentials.
- Minimal collection, controlled retention, documented access.
- Human-in-the-loop changes; no offensive retaliation.
