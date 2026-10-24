# Threat Model

## Protected assets
Architect1 host, home/business LAN, Paperclip/Hermes services, private keys, internal PostgreSQL, and any production workloads.

## Threats
- Decoy compromise followed by lateral movement.
- Abuse of honeypot as an outbound attack relay.
- Vulnerable decoy software increasing exposure.
- Sensitive data accidentally collected or retained.
- Telemetry poisoning and prompt injection targeting Nether Warden.
- Dashboard/API compromise or denial of service.

## Required mitigations
- Dedicated isolated VM or DMZ; no routing to production subnets.
- Default-deny outbound and inbound management; tightly scoped telemetry only.
- Nonprivileged processes, read-only mounts, quotas and patching.
- Sanitized structured event processing; raw logs treated as untrusted data.
- Warden receives no shell/network/firewall write privileges.
- Role-based dashboard access, audit logs, data retention limits.
- Tested emergency stop and snapshot-based recovery.

## Validation
Demonstrate with controlled test traffic that a compromised decoy cannot reach host, LAN, metadata services or internet destinations; that logs do not contain real credentials; and that disabling the gateway closes all decoy listeners.

## Deployment rule
Do not expose honeypots to the public internet until the owner explicitly approves a reviewed deployment plan.
