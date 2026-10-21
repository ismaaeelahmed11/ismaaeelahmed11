# Ismaaeel Ahmed

### DevOps & Cloud Engineering | AWS · Kubernetes · Terraform · CI/CD

I build and automate cloud infrastructure, containerised applications and Kubernetes environments, with a focus on reliable deployments, infrastructure as code and troubleshooting.

My hands-on portfolio covers three infrastructure projects: an AWS EKS platform with GitOps and monitoring, an automated AWS ECS Fargate deployment, and a self-managed Kubernetes cluster built using kubeadm.

Across these projects, I've worked with Terraform, Docker, Kubernetes, GitHub Actions, AWS networking, IAM, monitoring and Linux systems. My repositories include infrastructure code, deployment workflows, architecture diagrams, technical documentation and evidence of problems investigated and resolved.

I completed a nine-module DevOps engineering bootcamp and have continued building independent projects to develop deeper experience with infrastructure and Kubernetes operations.

**Open to DevOps, Cloud Engineering and Platform Engineering opportunities across the UK.**

[LinkedIn](https://www.linkedin.com/in/ismaaeelahmed) · [Email](mailto:ismaaeelahmed11@gmail.com) · [Explore My Portfolio](https://github.com/ismaaeelahmed11/devops-learning)

---

## Featured Engineering Projects

### 01 · [AWS EKS — Kubernetes, GitOps & Monitoring](https://github.com/ismaaeelahmed11/eks-project)

**Infrastructure as Code · Kubernetes · GitOps · Observability · CI/CD**

Built an AWS Kubernetes environment for deploying and operating the IT-Tools application, incorporating automated infrastructure provisioning, HTTPS ingress, GitOps reconciliation, monitoring and security scanning.

**Engineering implementation**

- Provisioned AWS networking, an EKS cluster and a managed node group using modular Terraform configurations.
- Configured NGINX Ingress, cert-manager and ExternalDNS for application routing, TLS certificates and DNS management.
- Implemented Argo CD to reconcile Kubernetes application resources from Git.
- Installed Prometheus and Grafana for metrics collection and monitoring dashboards.
- Built GitHub Actions workflows using AWS OIDC authentication instead of long-lived access keys.
- Integrated Checkov and Trivy for infrastructure and container security scanning.
- Configured Kubernetes readiness and liveness probes, resource requests and limits.

**Troubleshooting and technical challenges**

- **Persistent storage:** Investigated monitoring workloads unable to provision storage, then configured the EBS CSI driver and required IAM permissions.
- **Kubernetes scheduling:** Diagnosed pods remaining `Pending` because of node capacity constraints and adjusted the managed node group.
- **Cluster authentication:** Investigated conflicting access configuration and documented the resolution using explicit EKS access entries.

**Technologies:** AWS EKS · Terraform · Kubernetes · Helm · Argo CD · GitHub Actions · Prometheus · Grafana · NGINX Ingress · IAM

[Explore Source Code, Architecture & Troubleshooting →](https://github.com/ismaaeelahmed11/eks-project)

---

### 02 · [AWS ECS Fargate — Container Deployment & Infrastructure Automation](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

**AWS Infrastructure · Terraform · Docker · CI/CD · Networking**

Built an end-to-end container deployment for a Go web application on AWS ECS Fargate, with infrastructure managed through Terraform and deployments automated through GitHub Actions.

**Engineering implementation**

- Containerised the application using a multi-stage Docker build and a minimal scratch-based runtime image.
- Published container images to Amazon Elastic Container Registry (ECR).
- Organised AWS infrastructure into eight Terraform modules.
- Configured an S3 remote backend using native Terraform state locking.
- Automated container builds, Terraform planning, application deployment and infrastructure teardown with GitHub Actions.
- Used GitHub Actions OIDC authentication to access AWS without storing long-lived credentials.
- Configured an Application Load Balancer, ACM certificates and HTTPS application access.
- Integrated application health checks and CloudWatch logging.

**Troubleshooting and technical challenges**

- **IAM permissions:** Investigated why ECS tasks could not create their CloudWatch log group and added the missing permission.
- **CI/CD execution:** Resolved GitHub Actions workflows not triggering by correcting their repository directory structure.
- **Terraform state management:** Identified a Terraform version incompatibility with state locking and aligned the CI environment with the backend configuration.

**Technologies:** AWS ECS Fargate · ECR · ALB · ACM · CloudWatch · Docker · Terraform · GitHub Actions · IAM

[Explore Source Code, Architecture & Deployment Workflow →](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

---

### 03 · [Self-Managed Kubernetes — kubeadm, Networking & Cluster Operations](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab)

**Kubernetes Administration · Linux · Networking · Cluster Operations · Troubleshooting**

Built and operated a two-node Kubernetes cluster on Ubuntu virtual machines using kubeadm, gaining direct experience with Kubernetes infrastructure beyond managed services such as AWS EKS.

The environment uses Kubernetes v1.35.9, containerd and Calico, with an NGINX application running across four replicas on the worker node.

**Engineering implementation**

- Provisioned a control-plane and worker-node environment using Oracle VirtualBox and Ubuntu Linux.
- Configured NAT, host-only networking and static IP addresses for node communication and application access.
- Bootstrapped Kubernetes with kubeadm and configured containerd as the container runtime.
- Installed Calico for Kubernetes pod networking.
- Deployed NGINX using declarative Kubernetes Deployment and Service manifests.
- Configured ClusterIP and NodePort Services for internal connectivity and application access from the Windows host.
- Implemented CPU/memory requests and limits, readiness probes and liveness probes.
- Tested manual horizontal scaling, pod self-healing, rolling application updates and Deployment rollback.
- Documented infrastructure configuration, cluster operations and troubleshooting with 19 supporting screenshots.

**Troubleshooting and technical challenges**

- **Virtualisation performance:** Investigated repeated CPU lockups and control-plane bootstrap failures, diagnosed hardware acceleration issues and recovered the VM environment.
- **Kubernetes access:** Investigated administrative access and RBAC issues during cluster recovery.
- **Cluster networking and readiness:** Verified Calico networking, Kubernetes system components and node readiness.

**Verified outcome:** Two Kubernetes nodes in the `Ready` state, with four available NGINX replicas running on the worker node and accessible through NodePort.

**Technologies:** Kubernetes · kubeadm · Linux · containerd · Calico · NGINX · VirtualBox · Git

[Explore Source Code, Architecture & Technical Evidence →](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [Cluster Setup Guide](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab/blob/main/docs/cluster-setup.md)

---

> **Project context:** The ECS and EKS environments were completed as part of my DevOps training, while the kubeadm cluster was built independently to deepen my understanding of Kubernetes infrastructure. AWS resources were destroyed after project completion to avoid ongoing costs. Source code, deployment configurations, architecture diagrams and technical evidence remain available for review.

---

## Engineering Approach

My approach focuses on understanding infrastructure, building reproducible solutions and investigating problems through to resolution.

- **Infrastructure as Code:** Use Terraform to define and manage cloud infrastructure, keeping configurations modular, version-controlled and reviewable.
- **Understand before automating:** Built the ECS environment manually before reproducing the infrastructure with Terraform to understand how the underlying AWS components connect.
- **Troubleshoot systematically:** Investigate errors through logs, configuration, permissions, networking and resource constraints rather than relying on trial and error.
- **Understand Kubernetes beyond managed services:** Built a self-managed cluster to work directly with kubeadm, container runtimes, CNI networking, node readiness and control-plane administration.
- **Automate delivery:** Use GitHub Actions for application builds, container publishing, infrastructure planning and deployment workflows.
- **Build with visibility:** Incorporate CloudWatch, Prometheus and Grafana to observe application and infrastructure behaviour.
- **Consider security:** Use OIDC authentication, IAM permissions, HTTPS and automated security scanning where appropriate.
- **Document decisions and outcomes:** Record architecture, troubleshooting processes and operational evidence so engineering work can be reviewed and understood.
- **Manage cloud costs:** Include infrastructure teardown workflows and remove temporary AWS demonstration environments when no longer required.

---

## Technical Skills

| Area | Technologies & Practical Experience |
| --- | --- |
| **Cloud & Infrastructure** | AWS, VPC, EC2, ECS Fargate, EKS, IAM, ECR, ALB, ACM, CloudWatch, DNS |
| **Infrastructure as Code** | Terraform, modules, variables, outputs, S3 remote state, state locking |
| **Containers** | Docker, multi-stage Dockerfiles, Docker Compose, container registries, containerd |
| **Kubernetes** | kubeadm, Deployments, Services, Ingress, scheduling, probes, resource management, cluster networking |
| **CI/CD & Automation** | GitHub Actions, build and deployment workflows, automated testing, image publishing |
| **GitOps** | Argo CD, declarative Kubernetes configuration, Git-based reconciliation |
| **Monitoring & Observability** | Prometheus, Grafana, CloudWatch logs |
| **Linux & Scripting** | Linux administration, Bash, processes, permissions, file systems, text processing |
| **Networking** | TCP/IP, DNS, routing, subnetting, load balancing, NAT, host-only networking |
| **Version Control** | Git, GitHub, branching, merging, rebasing, pull requests |
| **Security Practices** | AWS OIDC, IAM permissions, TLS/HTTPS, Checkov, Trivy |

*Experience demonstrated through hands-on engineering projects, technical exercises and DevOps training.*

---

## DevOps Engineering Foundations

Completed nine practical modules covering infrastructure, automation, networking, cloud computing and Kubernetes.

| Module | Practical Work |
| --- | --- |
| [Linux Fundamentals](https://github.com/ismaaeelahmed11/devops-learning/tree/main/linux) | Linux command-line operations, permissions, processes and documented Bandit challenges |
| [Bash Scripting](https://github.com/ismaaeelahmed11/devops-learning/tree/main/bash-scripting) | File operations, input handling, permission checks and backup automation |
| [Git & Version Control](https://github.com/ismaaeelahmed11/git-labs) | Branching, merging, rebasing, stashing and recovering changes |
| [Networking](https://github.com/ismaaeelahmed11/devops-learning/tree/main/networking) | DNS, routing, subnetting and NGINX deployment on EC2 |
| [Docker & Containers](https://github.com/ismaaeelahmed11/devops-learning/tree/main/docker) | Container image builds and a multi-container Flask/Redis application |
| [AWS Cloud](https://github.com/ismaaeelahmed11/devops-learning/tree/main/aws) | VPC architecture, public/private subnets, EC2 and load balancing |
| [Terraform & Infrastructure as Code](https://github.com/ismaaeelahmed11/devops-learning/tree/main/terraform) | AWS infrastructure provisioning and automated instance configuration |
| [CI/CD](https://github.com/ismaaeelahmed11/devops-learning/tree/main/cicd) | GitHub Actions workflows for testing and container publishing |
| [Kubernetes](https://github.com/ismaaeelahmed11/devops-learning/tree/main/k8s) | Workload deployment, networking, configuration, storage and access-control exercises |

---

## What I'm Focused On

I'm continuing to develop my skills in cloud infrastructure, Kubernetes operations, infrastructure automation and deployment reliability.

My focus is on engineering environments that are understandable, maintainable and observable — and on strengthening the practical skills required to operate infrastructure reliably.

I'm particularly interested in working with teams responsible for cloud platforms, CI/CD pipelines, container infrastructure, Kubernetes and infrastructure automation.

---

## Opportunities & Contact

I'm open to opportunities in **DevOps Engineering, Cloud Engineering, Platform Engineering and Infrastructure Engineering** across the United Kingdom.

I bring hands-on portfolio experience in AWS infrastructure, Terraform automation, Kubernetes administration, CI/CD and Linux troubleshooting, alongside a strong interest in developing and supporting production engineering systems.

**Location:** United Kingdom  
**Work eligibility:** British citizen — no visa sponsorship required

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
- **GitHub:** [github.com/ismaaeelahmed11](https://github.com/ismaaeelahmed11)

---

*Building infrastructure. Automating delivery. Understanding systems.*
