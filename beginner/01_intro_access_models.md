# 01 — Intro to Access Models

**Goal:** Understand access models and why **Least‑Privilege (LP)** reduces risk and blast radius.

```mermaid
graph TD
    A[Identity (User/App/Service)] --> B{Access Model}
    B -->|Open Access| C[High Risk • No Controls]
    B -->|Coarse RBAC| D[Medium Risk • Over-broad Roles]
    B -->|Least‑Privilege| E[Low Risk • Just‑Enough Access]
    E --> F[Smaller Blast Radius • Easier Audits • Compliance]
```

**Key ideas**
- Give every identity **only** the permissions it needs—**no more**.
- Prefer **temporary elevation** (JIT) over standing privileges.
- Split duties; separate production‑change privileges from audit/monitor.
- **Measure & trim**: observe usage, remove unused rights regularly.

**Read next →** [02 — IAM Fundamentals](02_iam_fundamentals.md)
