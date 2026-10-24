# Ismaaeel Ahmed

### DevOps Engineer | AWS · Kubernetes · Terraform · CI/CD · Linux

I build and automate **end-to-end cloud infrastructure**, containerised applications and Kubernetes environments, applying **production-grade engineering practices** across infrastructure as code, CI/CD, security, monitoring and troubleshooting.

My engineering portfolio covers three projects:

- **AWS EKS:** A Kubernetes platform with Terraform, GitOps, CI/CD, HTTPS and monitoring.
- **AWS ECS Fargate:** An automated container deployment using eight Terraform modules and GitHub Actions.
- **Self-Managed Kubernetes:** An independently built two-node Kubernetes cluster using kubeadm, containerd and Calico.

These projects cover the full deployment process, from provisioning infrastructure and configuring networking to deploying applications, automating delivery and resolving operational issues.

Each repository includes source code, configuration files, architecture diagrams, deployment evidence and documented troubleshooting.

[**LinkedIn**](https://www.linkedin.com/in/ismaaeelahmed) · [**Email**](mailto:ismaaeelahmed11@gmail.com) · [**DevOps Learning Repository**](https://github.com/ismaaeelahmed11/devops-learning)

---

## Featured Engineering Projects

| Project | Key Technologies | Source Code & Walkthrough |
| --- | --- | --- |
| **AWS EKS — End-to-End Production-Grade Kubernetes, GitOps & Monitoring** | Terraform, Kubernetes, Argo CD, GitHub Actions, Prometheus, Grafana | [GitHub](https://github.com/ismaaeelahmed11/eks-project) · [Video (2:29)](https://youtu.be/RDmnaTi2auE) |
| **AWS ECS Fargate — End-to-End Production-Grade Infrastructure & CI/CD** | Terraform, Docker, ECS, ECR, ALB, GitHub Actions, OIDC | [GitHub](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project) · [Video (2:11)](https://youtu.be/qpIZlJkWmos) |
| **Self-Managed Kubernetes — kubeadm & Cluster Operations** | Linux, kubeadm, containerd, Calico, Kubernetes networking | [GitHub](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [Video (2:00)](https://youtu.be/a9hATioCGcs) |

---

## 01 · AWS EKS — End-to-End Production-Grade Kubernetes, GitOps & Monitoring

**AWS · Terraform · Kubernetes · Helm · GitOps · CI/CD · Observability · Security**

Built and deployed an end-to-end Kubernetes platform on **Amazon EKS**, applying production-grade engineering practices across infrastructure automation, Kubernetes orchestration, GitOps, CI/CD, monitoring and security scanning.

### Engineering Implementation

- Provisioned an AWS VPC, EKS cluster and managed node group using **Terraform**, deploying **four worker nodes across two Availability Zones**.
- Deployed the IT-Tools application with **two Kubernetes replicas**, readiness/liveness probes and resource requests/limits.
- Configured **NGINX Ingress, cert-manager and ExternalDNS** for HTTPS application routing, Let's Encrypt certificates and Cloudflare DNS management.
- Implemented **Argo CD GitOps** for Git-based application reconciliation and automated synchronisation.
- Deployed **Prometheus and Grafana** for Kubernetes metrics, cluster visibility and monitoring dashboards.
- Built **GitHub Actions CI/CD workflows** using AWS OIDC authentication without long-lived AWS access keys.
- Integrated **Checkov and Trivy** for infrastructure and container security scanning.
- Configured **Amazon EBS CSI Driver and IRSA** to support persistent storage for monitoring workloads.

### Troubleshooting & Problem Solving

- **Persistent storage:** Investigated PVC provisioning failures and configured the EBS CSI Driver with the required IAM permissions.
- **Pod scheduling:** Diagnosed workloads stuck in `Pending` because of node capacity constraints and expanded the managed node group.
- **Cluster access:** Resolved conflicting EKS access configurations through explicit access entries.
- **CI/CD authentication:** Investigated OIDC trust policy conditions to restore GitHub Actions access to AWS.

**Outcome:** Successfully deployed a Kubernetes platform with HTTPS application access, Argo CD reporting `Synced` and `Healthy`, Prometheus/Grafana monitoring and working CI/CD pipelines.

**[View Source Code, Architecture & Troubleshooting →](https://github.com/ismaaeelahmed11/eks-project)** · **[Watch Project Walkthrough (2:29) →](https://youtu.be/RDmnaTi2auE)**

---

## 02 · AWS ECS Fargate — End-to-End Production-Grade Infrastructure & CI/CD

**AWS · Terraform · Docker · ECS Fargate · ECR · GitHub Actions · OIDC · CloudWatch**

Built and deployed an end-to-end AWS ECS Fargate environment for a containerised Go application, applying production-grade engineering practices across infrastructure as code, CI/CD, networking, security and logging.

I initially configured the AWS infrastructure manually before recreating it using **eight Terraform modules** and automating delivery through GitHub Actions.

### Engineering Implementation

- Containerised a Go application using a **multi-stage Docker build**, producing a **4.42 MB scratch-based image** running as a non-root user.
- Provisioned AWS infrastructure with **eight Terraform modules** covering VPC, ECR, security groups, IAM, ACM, ALB, ECS and OIDC.
- Configured **S3 remote Terraform state** with encryption, versioning and native state locking.
- Implemented an **Application Load Balancer**, target group, health checks, HTTPS and Cloudflare DNS integration.
- Built **four GitHub Actions workflows** for container publishing, Terraform planning, infrastructure deployment and teardown.
- Used **AWS OIDC federation** for GitHub Actions authentication without long-lived access keys.
- Integrated **CloudWatch Logs** for application logging and troubleshooting.

### Troubleshooting & Problem Solving

- **Container startup:** Resolved an application failure caused by binding to a privileged port, moving the application to port `8080`.
- **IAM permissions:** Fixed an ECS logging failure caused by missing CloudWatch Logs permissions.
- **GitHub Actions:** Corrected workflow placement after pipelines failed to trigger.
- **Terraform:** Resolved S3 state-locking compatibility by aligning the Terraform version used in CI with the backend configuration.
- **Load balancing:** Investigated and resolved an ALB target group conflict during Terraform provisioning.

**Outcome:** Successfully deployed a Go application over a custom HTTPS domain using Terraform-managed AWS infrastructure, automated CI/CD, application health checks and CloudWatch logging.

**[View Source Code, Architecture & CI/CD Workflows →](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)** · **[Watch Project Walkthrough (2:11) →](https://youtu.be/qpIZlJkWmos)**

---

## 03 · Self-Managed Kubernetes — kubeadm & Cluster Operations

**Linux · Kubernetes Administration · kubeadm · containerd · Calico · Networking · Troubleshooting**

Independently built and operated a **two-node Kubernetes v1.35.9 cluster** on Ubuntu virtual machines using kubeadm, containerd and Calico.

Unlike Amazon EKS, this lab required me to configure the Kubernetes environment directly, including the control plane, worker-node connectivity, container runtime and pod networking.

### Engineering Implementation

- Created Ubuntu control-plane and worker-node VMs using **Oracle VirtualBox**.
- Configured **NAT, host-only networking and static IP addresses** for cluster communication and application access.
- Bootstrapped Kubernetes using **kubeadm** and configured **containerd** as the container runtime.
- Installed **Calico CNI** for Kubernetes pod networking.
- Deployed **four NGINX replicas** using declarative Kubernetes manifests.
- Configured **ClusterIP and NodePort Services**, readiness/liveness probes and CPU/memory requests and limits.
- Tested **pod self-healing, manual scaling, rolling updates and rollback**.
- Documented the setup with Kubernetes manifests, architecture diagrams, a deployment guide and **19 supporting screenshots**.

### Troubleshooting & Problem Solving

- **Virtualisation:** Investigated CPU lockups during cluster bootstrap and recovered the VM environment.
- **Cluster administration:** Diagnosed administrative access and RBAC issues.
- **Networking:** Verified Calico pod networking, Kubernetes system components and node readiness.

**Verified Outcome:** Both Kubernetes nodes reached `Ready`, with **four available NGINX replicas** and application access from the Windows host through NodePort.

**[View Source Code, Architecture & Technical Evidence →](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab)** · **[Watch Project Walkthrough (2:00) →](https://youtu.be/a9hATioCGcs)**

---

> **Project context:** The ECS and EKS environments were completed as part of my CoderCo DevOps Engineering programme using real AWS infrastructure and production-grade engineering practices. I built the kubeadm lab independently to develop deeper Kubernetes administration skills. These are hands-on portfolio projects, not claims of operating commercial production systems. The AWS demonstration resources were removed after completion to avoid ongoing costs; source code, architecture diagrams, pipeline evidence and documentation remain available.

---

## How I Approach Engineering

What I enjoy most is troubleshooting — investigating why something isn't working, following the evidence and understanding the root cause rather than simply getting a service running once.

My approach is to:

- **Understand before automating:** Configure services manually where useful, then reproduce the environment using infrastructure as code.
- **Build repeatable infrastructure:** Use modular Terraform, remote state and version-controlled configurations.
- **Automate delivery:** Use GitHub Actions for container publishing, infrastructure changes and application deployment.
- **Apply security practices:** Use AWS IAM, OIDC authentication, TLS/HTTPS and automated security scanning.
- **Monitor and validate:** Use CloudWatch Logs, Prometheus, Grafana, Kubernetes health probes and workload checks.
- **Troubleshoot systematically:** Investigate logs, configuration, IAM permissions, networking, storage and resource capacity.
- **Document the engineering work:** Preserve code, architecture diagrams, implementation evidence, technical challenges and resolutions.

---

## Technical Skills

| Area | Technologies & Practical Experience |
| --- | --- |
| **Cloud & Infrastructure** | AWS, VPC, EC2, ECS Fargate, EKS, IAM, ECR, ALB, ACM, CloudWatch |
| **Infrastructure as Code** | Terraform, reusable modules, variables, outputs, S3 remote state, state locking |
| **Containers & Kubernetes** | Docker, Kubernetes, kubeadm, containerd, Calico, Helm, NGINX Ingress |
| **CI/CD & Automation** | GitHub Actions, image publishing, infrastructure and application deployment workflows |
| **GitOps** | Argo CD, declarative configuration, Git-based application reconciliation |
| **Monitoring & Observability** | Prometheus, Grafana, CloudWatch Logs |
| **Linux & Scripting** | Ubuntu, Bash, permissions, processes, file systems, command-line troubleshooting |
| **Networking** | TCP/IP, DNS, routing, subnetting, load balancing, NAT, HTTPS/TLS |
| **Version Control** | Git, GitHub, branching, merging, rebasing, pull requests |
| **Security Practices** | AWS OIDC, IAM, TLS certificates, Checkov, Trivy |

*Technical skills demonstrated through hands-on engineering projects, DevOps training and practical labs.*

---

## Background & Training

Completed the **CoderCo DevOps Engineering programme (January–October 2026)**, covering nine practical modules:

**Linux · Bash · Git · Networking · Docker · AWS · Terraform · CI/CD · Kubernetes**

Alongside my engineering portfolio, I bring **two years of professional IT support experience**, troubleshooting Windows systems, networking issues, user access and day-to-day IT operations.

I continue to develop my infrastructure automation, Linux and Kubernetes skills through hands-on technical exercises and documented labs.

**[Explore DevOps Training & Technical Labs →](https://github.com/ismaaeelahmed11/devops-learning)** · **[Explore Git & Version Control Labs →](https://github.com/ismaaeelahmed11/git-labs)**

---

## Connect

I'm open to opportunities across **DevOps Engineering, Cloud Engineering, Platform Engineering and Infrastructure Operations**, with a focus on building, automating and maintaining reliable infrastructure.

**Based in the United Kingdom** · **British citizen — no visa sponsorship required**

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
- **GitHub:** [github.com/ismaaeelahmed11](https://github.com/ismaaeelahmed11)

---

*Building infrastructure. Automating delivery. Understanding systems.*
