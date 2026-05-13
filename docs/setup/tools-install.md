# GPM-35: Required Development Tools

## Tools Required
| Tool | Purpose | Install Command |
|------|---------|-----------------|
| Java 17 | Build Spring Boot services | sudo apt install openjdk-17-jdk |
| Maven | Build tool (via wrapper) | included in repo as ./mvnw |
| Git | Version control | sudo apt install git |
| Docker | Container runtime | sudo apt install docker.io |
| Docker Compose | Multi-service local run | sudo apt install docker-compose-v2 |
| AWS CLI | AWS resource management | sudo apt install awscli |
| kubectl | Kubernetes CLI | snap install kubectl --classic |
| eksctl | EKS cluster management | via GitHub releases |
| Helm | Kubernetes package manager | snap install helm --classic |
| Terraform | Infrastructure as Code | via HashiCorp apt repo |

## Install Sequence
1. Java 17 first — required to build
2. Docker + Docker Compose — required to run locally
3. Git — required for all version control
4. AWS CLI — required for cloud tasks
5. kubectl + eksctl + Helm + Terraform — required for deployment tasks
