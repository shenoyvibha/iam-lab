# iam-lab

A 10-week hands-on lab for learning Identity and Access Management (IAM), built in public.

> **Honest framing:** this is a learning lab, not production experience. Everything here was built to learn and to show my work.

## Goal

Move from product security and quality engineering into cloud IAM roles, then extend into AI agent identity and access management.

## Stack

AWS IAM and STS, Terraform, Python (boto3), Keycloak (Docker), GitHub Actions OIDC, and an MCP OAuth 2.1 gateway for the agent track.

## 10-week map

| Week | Folder | Focus |
|---|---|---|
| 0 | `00-setup/` | Environment and safety setup |
| 1 | `01-foundations/` | Identity model, RBAC matrix, matrix checker |
| 2 | `02-aws-iam-core/` | AWS IAM by hand: policies, roles, STS |
| 3 | `03-terraform-iam/` | Week 2 rebuilt as code |
| 4 | `04-protocols-keycloak/` | OAuth 2.0, OIDC, SAML with Keycloak |
| 5 | `05-federation-aws/` | Keycloak federated into AWS |
| 6 | `06-access-audit/` | Access audit script and evidence report |
| 7 | `07-workload-identity/` | GitHub Actions OIDC to AWS, secrets |
| 8 | `08-agent-identity-design/` | Agent identity threat model and design |
| 9 | `09-agent-identity-build/` | Agent identity build and denial tests |
| 10 | `10-capstone/` | Rebuild from scratch, case study |

Each week's folder has a README, a `failure-modes.md`, and at least one automated check.

## Rules I follow

- No secrets, keys or tokens in this repo.
- AWS account IDs and personal data are redacted in screenshots.
- Terraform state is never committed.
