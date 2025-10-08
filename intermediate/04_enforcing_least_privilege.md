# 04 — Enforcing Least‑Privilege (Design Patterns)

- **Design with Deny‑by‑Default**: start with no access, add narrowly.
- **Break up duties**: deployer vs. auditor vs. incident‑responder.
- **Use conditions**: time, network, device posture, tag‑based (ABAC).
- **Short sessions**: STS durations, PIM activations, JIT brokers.
- **Guardrails**: SCP (AWS), Azure Policy, GCP Org Policies.
- **Review cadence**: monthly usage review, quarterly cert & recert.

```mermaid
flowchart LR
    LP[Least‑Privilege Role] --> JIT[Just‑In‑Time Elevation]
    JIT --> Approve[Approval & MFA]
    Approve --> Session[Short‑Lived Session]
    Session --> Logs[Centralized Logs & Alerts]
    Logs --> Trim[Revoke Unused Permissions]
    Trim --> LP
```
