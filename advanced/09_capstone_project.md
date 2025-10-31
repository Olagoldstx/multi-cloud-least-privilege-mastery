# 09 — Capstone: Multi‑Cloud Least‑Privilege Architecture


flowchart TD
    subgraph A [Central Identity & Policy Governance]
        direction TB
        A1[Human & Non-Human Identity] --> A2(Central Identity Provider<br>e.g., Entra ID, Okta)
        A3[Least-Privilege Policy Definition] --> A4(Central Policy Engine<br>e.g., CIEM, CSPM)
        A2 --> A5{Policy Decision Point}
        A4 --> A5
    end
```mermaid 
    subgraph B [Multi-Cloud Environment]
        B1[AWS Account]
        B2[Azure Tenant]
        B3[GCP Project]
    end

    A5 -- “Policy & Identity Context” --> B

    subgraph C [Access Request & Enforcement]
        C1[Access Request<br>e.g., “Start VM in Azure”] --> C2{Policy Decision Point<br>Evaluates Request}
        C2 -- “Granted?<br>Yes + Just-In-Time?” --> C3[Enforce Time-Bound Access]
        C2 -- “Denied?” --> C4[Access Denied]
        C3 --> C5[Policy Enforcement Point<br>e.g., Azure RBAC, AWS IAM]
    end
```

    C5 --> B2

    subgraph D [Continuous Monitoring & Optimization]
        B -- “Logs & Usage Data” --> D1(Cloud Monitoring Tools)
        D1 --> D2[Privilege Creep Analysis]
        D2 --> D3[Automated Policy Recommendations]
        D3 --> A3
    end

    %% Styling for clarity
    classDef governance fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef cloud fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef enforcement fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px
    classDef monitoring fill:#fff3e0,stroke:#e65100,stroke-width:2px
    
    class A,A1,A2,A3,A4,A5 governance
    class B,B1,B2,B3 cloud
    class C,C1,C2,C3,C4,C5 enforcement
    class D,D1,D2,D3 monitoring
**Deliverables**
- **Design doc**: target state, trust boundaries, roles matrix.
- **IaC**: Terraform that provisions LP roles across clouds.
- **JIT**: Implement PIM/STS/workload identity with short durations.
- **Detection**: SIEM rules for privilege escalation and abuse.
- **Runbook**: quarterly access review + emergency break‑glass.

**Assessment**
- PR review checks policy granularity
- Automated tests validate deny‑by‑default behavior
