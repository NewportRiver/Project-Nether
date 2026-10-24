# Rabbit Hole — Adaptive API Deception (Design Proposal)

Status: proposed; not deployed.
Owner: Newport River Company / Project Nether.

## Goal
Create a trail of synthetic API references that draws unauthorized reconnaissance deeper into an isolated, controlled simulation while gathering defensible threat telemetry. Never intrude into, exploit, or modify a visitor's system.

## Architecture
1. **Breadcrumb Generator:** embeds clearly synthetic, non-sensitive endpoint references in decoy responses, robots.txt, error pages, and simulated documentation.
2. **API Mirage:** responds to suspicious probes with fake schemas, fake config and nonfunctional tokens. Never expose real credentials, production hostnames or internal topology.
3. **Rabbit Hole Router:** session-scoped state machine that progresses through prebuilt decoy layers, with rate limits and a maximum depth. No open redirects to third parties.
4. **Watchers:** collect request method, path, timestamp, sensor, source IP, user agent, safe header subset, event ID and correlation ID; redact authorization/cookie values.
5. **Warden:** summarize behavior from untrusted telemetry; correlate indicators and recommend human-reviewed mitigations. No shell, network pivot or firewall write access.
6. **Evidence Vault:** append-only event records, audit access, retention and export with sensitive-field scrubbing.

## Example fictional trail
```text
GET /api/v1/config        -> synthetic service index
GET /api/v1/internal      -> fictional API schema
GET /api/v2/admin         -> simulated permission response
GET /api/v2/backup-index  -> fabricated filenames only
```
All returned artifacts are inert, generated for the decoy, and contain no executable attack payloads.

## Safety boundaries
- Decoys live in a dedicated VM/DMZ with no route to production or private networks.
- Deny outbound network traffic by default, except explicit collector channel.
- No retaliatory scanning, exploit delivery, browser fingerprint scripts, malware or unauthorized access to remote systems.
- No unbounded content generation; deterministic templates first.
- Prevent reflection attacks, SSRF, prompt injection, and credential collection.
- Rate limit, cap session duration/depth, provide emergency shutdown.
- Use reserved example IPs in screenshots and test fixtures.

## Proposed milestones
- NET-011: Define breadcrumb templates and fake API schemas.
- NET-012: Build stateful Rabbit Hole Router with depth limits.
- NET-013: Implement telemetry, correlation and privacy scrubbing.
- NET-014: Add Warden classification and evidence-linked summaries.
- NET-015: Build tests for isolation, SSRF, egress, abuse and shutdown.
- NET-016: Add terminal dashboard Rabbit Hole depth view.

## Acceptance
- Lab-only default.
- Every breadcrumb resolves only to controlled decoy resources.
- All observed events carry session and evidence IDs.
- All telemetry is treated as untrusted.
- No outbound connection initiated toward the visitor.
- Demonstrated network isolation and manual deployment approval.
