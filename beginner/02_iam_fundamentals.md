# 02 — IAM Fundamentals (AWS/Azure/GCP)

**Objective:** Map identities/roles/policies across clouds and learn the LP building blocks.

## Common Building Blocks
- **Principals**: who/what acts (users, groups, service accounts, workloads).
- **Permissions**: granular actions on resources (read, write, admin).
- **Policy**: JSON/YAML documents that allow/deny actions.
- **Scope**: resource or folder/subscription/account level.
- **Evaluation**: explicit deny > allow; condition evaluation; inheritance.

## AWS (IAM & STS)
- **Identities**: Users, Groups, Roles (assumed via STS), Instance/Task roles.
- **Policy JSON**: Action, Resource, Condition.
- **Guardrails**: SCPs (AWS Organizations), Permission Boundaries, Session Policies.

**Minimal S3 read policy**
```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": ["s3:GetObject"],
    "Resource": ["arn:aws:s3:::example-bucket/reports/*"]
  }]
}
```

## Azure (Entra ID + RBAC + PIM)
- **Identities**: Users, Groups, Service Principals, Managed Identities.
- **Scopes**: Management Group → Subscription → Resource Group → Resource.
- **Built-ins**: Reader, Contributor, Owner; prefer **custom roles** for LP.
- **PIM**: Just‑in‑time elevation and approval workflows.

**Assign Storage Blob Data Reader**
```bash
az role assignment create   --assignee "<user@contoso.com>"   --role "Storage Blob Data Reader"   --scope "/subscriptions/<SUB>/resourceGroups/<RG>/providers/Microsoft.Storage/storageAccounts/<acct>"
```

## GCP (Cloud IAM)
- **Identities**: Users, Groups, Service Accounts, Workload Identity.
- **Scopes**: Project, Folder, Organization; resource‑level where supported.
- **Recommender**: suggests LP bindings based on actual usage.

**Minimal GCS read binding**
```bash
gcloud storage buckets add-iam-policy-binding gs://example-bucket   --member="user:alice@example.com" --role="roles/storage.objectViewer"
```

**Next →** [03 — Lab: Read‑Only Access](03_lab_readonly_access.md)
