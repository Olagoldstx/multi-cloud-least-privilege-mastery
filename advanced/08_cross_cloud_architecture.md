# 08 — Cross‑Cloud Identity & JIT Privilege

**Pattern**
- Central IdP (Okta/Entra) → SAML/OIDC federation to AWS/Azure/GCP.
- No standing admins; use **Privileged Access** systems for elevation.
- Central SIEM/SOAR monitors privilege creation & usage.

```mermaid
sequenceDiagram
    participant User
    participant IdP
    participant Broker as JIT Broker
    participant AWS
    participant Azure
    participant GCP

    User->>IdP: MFA + Request privilege
    IdP->>Broker: Token + context (device, risk)
    Broker->>AWS: Issue short STS creds
    Broker->>Azure: Activate PIM role (timed)
    Broker->>GCP: Bind temp role to SA session
    AWS-->>Broker: Logs
    Azure-->>Broker: Logs
    GCP-->>Broker: Logs
    Broker-->>SIEM: Correlated events & alerts
```
