# GPM-33: Clone the PetClinic Repository

## App Repo
git clone https://github.com/gregodprogrammer/petclinic-microservices.git
cd petclinic-microservices
git remote add upstream https://github.com/Achievers11-DevOps/petclinic-microservices.git

## Platform Repo
git clone https://github.com/gregodprogrammer/petclinic-k8s-platform.git
cd petclinic-k8s-platform
git remote add upstream https://github.com/Achievers11-DevOps/petclinic-k8s-platform.git

## Verify Remotes
git remote -v
# Expected output:
# origin    https://github.com/gregodprogrammer/{repo}.git (fetch)
# origin    https://github.com/gregodprogrammer/{repo}.git (push)
# upstream  https://github.com/Achievers11-DevOps/{repo}.git (fetch)
# upstream  https://github.com/Achievers11-DevOps/{repo}.git (push)

## Evidence
- petclinic-microservices: cloned successfully (11466 objects, 7.27 MiB)
- petclinic-k8s-platform: cloned successfully (161 objects, 59.85 KiB)
- Both upstream remotes confirmed pointing to Achievers11-DevOps org
