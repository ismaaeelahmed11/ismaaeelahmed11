# Ismaaeel Ahmed

### DevOps Engineer | AWS · Kubernetes · Terraform · CI/CD · Linux

I build and automate **end-to-end, production-style cloud infrastructure**, containerised applications and Kubernetes environments, with a focus on reliable deployments, infrastructure as code and troubleshooting.

My engineering portfolio covers three complete environments: an **AWS EKS platform with GitOps and monitoring**, an **automated ECS Fargate deployment**, and a **self-managed Kubernetes cluster built from scratch with kubeadm**. Across these projects, I've worked from infrastructure provisioning and networking through to application deployment, automation, monitoring and troubleshooting.

Each project includes source code, configuration, architecture diagrams and evidence of the implementation, including the technical problems I encountered and how I resolved them.

[LinkedIn](https://www.linkedin.com/in/ismaaeelahmed) · [Email](mailto:ismaaeelahmed11@gmail.com) · [DevOps Learning Repository](https://github.com/ismaaeelahmed11/devops-learning)

---

## Featured Engineering Projects

| Project | Focus | Code & walkthrough |
| --- | --- | --- |
| **AWS EKS — End-to-End Kubernetes Platform** | Terraform, Kubernetes, Argo CD GitOps, HTTPS, Prometheus/Grafana, CI/CD | [GitHub](https://github.com/ismaaeelahmed11/eks-project) · [Video (2:29)](https://youtu.be/RDmnaTi2auE) |
| **AWS ECS Fargate — End-to-End Infrastructure & CI/CD** | Terraform modules, Docker, ECR, ALB, GitHub Actions, OIDC, CloudWatch | [GitHub](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project) · [Video (2:11)](https://youtu.be/qpIZlJkWmos) |
| **Self-Managed Kubernetes — kubeadm & Cluster Operations** | Linux, kubeadm, containerd, Calico, workload lifecycle, troubleshooting | [GitHub](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [Video (2:00)](https://youtu.be/a9hATioCGcs) |

### 01 · [AWS EKS — End-to-End Kubernetes, GitOps & Monitoring](https://github.com/ismaaeelahmed11/eks-project)

**Terraform · Kubernetes · GitOps · Observability · CI/CD · Security**

Built an end-to-end AWS EKS environment to deploy and operate the IT-Tools application. The platform combines Terraform-provisioned infrastructure, HTTPS ingress, GitOps-based deployments, monitoring and automated security scanning.

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

**Result:** A deployed Kubernetes platform with application routing over HTTPS, automated GitOps reconciliation, monitoring and documented operational troubleshooting.

[**View EKS source code, architecture & troubleshooting →**](https://github.com/ismaaeelahmed11/eks-project) · [**Watch the walkthrough →**](https://youtu.be/RDmnaTi2auE)

---

### 02 · [AWS ECS Fargate — End-to-End Infrastructure & CI/CD](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

**AWS Infrastructure · Terraform · Docker · GitHub Actions · Networking**

Built an end-to-end deployment for a containerised Go web application on AWS ECS Fargate, with infrastructure managed through Terraform and build/deployment workflows automated using GitHub Actions.

**What I implemented**

- Containerised the application using a **multi-stage Docker build**, producing a minimal, scratch-based image that runs as a non-root user.
- Published container images to **Amazon ECR**.
- Provisioned AWS infrastructure with **eight Terraform modules**, including networking, ECS and load balancing.
- Configured an **S3 remote state backend with native state locking**.
- Built **four GitHub Actions workflows** for image publishing, Terraform planning, infrastructure deployment and teardown.
- Used **OIDC authentication** to connect GitHub Actions to AWS without long-lived access keys.
- Configured an **Application Load Balancer, AWS Certificate Manager and HTTPS**.
- Added application health checks and **CloudWatch Logs**.

**Troubleshooting**

- **IAM permissions:** Resolved an ECS logging failure caused by missing CloudWatch Logs permissions.
- **CI/CD:** Fixed GitHub Actions workflows that were not triggering because of their directory structure.
- **Terraform:** Resolved a state-locking compatibility issue by aligning the Terraform version used in CI with the backend configuration.

**Result:** A containerised application delivered through infrastructure as code and automated CI/CD, with HTTPS, health checks, logging and a repeatable teardown workflow.

[**View ECS source code, architecture & workflows →**](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project) · [**Watch the walkthrough →**](https://youtu.be/qpIZlJkWmos)

---

### 03 · [Self-Managed Kubernetes — kubeadm & Cluster Operations](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab)

**Kubernetes Administration · Linux · Networking · Cluster Operations · Troubleshooting**

Built and operated a **two-node Kubernetes v1.35.9 cluster** on Ubuntu virtual machines using kubeadm, containerd and Calico. Unlike EKS, this lab required me to configure the underlying Kubernetes environment myself, including node connectivity, cluster bootstrap and pod networking.

**What I implemented**

- Created control-plane and worker-node VMs using **Oracle VirtualBox and Ubuntu Linux**.
- Configured **NAT, host-only networking and static IP addresses** for node communication and application access.
- Bootstrapped Kubernetes with **kubeadm** and configured **containerd** as the container runtime.
- Installed **Calico** for pod networking.
- Deployed NGINX using declarative Kubernetes Deployment and Service manifests.
- Configured **ClusterIP and NodePort Services**, readiness/liveness probes, and CPU/memory requests and limits.
- Tested **pod self-healing, scaling, rolling updates and rollback**.
- Documented the lab with Kubernetes manifests, architecture diagrams, a setup guide and **19 supporting screenshots**.

**Troubleshooting**

- **Virtualisation:** Investigated CPU lockups during cluster bootstrap, diagnosed virtualisation performance issues and recovered the VM environment.
- **Cluster access:** Investigated administrative access and RBAC issues during recovery.
- **Networking and readiness:** Verified Calico networking, Kubernetes system components and both nodes reaching `Ready`.

**Verified result:** Both Kubernetes nodes reached `Ready`, with **four available NGINX replicas** and application access from the Windows host through NodePort.

[**View kubeadm source code, diagrams & evidence →**](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [**Setup guide →**](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab/blob/main/docs/cluster-setup.md) · [**Watch the walkthrough →**](https://youtu.be/a9hATioCGcs)

---

> **Project context:** ECS and EKS were completed as part of my CoderCo DevOps Engineering programme. I built the kubeadm lab independently to understand Kubernetes beyond a managed cloud service. These are production-style portfolio environments, not systems I claim to have operated for commercial customers. The AWS demonstration resources were removed after completion to avoid ongoing charges; code, diagrams and deployment evidence remain available.

## How I Approach Engineering

What I enjoy most is troubleshooting: investigating why something isn't working, following the evidence and understanding the root cause rather than just getting a service running once.

- **Build with infrastructure as code.** Use modular Terraform configurations, remote state and reviewable changes.
- **Understand the services underneath.** I built the ECS infrastructure manually before recreating it with Terraform, and built a kubeadm lab after working with managed EKS.
- **Automate repeatable work.** Use GitHub Actions for image publishing, Terraform workflows and deployments.
- **Check how systems behave.** Work with Kubernetes health probes, CloudWatch Logs, Prometheus and Grafana, and test workload recovery and updates.
- **Troubleshoot methodically.** Inspect logs, IAM permissions, networking, configuration and capacity before making changes.
- **Make security part of delivery.** Use OIDC, IAM permissions, TLS/HTTPS, Checkov and Trivy where appropriate.
- **Leave useful documentation.** Record architecture, implementation decisions, failures, fixes and results so others can understand the work.

## Technical Skills

| Area | Technologies & practical experience |
| --- | --- |
| **Cloud & Infrastructure** | AWS, VPC, EC2, ECS Fargate, EKS, IAM, ECR, ALB, ACM, CloudWatch |
| **Infrastructure as Code** | Terraform, reusable modules, variables, outputs, S3 remote state, state locking |
| **Containers & Kubernetes** | Docker, Kubernetes, kubeadm, containerd, Calico, Helm, NGINX Ingress |
| **CI/CD & Automation** | GitHub Actions, image publishing, infrastructure and application deployment workflows |
| **GitOps** | Argo CD, declarative configuration, Git-based reconciliation |
| **Monitoring & Observability** | Prometheus, Grafana, CloudWatch Logs |
| **Linux & Scripting** | Ubuntu, Bash, permissions, processes, file systems, command-line troubleshooting |
| **Networking** | TCP/IP, DNS, routing, subnetting, load balancing, NAT, HTTPS/TLS |
| **Version Control** | Git, GitHub, branching, merging, rebasing, pull requests |
| **Security Practices** | AWS OIDC, IAM, TLS certificates, Checkov, Trivy |

*Technical skills demonstrated through hands-on engineering projects, DevOps training and practical labs.*

## Background & Training

Completed the **CoderCo DevOps Engineering programme (January–October 2026)**, covering nine practical modules: Linux, Bash, Git, networking, Docker, AWS, Terraform, CI/CD and Kubernetes.

Alongside my DevOps portfolio, I bring **two years of professional IT support experience** troubleshooting Windows systems, networking, user access and day-to-day IT issues.

I continue to develop my Linux, infrastructure automation and Kubernetes skills through hands-on labs and documented exercises.

[**DevOps training & technical exercises →**](https://github.com/ismaaeelahmed11/devops-learning) · [**Git & version control labs →**](https://github.com/ismaaeelahmed11/git-labs)

---

## Connect

I'm open to opportunities across **DevOps Engineering, Cloud Engineering, Platform Engineering and Infrastructure Operations**, with a focus on building, automating and maintaining reliable infrastructure.

**Based in the United Kingdom** · **British citizen — no visa sponsorship required**

[LinkedIn](https://www.linkedin.com/in/ismaaeelahmed) · [Email](mailto:ismaaeelahmed11@gmail.com) · [GitHub](https://github.com/ismaaeelahmed11)

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
- **GitHub:** [github.com/ismaaeelahmed11](https://github.com/ismaaeelahmed11)

---

*Building infrastructure. Automating delivery. Understanding systems.*
