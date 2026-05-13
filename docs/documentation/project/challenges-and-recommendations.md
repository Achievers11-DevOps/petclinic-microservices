# GPM-220: Challenges, Lessons Learned, and Recommendations

## Challenges Faced

### Challenge 1: AWS Cost Management
Problem: EKS cluster costs money even when idle
Impact: Risk of unexpected AWS bills
Resolution: Established terraform destroy rule after every session
Recommendation: Set billing alerts in AWS at dollar 10 and dollar 50

### Challenge 2: WSL2 Slow Container Startup
Problem: discovery-server takes 194 seconds on WSL2
Impact: Team members thought services were broken
Resolution: Documented expected startup times, added to troubleshooting guide
Recommendation: Use native Linux or increase WSL2 memory allocation

### Challenge 3: GitHub-Jira Integration Setup
Problem: Required both GitHub org owner and Jira site admin together
Impact: Integration took longer than expected to configure
Resolution: Greg (GitHub owner) and Idah (Jira admin) collaborated
Recommendation: Set up integration on day one of the project

### Challenge 4: Team Member Onboarding
Problem: Each team member needed individual setup guidance
Impact: Time spent on setup instead of delivery
Resolution: Tech Lead created individual deployment guides per member
Recommendation: Create team onboarding guide before sprint starts

### Challenge 5: Container Name Conflicts
Problem: docker compose up fails when old containers exist
Impact: Team members blocked and confused
Resolution: Documented fix: docker compose down --remove-orphans
Recommendation: Add this to team onboarding as day-one knowledge

### Challenge 6: Feature Branch Awareness
Problem: Risk of team members pushing to main directly
Impact: Could break live deployment
Resolution: Branch protection rules on main and dev
Recommendation: Set branch protection before first commit

## Key Achievements
8 microservices successfully deployed to AWS EKS
Fully automated CI/CD — zero manual deployments
Complete Infrastructure as Code via Terraform
GitOps deployment via ArgoCD
Production-grade monitoring with Prometheus and Grafana
Team of 10 collaborated without breaking main branch
Live application accessible at https://eta-oko.com

## Recommendations for Future Projects
1. Set up branch protection and CI on day one
2. Configure GitHub-Jira integration before first sprint
3. Create billing alerts in AWS immediately
4. Document terraform destroy as a team rule from day one
5. Give each team member a personalised setup guide
6. Test locally with Docker Compose before any AWS work
7. Use feature branches for every piece of work — no exceptions
8. Document as you go — not all at the end
9. Establish startup order knowledge early (config first always)
10. Use Secrets Manager from day one — never accept hardcoded secrets
