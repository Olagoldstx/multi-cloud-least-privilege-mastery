# 03 — Lab: Read‑Only Access (S3/Blob/GCS)

**Goal:** Grant **read‑only** access to a narrow data path in each cloud.

## AWS — S3 read to a prefix
1. Create a policy file `s3-read.json` (see Fundamentals page).
2. Attach to a **role** and let users **assume** it:
```bash
aws iam create-policy --policy-name S3ReadReports --policy-document file://s3-read.json
aws iam create-role --role-name ReportsReader --assume-role-policy-document file://trust.json
aws iam attach-role-policy --role-name ReportsReader --policy-arn arn:aws:iam::<ACC>:policy/S3ReadReports
aws sts assume-role --role-arn arn:aws:iam::<ACC>:role/ReportsReader --role-session-name demo
```

## Azure — Storage Blob Data Reader
```bash
az role assignment create --assignee "<user@contoso.com>" --role "Storage Blob Data Reader" --scope "<scope>"
```

## GCP — Cloud Storage Viewer
```bash
gcloud storage buckets add-iam-policy-binding gs://example-bucket   --member="user:alice@example.com" --role="roles/storage.objectViewer"
```

**Checkpoint**
- ✅ Read succeeds
- 🚫 Write/delete fails
- 🕒 Access is temporary where possible (PIM / short STS session)
