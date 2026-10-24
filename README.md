# Ismaaeel Ahmed

### DevOps Engineer | AWS · Kubernetes · Terraform · CI/CD · Linux

I build and automate end-to-end cloud infrastructure, containerised applications and Kubernetes environments, applying **production-grade engineering practices** with a focus on reliable deployments, infrastructure as code and troubleshooting.

My engineering portfolio covers three projects: an **end-to-end AWS EKS platform with GitOps and monitoring**, an **automated ECS Fargate deployment**, and a **self-managed Kubernetes cluster built from scratch with kubeadm**. Across these projects, I've worked from infrastructure provisioning and networking through to application deployment, automation, monitoring and troubleshooting.

Each project includes source code, infrastructure configurations, architecture diagrams and documentation covering implementation decisions, technical challenges and how I resolved them.

[LinkedIn](https://www.linkedin.com/in/ismaaeelahmed) · [Email](mailto:ismaaeelahmed11@gmail.com) · [DevOps Learning Repository](https://github.com/ismaaeelahmed11/devops-learning)

---

## Featured Engineering Projects

| Project | Focus | Code & Walkthrough |
| --- | --- | --- |
| **AWS EKS — End-to-End Production-Grade Kubernetes, GitOps & Monitoring** | Terraform, Kubernetes, Argo CD, HTTPS, Prometheus/Grafana, CI/CD | [GitHub](https://github.com/ismaaeelahmed11/eks-project) · [Video (2:29)](https://youtu.be/RDmnaTi2auE) |
| **AWS ECS Fargate — End-to-End Production-Grade Infrastructure & CI/CD** | Terraform, Docker, ECR, ALB, GitHub Actions, OIDC, CloudWatch | [GitHub](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project) · [Video (2:11)](https://youtu.be/qpIZlJkWmos) |
| **Self-Managed Kubernetes — kubeadm & Cluster Operations** | Linux, kubeadm, containerd, Calico, cluster administration, troubleshooting | [GitHub](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [Video (2:00)](https://youtu.be/a9hATioCGcs) |

---

### 01 · [AWS EKS — End-to-End Production-Grade Kubernetes, GitOps & Monitoring](https://github.com/ismaaeelahmed11/eks-project)

**Terraform · Kubernetes · GitOps · Observability · CI/CD · Security**

Built an end-to-end AWS EKS Kubernetes platform for the IT-Tools application, applying production-grade engineering practices across infrastructure automation, Kubernetes orchestration, GitOps, CI/CD, security scanning and monitoring.

The platform combines Terraform-provisioned infrastructure, HTTPS ingress, automated GitOps reconciliation, monitoring and infrastructure troubleshooting.

**What I implemented**

- Provisioned an AWS VPC, EKS cluster and managed node group with **Terraform**, deploying **four worker nodes across two Availability Zones**.
- Configured **NGINX Ingress, cert-manager and ExternalDNS** for application routing, TLS certificates and Cloudflare DNS management.
- Implemented **Argo CD** for Git-based application reconciliation and self-healing.
- Set up **Prometheus and Grafana** for cluster metrics and monitoring dashboards.
- Built **GitHub Actions** workflows using AWS **OIDC authentication**, avoiding long-lived access keys.
- Integrated **Checkov and Trivy** for infrastructure and container security scanning.
- Configured Kubernetes health probes, CPU/memory requests and resource limits.

**Troubleshooting**

- **Persistent storage:** Investigated monitoring workloads unable to provision volumes, then configured the EBS CSI driver and required IAM permissions.
- **Pod scheduling:** Diagnosed workloads stuck in `Pending` because of node capacity constraints and adjusted the managed node group.
- **Cluster access:** Investigated authentication conflicts and resolved access configuration using EKS access entries.

**Result:** Successfully deployed a Kubernetes platform with application routing over HTTPS, automated GitOps reconciliation, Prometheus/Grafana monitoring and documented operational troubleshooting.

[**Explore Source Code, Architecture & Troubleshooting →**](https://github.com/ismaaeelahmed11/eks-project) · [**Watch the Walkthrough →**](https://youtu.be/RDmnaTi2auE)

---

### 02 · [AWS ECS Fargate — End-to-End Production-Grade Infrastructure & CI/CD](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

**AWS Infrastructure · Terraform · Docker · GitHub Actions · Networking**

Built an end-to-end AWS ECS Fargate deployment for a containerised Go application, applying production-grade infrastructure practices across Terraform, CI/CD, networking, security and logging.

I initially configured the AWS infrastructure manually before recreating it using eight Terraform modules and automating deployments through GitHub Actions.

**What I implemented**

- Containerised the application using a **multi-stage Docker build**, producing a **4.42 MB scratch-based image** running as a non-root user.
- Published container images to **Amazon ECR**.
- Provisioned AWS infrastructure with **eight Terraform modules**, covering networking, ECR, IAM, security groups, ACM, ALB, ECS and OIDC.
- Configured an **S3 remote state backend with native state locking**.
- Built **four GitHub Actions workflows** for image publishing, Terraform planning, infrastructure deployment and teardown.
- Used **OIDC authentication** to connect GitHub Actions to AWS without long-lived access keys.
- Configured an **Application Load Balancer, AWS Certificate Manager and HTTPS**.
- Added application health checks and **CloudWatch Logs**.

**Troubleshooting**

- **IAM permissions:** Resolved an ECS logging failure caused by missing CloudWatch Logs permissions.
- **CI/CD:** Fixed GitHub Actions workflows that were not triggering because of their directory structure.
- **Terraform:** Resolved a state-locking compatibility issue by aligning the Terraform version used in CI with the backend configuration.

**Result:** Successfully deployed a containerised application through Terraform-managed AWS infrastructure and automated CI/CD, with HTTPS, application health checks, logging and a repeatable infrastructure teardown workflow.

[**Explore Source Code, Architecture & Deployment Workflows →**](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project) · [**Watch the Walkthrough →**](https://youtu.be/qpIZlJkWmos)

---

### 03 · [Self-Managed Kubernetes — kubeadm & Cluster Operations](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab)

**Kubernetes Administration · Linux · Networking · Cluster Operations · Troubleshooting**

Built and operated a **two-node Kubernetes v1.35.9 cluster** on Ubuntu virtual machines using kubeadm, containerd and Calico.

Unlike Amazon EKS, this independent lab required me to configure the underlying Kubernetes infrastructure myself, including node connectivity, control-plane bootstrap, container runtime and pod networking.

**What I implemented**

- Created control-plane and worker-node VMs using **Oracle VirtualBox and Ubuntu Linux**.
- Configured **NAT, host-only networking and static IP addresses** for node communication and application access.
- Bootstrapped Kubernetes with **kubeadm** and configured **containerd** as the container runtime.
- Installed **Calico** for Kubernetes pod networking.
- Deployed NGINX using declarative Kubernetes Deployment and Service manifests.
- Configured **ClusterIP and NodePort Services**, readiness/liveness probes, and CPU/memory requests and limits.
- Tested **pod self-healing, scaling, rolling updates and rollback**.
- Documented the lab with Kubernetes manifests, architecture diagrams and **19 supporting screenshots**.

**Troubleshooting**

- **Virtualisation:** Investigated CPU lockups during cluster bootstrap, diagnosed virtualisation performance issues and recovered the VM environment.
- **Cluster access:** Investigated administrative access and RBAC issues during recovery.
- **Networking and readiness:** Verified Calico networking, Kubernetes system components and both nodes reaching `Ready`.

**Verified result:** Both Kubernetes nodes reached `Ready`, with **four available NGINX replicas** and application access from the Windows host through NodePort.

[**Explore Source Code, Architecture & Technical Evidence →**](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [**Watch the Walkthrough →**](https://youtu.be/a9hATioCGcs)

---

> **Project context:** The ECS and EKS environments were completed during my CoderCo DevOps Engineering programme, using real AWS infrastructure and production-grade engineering practices. The kubeadm cluster was built independently to develop deeper Kubernetes administration skills. These are portfolio projects, not claims of operating commercial production systems. AWS demonstration resources were removed after completion to avoid ongoing charges; code, diagrams and deployment evidence remain available.

---

## How I Approach Engineering

What I enjoy most is troubleshooting: investigating why something isn't working, following the evidence and understanding the root cause rather than just getting a service running once.

- **Build with infrastructure as code.** Use modular Terraform configurations, remote state and reviewable changes.
- **Understand the services underneath.** I built the ECS infrastructure manually before recreating it with Terraform, and built a kubeadm lab after working with managed EKS.
- **Automate repeatable work.** Use GitHub Actions for image publishing, Terraform workflows and application deployments.
- **Check how systems behave.** Work with Kubernetes health probes, CloudWatch Logs, Prometheus and Grafana, and test workload recovery and updates.
- **Troubleshoot methodically.** Inspect logs, IAM permissions, networking, configuration and resource constraints before making changes.
- **Make security part of delivery.** Apply OIDC authentication, IAM permissions, TLS/HTTPS and automated security scanning using Checkov and Trivy.
- **Document engineering decisions.** Record architecture, implementation decisions, failures, fixes and results so others can understand the work.
- **Manage cloud costs.** Use infrastructure teardown workflows to remove AWS demonstration resources when no longer needed.

---

## Technical Skills

| Area | Technologies & Practical Experience |
| --- | --- |
| **Cloud & Infrastructure** | AWS, VPC, EC2, ECS Fargate, EKS, IAM, ECR, ALB, ACM, CloudWatch |
| **Infrastructure as Code** | Terraform, reusable modules, variables, outputs, S3 remote state, state locking |
| **Containers & Kubernetes** | Docker, Kubernetes, kubeadm, containerd, Calico, Helm, NGINX Ingress |
| **CI/CD & Automation** | GitHub Actions, image publishing, infrastructure and application deployment workflows |
| **GitOps** | Argo CD, declarative Kubernetes configuration, Git-based reconciliation |
| **Monitoring & Observability** | Prometheus, Grafana, CloudWatch Logs |
| **Linux & Scripting** | Ubuntu, Bash, permissions, processes, file systems, command-line troubleshooting |
| **Networking** | TCP/IP, DNS, routing, subnetting, load balancing, NAT, HTTPS/TLS |
| **Version Control** | Git, GitHub, branching, merging, rebasing, pull requests |
| **Security Practices** | AWS OIDC, IAM, TLS certificates, Checkov, Trivy |

*Technical skills demonstrated through hands-on engineering projects, DevOps training and practical labs.*

---

## Background & Training

Completed the **CoderCo DevOps Engineering programme (January–October 2026)**, covering nine practical modules: Linux, Bash, Git, networking, Docker, AWS, Terraform, CI/CD and Kubernetes.

Alongside my DevOps portfolio, I bring **two years of professional IT support experience** troubleshooting Windows systems, networking, user access and day-to-day IT issues.

I continue to develop my Linux, infrastructure automation and Kubernetes skills through hands-on labs and documented exercises.

[**DevOps Training & Technical Exercises →**](https://github.com/ismaaeelahmed11/devops-learning) · [**Git & Version Control Labs →**](https://github.com/ismaaeelahmed11/git-labs)

---

## Connect

I'm open to opportunities across **DevOps Engineering, Cloud Engineering, Platform Engineering and Infrastructure Operations**, with a focus on building, automating and maintaining reliable infrastructure.

**Based in the United Kingdom** · **British citizen — no visa sponsorship required**

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
- **GitHub:** [github.com/ismaaeelahmed11](https://github.com/ismaaeelahmed11)
