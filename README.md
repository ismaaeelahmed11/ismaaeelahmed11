# Ismaaeel Ahmed

### DevOps Engineer | AWS · Kubernetes · Terraform · CI/CD · Linux

I build and automate cloud infrastructure, containerised applications and Kubernetes environments, with a focus on reliable deployments, infrastructure as code and troubleshooting.

My portfolio includes three end-to-end engineering projects: an **AWS EKS platform with GitOps and monitoring**, an **automated ECS Fargate deployment**, and a **self-managed Kubernetes cluster built using kubeadm**.

Each project includes source code, infrastructure configurations, architecture diagrams and documentation covering implementation decisions, technical challenges and their resolutions.

[LinkedIn](https://www.linkedin.com/in/ismaaeelahmed) · [Email](mailto:ismaaeelahmed11@gmail.com) · [GitHub Portfolio](https://github.com/ismaaeelahmed11/devops-learning)

---

## Featured Engineering Projects

### 01 · [AWS EKS — Kubernetes, GitOps & Monitoring](https://github.com/ismaaeelahmed11/eks-project)

**Infrastructure as Code · Kubernetes · GitOps · Observability · CI/CD**

Built an AWS Kubernetes environment for deploying and operating the IT-Tools application, combining Terraform infrastructure provisioning, HTTPS ingress, GitOps, monitoring and automated security scanning.

**Engineering implementation**

- Provisioned a VPC, EKS cluster and managed node group using **Terraform**, with four worker nodes across two Availability Zones.
- Configured **NGINX Ingress, cert-manager and ExternalDNS** for application routing, HTTPS certificates and DNS management.
- Implemented **Argo CD** to reconcile Kubernetes resources from Git.
- Deployed **Prometheus and Grafana** for cluster metrics and monitoring dashboards.
- Built **GitHub Actions** workflows using AWS OIDC authentication instead of long-lived access keys.
- Integrated **Checkov and Trivy** for Terraform and container image security scanning.
- Configured Kubernetes health probes, CPU/memory requests and limits.

**Troubleshooting and technical challenges**

- **Persistent storage:** Investigated monitoring workloads unable to provision volumes; configured the EBS CSI driver and required IAM permissions.
- **Pod scheduling:** Diagnosed workloads stuck in `Pending` due to node capacity constraints and adjusted the managed node group.
- **Cluster access:** Investigated conflicting authentication settings and resolved access configuration using EKS access entries.

**Technologies:** AWS EKS · Terraform · Kubernetes · Helm · Argo CD · GitHub Actions · Prometheus · Grafana · NGINX Ingress · IAM

[**Explore Source Code, Architecture & Troubleshooting →**](https://github.com/ismaaeelahmed11/eks-project)

---

### 02 · [AWS ECS Fargate — Container Deployment & Infrastructure Automation](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

**AWS Infrastructure · Terraform · Docker · CI/CD · Networking**

Built an end-to-end container deployment for a Go web application on AWS ECS Fargate, with infrastructure managed through Terraform and deployment workflows automated using GitHub Actions.

**Engineering implementation**

- Containerised the application using a **multi-stage Docker build** and a minimal scratch-based image running as a non-root user.
- Published container images to **Amazon ECR**.
- Provisioned AWS infrastructure through **eight Terraform modules**, including networking, ECS and load balancing.
- Configured an **S3 remote state backend with native state locking**.
- Built **four GitHub Actions workflows** covering image publishing, Terraform planning, infrastructure deployment and teardown.
- Implemented **OIDC authentication** for AWS access without storing long-lived access keys.
- Configured an **Application Load Balancer, ACM certificates and HTTPS**.
- Integrated application health checks and **CloudWatch Logs**.

**Troubleshooting and technical challenges**

- **IAM permissions:** Resolved an ECS logging failure caused by missing CloudWatch Logs permissions.
- **CI/CD:** Fixed GitHub Actions workflows that were not triggering because of their directory structure.
- **Terraform:** Resolved a state-locking compatibility issue by aligning the Terraform version used in CI with the backend configuration.

**Technologies:** AWS ECS Fargate · ECR · ALB · ACM · CloudWatch · Docker · Terraform · GitHub Actions · IAM

[**Explore Source Code, Architecture & Deployment Workflows →**](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)

---

### 03 · [Self-Managed Kubernetes — kubeadm, Networking & Cluster Operations](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab)

**Kubernetes Administration · Linux · Networking · Cluster Operations · Troubleshooting**

Built and operated a two-node Kubernetes cluster on Ubuntu virtual machines using **kubeadm, containerd and Calico**, working directly with the underlying infrastructure rather than relying on a managed Kubernetes service.

The environment runs Kubernetes v1.35.9 with four NGINX replicas deployed on the worker node.

**Engineering implementation**

- Provisioned control-plane and worker-node VMs using **Oracle VirtualBox and Ubuntu Linux**.
- Configured **NAT, host-only networking and static IP addresses** for cluster communication and application access.
- Bootstrapped Kubernetes using **kubeadm** and configured **containerd** as the container runtime.
- Installed **Calico** for Kubernetes pod networking.
- Deployed NGINX through declarative Kubernetes Deployment and Service manifests.
- Configured **ClusterIP and NodePort Services**, readiness/liveness probes and CPU/memory resource management.
- Tested **pod self-healing, horizontal scaling, rolling updates and rollback**.
- Documented the architecture, implementation, operations and troubleshooting with **19 supporting screenshots**.

**Troubleshooting and technical challenges**

- **Virtualisation performance:** Investigated repeated CPU lockups during Kubernetes bootstrap, diagnosed hardware acceleration issues and recovered the VM environment.
- **Cluster access:** Investigated Kubernetes administrative permissions and RBAC issues during recovery.
- **Networking and readiness:** Verified Calico networking, system components and both Kubernetes nodes reaching `Ready`.

**Verified outcome:** Two Kubernetes nodes Ready, four available NGINX replicas and application connectivity from the Windows host through NodePort.

**Technologies:** Kubernetes · kubeadm · Linux · containerd · Calico · NGINX · VirtualBox · Git

[**Explore Source Code, Architecture & Technical Evidence →**](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [Cluster Setup Guide](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab/blob/main/docs/cluster-setup.md)

---

> **Project context:** The ECS and EKS environments were developed during my DevOps engineering programme, while the kubeadm cluster was built independently to develop deeper Kubernetes infrastructure experience. AWS demonstration resources were removed after completion to avoid ongoing charges. Source code, infrastructure configurations, architecture diagrams and troubleshooting evidence remain available.

---

## Engineering Approach

I focus on understanding how systems work, automating where it adds value and investigating problems through to resolution.

- **Infrastructure as Code:** Build modular, version-controlled infrastructure with Terraform, including remote state and reviewable changes.
- **Understand before automating:** Built the ECS infrastructure manually before recreating it with Terraform to understand how the underlying AWS services connect.
- **Troubleshoot systematically:** Investigate logs, permissions, networking, configuration and resource constraints to identify root causes.
- **Work beyond managed Kubernetes:** Built a kubeadm cluster to gain direct experience with control-plane administration, container runtimes, CNI networking and workload scheduling.
- **Automate deployments:** Use GitHub Actions to build container images, manage infrastructure workflows and support application delivery.
- **Build with observability:** Integrate CloudWatch, Prometheus and Grafana to understand infrastructure and application behaviour.
- **Consider security:** Apply OIDC authentication, IAM permissions, TLS/HTTPS and automated security scanning.
- **Document engineering decisions:** Maintain diagrams, configuration examples and troubleshooting notes that explain both implementation and outcomes.
- **Manage costs:** Build infrastructure teardown into AWS demonstration workflows to avoid unnecessary spending.

---

## Technical Skills

| Area | Technologies & Practical Experience |
| --- | --- |
| **Cloud & Infrastructure** | AWS, VPC, EC2, ECS Fargate, EKS, IAM, ECR, ALB, ACM, CloudWatch |
| **Infrastructure as Code** | Terraform, reusable modules, variables, outputs, S3 remote state, state locking |
| **Containers & Kubernetes** | Docker, Kubernetes, kubeadm, containerd, Calico, Helm, NGINX Ingress |
| **CI/CD & Automation** | GitHub Actions, automated testing, image publishing, deployment workflows |
| **GitOps** | Argo CD, declarative Kubernetes configuration, Git-based reconciliation |
| **Monitoring & Observability** | Prometheus, Grafana, CloudWatch Logs |
| **Linux & Scripting** | Ubuntu, Bash, processes, permissions, file systems, command-line troubleshooting |
| **Networking** | TCP/IP, DNS, routing, subnetting, load balancing, NAT, HTTPS/TLS |
| **Version Control** | Git, GitHub, branching, merging, rebasing, pull requests |
| **Security Practices** | AWS OIDC, IAM, TLS certificates, Checkov, Trivy |

*Experience demonstrated through hands-on engineering projects, DevOps training and technical exercises.*

---

## DevOps Engineering Foundations

Completed the **CoderCo DevOps Engineering programme (January–October 2026)**, covering nine practical modules: Linux, Bash, Git, networking, Docker, AWS, Terraform, CI/CD and Kubernetes.

Applied these foundations through two AWS infrastructure projects and continued building independently with a self-managed Kubernetes environment.

My technical exercises include Linux administration, Bash automation, Git workflows, networking, Docker, Terraform and Kubernetes.

[**Explore My DevOps Training & Technical Exercises →**](https://github.com/ismaaeelahmed11/devops-learning) · [Git & Version Control Labs](https://github.com/ismaaeelahmed11/git-labs)

---

## Connect

I'm interested in connecting with engineers and teams working across DevOps, cloud platforms, Kubernetes, CI/CD and infrastructure automation.

**Based in the United Kingdom** · **British citizen — no visa sponsorship required**

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
- **GitHub:** [github.com/ismaaeelahmed11](https://github.com/ismaaeelahmed11)

---

*Building infrastructure. Automating delivery. Understanding systems.*
