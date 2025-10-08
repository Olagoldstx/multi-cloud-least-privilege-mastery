# 🌐 Multi-Cloud Security Architect: Least‑Privilege Access (Living Course)

This repo is a **living directory** for a hands‑on course that makes **Least‑Privilege** the backbone of multi‑cloud security (AWS, Azure, GCP). Start at Beginner, climb to Advanced, then ship a capstone.

> **How to navigate:** Click a section below—each page links onward to labs, diagrams, and references.

---

## 📘 Beginner
- [01 — Intro to Access Models](beginner/01_intro_access_models.md)
- [02 — IAM Fundamentals (AWS/Azure/GCP)](beginner/02_iam_fundamentals.md)
- [03 — Lab: Read‑Only Access (S3/Blob/Cloud Storage)](beginner/03_lab_readonly_access.md)

## 📗 Intermediate
- [04 — Enforcing Least‑Privilege (Design Patterns)](intermediate/04_enforcing_least_privilege.md)
- [05 — Failure Scenario & Rapid Remediation](intermediate/05_failure_scenario.md)
- [06 — Lab: Detect & Remove Unused Permissions](intermediate/06_lab_unused_permissions.md)

## 📕 Advanced
- [07 — Zero‑Trust + Least‑Privilege](advanced/07_zero_trust_least_privilege.md)
- [08 — Cross‑Cloud Identity & JIT Privilege](advanced/08_cross_cloud_architecture.md)
- [09 — Capstone: Multi‑Cloud Least‑Privilege Architecture](advanced/09_capstone_project.md)

## 📊 Diagrams
- [Least‑Privilege vs. Full Access](diagrams/least_privilege_vs_full_access.mmd)
- [Cross‑Cloud Identity Flow](diagrams/cross_cloud_identity_flow.mmd)

---

## 🧪 How to Use This Repo
1. **Read → Lab → Review**: Each module pairs concepts with a small lab.
2. **Fork → PR**: Improve policies, add detections, contribute new labs.
3. **Automation first**: Prefer IaC (Terraform) and policy-as-code.
4. **Security posture**: Add SIEM queries & alerts as you go.

**Local quickstart**
```bash
# from repo root
tree -L 2
# read
bat README.md || cat README.md
```

**Contribute**
- Open an issue, propose a lab, then PR your branch.
- Keep examples minimal, least‑privilege, and auditable.
