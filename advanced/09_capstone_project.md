# 09 — Capstone: Multi‑Cloud Least‑Privilege Architecture

**Deliverables**
- **Design doc**: target state, trust boundaries, roles matrix.
- **IaC**: Terraform that provisions LP roles across clouds.
- **JIT**: Implement PIM/STS/workload identity with short durations.
- **Detection**: SIEM rules for privilege escalation and abuse.
- **Runbook**: quarterly access review + emergency break‑glass.

**Assessment**
- PR review checks policy granularity
- Automated tests validate deny‑by‑default behavior
