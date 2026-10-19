# Ismaaeel Ahmed

### DevOps & Cloud Engineering | AWS · Terraform · Kubernetes · CI/CD

I'm a UK-based DevOps bootcamp graduate with practical experience provisioning AWS infrastructure, containerising applications and automating deployment workflows.

After completing nine modules, I applied my learning through two AWS portfolio projects: an ECS Fargate application deployment and an EKS Kubernetes platform. My repositories include Terraform code, GitHub Actions workflows, architecture diagrams, deployment screenshots and troubleshooting notes.

I enjoy investigating why something has failed, understanding the underlying system and documenting the solution.

**Seeking junior DevOps, Cloud Engineer and Platform Engineering opportunities in the UK.**

[LinkedIn](https://www.linkedin.com/in/ismaaeelahmed) · [Email](mailto:ismaaeelahmed11@gmail.com) · [Explore My Portfolio](https://github.com/ismaaeelahmed11/devops-learning)

---
## Watch My Project Pitches

Short introductions to what I built, how it works and the problems I solved.

- **[Watch: AWS ECS Fargate — 1:17](https://github.com/ismaaeelahmed11/ismaaeelahmed11/blob/main/ECS-Recruiter-Pitch.mp4)**  
  Docker, Terraform, infrastructure automation and IAM troubleshooting.

- **[Watch: AWS EKS — 1:32](https://github.com/ismaaeelahmed11/ismaaeelahmed11/blob/main/EKS-Recruiter-Pitch.mp4)**  
  Kubernetes, GitOps, monitoring and persistent-storage troubleshooting.

---

## Featured Projects

### [AWS EKS — Kubernetes, GitOps & Monitoring](https://github.com/ismaaeelahmed11/eks-project)

An AWS Kubernetes portfolio project deploying IT-Tools with HTTPS, GitOps reconciliation and cluster monitoring.

**What I implemented**

- Provisioned a VPC, EKS cluster and managed node group using Terraform.
- Configured application access with NGINX Ingress, cert-manager and ExternalDNS.
- Set up Argo CD to reconcile Kubernetes resources from Git.
- Installed Prometheus and Grafana for cluster monitoring.
- Created GitHub Actions workflows using OIDC to authenticate with AWS.
- Integrated Checkov and Trivy scans into the application workflow.
- Configured application resource requests, limits, readiness and liveness probes.

**Problems I investigated and resolved**

- Monitoring workloads could not obtain persistent storage: configured the EBS CSI driver and the required IAM permissions.
- Pods remained pending because of node capacity limits: investigated the scheduling constraints and adjusted the node group.
- Cluster access configuration conflicted: documented the resolution using explicit EKS access entries.

**Stack:** AWS EKS · Terraform · Kubernetes · Helm · Argo CD · GitHub Actions · Prometheus · Grafana

[View Project, Architecture & Troubleshooting](https://github.com/ismaaeelahmed11/eks-project)

### [AWS ECS Fargate — Container Deployment & Infrastructure Automation](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

A Go web application deployed to ECS Fargate, served over HTTPS through an Application Load Balancer.

**What I implemented**

- Containerised the application using a multi-stage Docker build and a minimal scratch-based image.
- Published container images to Amazon ECR.
- Organised infrastructure into eight Terraform modules.
- Configured S3 remote state with native state locking.
- Created GitHub Actions workflows for image builds, Terraform planning, deployment and teardown.
- Used OIDC authentication for AWS access without storing long-lived AWS access keys in GitHub.
- Configured HTTPS with ACM and application health checks.

**Problems I investigated and resolved**

- ECS tasks could not create their CloudWatch log group: identified and added the missing permission.
- GitHub Actions workflows did not trigger: moved workflow definitions to the repository-level workflow directory.
- Terraform state locking was unsupported by the CI version: aligned the pipeline's Terraform version with the backend configuration.

**Stack:** AWS ECS Fargate · ECR · ALB · ACM · CloudWatch · Docker · Terraform · GitHub Actions

[View Project, Architecture & Deployment Workflow](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

> **Project scope:** These are bootcamp portfolio projects. Cloud infrastructure was destroyed after submission to avoid ongoing AWS costs. Source code, architecture diagrams, screenshots and troubleshooting documentation remain available for review.

---

## Engineering Approach

- **Understand before automating:** Built the ECS environment manually before recreating it with Terraform to understand how the AWS resources connect.
- **Investigate failures:** Documented issues involving IAM permissions, Kubernetes scheduling, persistent storage and CI configuration, including their causes and resolutions.
- **Make changes reviewable:** Used modular infrastructure code and a Terraform plan workflow for pull requests in the ECS project.
- **Explain design decisions:** Documented why I selected ECS or EKS, how traffic reaches the application and how the deployment components fit together.
- **Consider running costs:** Included teardown workflows and documented the decision to remove demonstration infrastructure after completion.

---

## Technical Skills

| Area | Practical Experience |
| --- | --- |
| Linux & Scripting | File systems, permissions, processes, text processing and Bash automation |
| Git & Collaboration Workflows | Branching, merging, rebasing, pull requests and GitHub |
| AWS & Networking | VPC, subnets, routing, EC2, IAM, ECR, ECS Fargate, EKS, load balancing and DNS |
| Infrastructure as Code | Terraform modules, variables, outputs, S3 remote state and state locking |
| Containers | Dockerfiles, multi-stage builds, Docker Compose and container registries |
| Kubernetes | Deployments, services, ingress, configuration, storage, probes and resource allocation |
| CI/CD | GitHub Actions, automated application tests, image publishing and Terraform workflows |
| GitOps | Argo CD application configuration and automated reconciliation |
| Monitoring | Prometheus, Grafana and CloudWatch logs |
| Security Practices | OIDC authentication, IAM configuration, HTTPS and Checkov/Trivy scanning |

*Skills above reflect hands-on bootcamp and portfolio experience.*

---

## DevOps Bootcamp — Nine Modules Completed

| Module | Practical Work |
| --- | --- |
| [Linux Fundamentals](https://github.com/ismaaeelahmed11/devops-learning/tree/main/linux) | Command-line exercises, permissions, processes and documented Bandit challenges |
| [Bash Scripting](https://github.com/ismaaeelahmed11/devops-learning/tree/main/bash-scripting) | File operations, input handling, permission checks and backup scripting |
| [Git & Version Control](https://github.com/ismaaeelahmed11/git-labs) | Branching, merging, rebasing, stashing and recovering changes |
| [Networking](https://github.com/ismaaeelahmed11/devops-learning/tree/main/networking) | DNS, routing, subnetting and NGINX deployment on EC2 |
| [Docker & Containers](https://github.com/ismaaeelahmed11/devops-learning/tree/main/docker) | Image builds and a multi-container Flask/Redis application |
| [AWS Cloud](https://github.com/ismaaeelahmed11/devops-learning/tree/main/aws) | VPC configuration, public/private subnets, EC2 and application load balancing |
| [Terraform & Infrastructure as Code](https://github.com/ismaaeelahmed11/devops-learning/tree/main/terraform) | Infrastructure provisioning and automated instance configuration |
| [CI/CD](https://github.com/ismaaeelahmed11/devops-learning/tree/main/cicd) | GitHub Actions workflows for application testing and container publishing |
| [Kubernetes](https://github.com/ismaaeelahmed11/devops-learning/tree/main/k8s) | Workload deployment, networking, configuration, storage and access-control exercises |

---

## Opportunities & Contact

I'm looking to join an engineering team where I can contribute to infrastructure automation, deployment workflows and troubleshooting while developing experience supporting production systems.

**Roles of interest:** Junior DevOps Engineer · Junior Cloud Engineer · Junior Platform Engineer

**Location:** United Kingdom

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
