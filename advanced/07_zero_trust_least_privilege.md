```mermaid 
flowchart TD
    A[Access Request] --> B{<b>Continuous Verification</b><br>Is the identity & device trusted?}
    
    B --&gt;|No| C[<b>Access Denied</b><br>Request Blocked & Logged]
    B --&gt;|Yes| D{<b>Policy Check</b><br>Does the user have the<br>required permissions?}
    
    D --&gt;|No| C
    D --&gt;|Yes| E[<b>Apply Least-Privilege</b><br>Grant TEMPORARY,<br>MINIMAL access]
    
    E --> F{<b>Continuous Monitoring</b><br>Behavior & Context changed?}
    
    F --&gt;|Yes - Risk Detected| G[<b>Re-evaluate Trust</b><br>Revoke/Reduce Access]
    F --&gt;|No| H[<b>Access Allowed</b><br>For session duration]
    
    G --> C

    style A fill:#f9f,stroke:#333,stroke-width:2px,color:#000
    style C fill:#f96,stroke:#333,stroke-width:2px,color:#000
    style H fill:#9f9,stroke:#333,stroke-width:2px,color:#000
```
      

# 07 — Zero‑Trust + Least‑Privilege

- **Never trust, always verify**: identity, device, posture, context.
- **Brokered access**: IdP + JIT broker + short‑lived creds.
- **Continuous evaluation**: revoke if posture/drift changes.
- **Segmentation**: network + identity + data zones.
- **Data‑aware**: labels/classification drive ABAC conditions.
