# GPM-137: Code Review Process — Achievers11-DevOps Team

## Branch Strategy
main   <- production, protected, requires PR + CI green + 1 reviewer
dev    <- integration, protected, requires PR + CI green + 1 reviewer
feature/GPM-{number}-{name}-{description} <- all work happens here

## Branch Naming Convention
feature/GPM-{ticket-number}-{your-name}-{short-description}

Examples:
feature/GPM-226-greg-local-setup
feature/GPM-227-greg-architecture
feature/GPM-50-anthonia-visits-service

## Commit Message Format
GPM-{ticket-number}: short description of what you did

Examples:
GPM-226: add repo access confirmation doc
GPM-32 GPM-33: clone steps and README review
GPM-38: local run complete — all 11 containers healthy

## Pull Request Workflow
1. Create feature branch from main
2. Do your work — commit with GPM-number in message
3. Push to your personal fork
4. Wait for CI to pass on your branch
5. Open PR from your fork to Achievers11-DevOps:dev
6. Add title: GPM-{number}: description
7. Add description: tickets covered, CI status, files changed, safety checks
8. Assign at least 1 reviewer (etaoko333 or iamDayoDev)
9. Assign yourself as assignee
10. Wait for approval — do NOT merge your own PR
11. After dev merge — Osenat raises PR from dev to main

## Code Review Rules
| Rule | Detail |
|------|--------|
| Minimum reviewers | 1 approving review required |
| Self-merge | Never — author cannot approve own PR |
| CI must pass | Green CI required before merge |
| Branch must be up to date | Rebase before PR if behind main |
| Review comments | All comments must be resolved before merge |
| Stale reviews | Re-review required if new commits pushed after approval |

## Reviewer Responsibilities
- Read every file changed in the PR
- Check commit messages reference correct Jira tickets
- Verify no existing files were modified without reason
- Verify no secrets are hardcoded
- Verify CI is green before approving
- Leave clear comments if changes are needed
- Approve only when all checks pass

## Author Responsibilities
- Keep PRs small and focused — one ticket or story per PR
- Write a clear PR description
- Respond to review comments within 24 hours
- Never force push to a branch with an open PR
- Never merge without approval
- Update Jira ticket status when PR is raised and when merged

## What NOT to Do
- Never commit directly to main or dev
- Never push AWS credentials, passwords, or API keys
- Never modify Osenat's Terraform, Helm, or ArgoCD files
- Never open a PR without CI being green first
- Never merge your own PR

## Files Team Members Should Never Modify
terraform/           <- Osenat's infrastructure code
helm/                <- Osenat's Kubernetes manifests
argocd/              <- Osenat's GitOps manifests
docker-compose.yml   <- do not modify
Dockerfile           <- do not modify
pom.xml              <- do not modify
src/                 <- do not modify application source
.github/workflows/ci.yml <- Osenat's main CI pipeline

## Safe Zones for Team Members
docs/                <- everyone's documentation
docs/setup/          <- setup guides
docs/architecture/   <- architecture docs
docs/process/        <- process documents
.github/workflows/   <- only add new workflows, never modify ci.yml
