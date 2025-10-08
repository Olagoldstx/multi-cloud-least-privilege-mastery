# 06 — Lab: Detect & Remove Unused Permissions

## AWS — Service Last Accessed
```bash
POL_ARN=arn:aws:iam::<ACC>:policy/YourPolicy
JOB=$(aws iam generate-service-last-accessed-details --arn $POL_ARN --query JobId --output text)
aws iam get-service-last-accessed-details --job-id "$JOB" > last-access.json
# Review services with "TotalAuthenticatedEntities"==0 and trim actions
```

## Azure — Access Review (PIM)
- Create an **Access Review** for a high‑value resource group.
- Require justification & auto‑remove non‑responders.

## GCP — IAM Recommender
```bash
gcloud recommender recommendations list   --recommender=google.iam.policy.Recommender   --project=<PROJECT>
# Apply carefully; review diffs.
```

**Success criteria**
- Policy diff shows **fewer actions** with same job success.
- New alerts fire if someone tries disallowed actions.
