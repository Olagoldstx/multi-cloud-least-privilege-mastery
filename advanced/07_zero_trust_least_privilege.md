```mermaid 
  flowchart TD
    A[Access Request] --> B{"Continuous Verification<br>Is the identity & device trusted?"}
    
    B -->|No| C[Access Denied<br>Request Blocked & Logged]
    B -->|Yes| D{"Policy Check<br>Does the user have the<br>required permissions?"}
    
    D -->|No| C
    D -->|Yes| E[Apply Least-Privilege<br>Grant TEMPORARY,<br>MINIMAL access]
    
    E --> F{"Continuous Monitoring<br>Behavior & Context changed?"}
    
    F -->|Yes - Risk Detected| G[Re-evaluate Trust<br>Revoke/Reduce Access]
    F -->|No| H[Access Allowed<br>For session duration]
    
    G --> C

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style C fill:#f96,stroke:#333,stroke-width:2px
    style H fill:#9f9,stroke:#333,stroke-width:2px
```

# 07 — Zero‑Trust + Least‑Privilege

- **Never trust, always verify**: identity, device, posture, context.
- **Brokered access**: IdP + JIT broker + short‑lived creds.
- **Continuous evaluation**: revoke if posture/drift changes.
- **Segmentation**: network + identity + data zones.
- **Data‑aware**: labels/classification drive ABAC conditions.
