# 05 — Failure Scenario & Rapid Remediation

## Scenario
A dev user holds **AdministratorAccess** in AWS for convenience. Their laptop is compromised. The attacker:
- Creates backdoor users & keys
- Reads sensitive S3 buckets
- Spins up crypto‑miners (cost spike)
- Attempts to disable CloudTrail

## Discover the Blast Radius
- **AWS**
  - **Access Analyzer**: public/unused/over‑permissive findings
  - **Last Accessed**: identify unused services per policy
  - **CloudTrail**: enumerate actions by principal
  ```bash
  job=$(aws iam generate-service-last-accessed-details --arn arn:aws:iam::<ACC>:policy/AdminAccess --query JobId --output text)
  aws iam get-service-last-accessed-details --job-id "$job"
  ```

- **Azure**
  - **PIM**: list permanent Owner/Contributor; review activations
  - **Activity Logs / Defender for Cloud** alerts
  - **Azure Policy**: deny assignment gaps

- **GCP**
  - **Policy Analyzer**: who can do what
  - **IAM Recommender**: tightens roles from usage
  - **Cloud Audit Logs**: enumerate risky actions

## Rapid Remediation
1. **Contain**: disable compromised creds; rotate keys; force sign‑out.
2. **Revoke**: remove broad roles; replace with custom least‑privilege.
3. **Instrument**: ensure logs are immutable (S3 Object Lock, Log Analytics retention, GCS retention).
4. **Harden**: enable MFA/PIM/JIT; set max session duration; permission boundaries.
5. **Review**: run access recertification; document exceptions with expiry.
6. **Automate**: add CI checks for policy size/scope; policy‑as‑code tests.
