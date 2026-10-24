# PROJECT NETHER

**Network Entrapment, Threat Hunting & Electronic Reconnaissance**

A defensive, open-source deception and threat-observation research platform from Newport River Company.

> Every unauthorized connection opens another door into The Nether.

## Mission
Observe internet reconnaissance safely using isolated decoy services, normalize telemetry, and provide human-reviewed threat intelligence. Never retaliate or permit decoys to reach production networks.

## Components
- **Portal:** OpenCanary for low-interaction decoys; optional Cowrie for SSH/Telnet interaction.
- **Gateway:** Dedicated firewall/DMZ or isolated VM network with deny-by-default egress.
- **Collector:** Structured events into PostgreSQL; secret scrubbing and retention controls.
- **Nether Warden:** Local model classifies sessions, summarizes patterns, and recommends (never directly applies) defensive actions.
- **Observatory:** Read-only dashboard with timeline, service map, indicators, alerting and system health.

## Non-goals
No counterattacks, malware execution outside hardened sandboxes, credential harvesting of real users, deceptive public websites, uncontrolled outbound connections, or exposing the Architect1 host management plane.

## MVP success criteria
- Decoys run in isolated environment without routes to production subnets.
- Test scanner events appear in dashboard within 10 seconds.
- Source IP, timestamp, service, and session correlation are recorded accurately.
- Warden produces cited summaries referencing original event IDs.
- Outbound traffic is blocked except explicitly allowlisted updates/telemetry.
- Shutdown switch disables public listeners and preserves evidence.

See [Development Plan](docs/DEVELOPMENT_PLAN.md) and [Threat Model](docs/THREAT_MODEL.md).

## Status
Design only. No honeypots deployed.