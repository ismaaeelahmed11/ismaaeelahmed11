
# Ismaaeel Ahmed

### DevOps Engineer | AWS · Kubernetes · Terraform · CI/CD · Linux

I build and automate **end-to-end cloud infrastructure**, containerised applications and Kubernetes environments, applying **production-grade engineering practices** across infrastructure as code, deployment automation, security, monitoring and troubleshooting.

My portfolio focuses on three complementary engineering projects:

- **AWS EKS:** A Kubernetes platform with Terraform, GitOps, CI/CD, HTTPS and observability.
- **AWS ECS Fargate:** Containerised application infrastructure built with eight Terraform modules and GitHub Actions workflows.
- **Self-Managed Kubernetes:** An independent two-node kubeadm cluster using Ubuntu, containerd and Calico.

I work through the full delivery process: provisioning infrastructure, configuring networking and access, deploying applications, validating behaviour and investigating failures. The repositories include **source code, architecture diagrams, deployment evidence and troubleshooting notes** so you can inspect the work, not just read a list of tools.

**[LinkedIn](https://www.linkedin.com/in/ismaaeelahmed)** · **[Email](mailto:ismaaeelahmed11@gmail.com)** · **[DevOps Training & Labs](https://github.com/ismaaeelahmed11/devops-learning)**

---

## Featured Engineering Projects

| Project | Engineering Focus | Source Code & Walkthrough |
| --- | --- | --- |
| **AWS EKS — Production-Grade Kubernetes, GitOps & Monitoring** | Terraform, EKS, Helm, Argo CD, GitHub Actions, Prometheus, Grafana | [GitHub](https://github.com/ismaaeelahmed11/eks-project) · [Video (2:29)](https://youtu.be/RDmnaTi2auE) |
| **AWS ECS Fargate — Production-Grade Infrastructure & CI/CD** | Terraform, Docker, ECS, ECR, ALB, GitHub Actions, AWS OIDC | [GitHub](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project) · [Video (2:11)](https://youtu.be/qpIZlJkWmos) |
| **Self-Managed Kubernetes — kubeadm & Cluster Operations** | Ubuntu, Kubernetes, containerd, Calico, networking, troubleshooting | [GitHub](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab) · [Video (2:00)](https://youtu.be/a9hATioCGcs) |

---

## 01 · AWS EKS — Production-Grade Kubernetes, GitOps & Monitoring

**AWS · Terraform · Kubernetes · Helm · GitOps · CI/CD · Observability · Security**

Built and demonstrated an end-to-end Kubernetes platform on **Amazon EKS**, applying production-grade engineering practices to AWS infrastructure provisioning, Kubernetes operations, GitOps, monitoring and security reporting.

### Engineering Implementation

- Provisioned a VPC, public/private subnets, Amazon EKS and a managed node group with **Terraform**, configuring **four desired worker nodes across two Availability Zones**.
- Deployed the **IT-Tools** application with **two Kubernetes replicas**, health probes and resource requests/limits.
- Configured **NGINX Ingress, cert-manager and ExternalDNS** for HTTPS application access, Let's Encrypt certificates and Cloudflare DNS.
- Implemented **Argo CD** for Git-based Kubernetes reconciliation, with observed `Synced` and `Healthy` application status.
- Deployed **Prometheus and Grafana** for cluster and workload metrics; configured EBS-backed storage for monitoring components.
- Built **GitHub Actions** workflows for infrastructure provisioning, image publishing, application deployment and controlled teardown using **AWS OIDC** authentication.
- Integrated **Checkov and Trivy** to report infrastructure and container security findings. These scans were **non-blocking**, rather than enforced deployment gates.

### Troubleshooting & Problem Solving

- **Persistent storage:** Investigated PVC provisioning failures and configured the Amazon EBS CSI Driver with the required IAM permissions.
- **Scheduling and capacity:** Diagnosed Pods stuck in `Pending` and increased the managed node group's configured capacity.
- **Cluster access:** Resolved conflicting EKS access configuration through explicit access entries.
- **CI/CD authentication:** Investigated GitHub OIDC trust-policy conditions to restore AWS access from workflows.

**Verified outcome:** Demonstrated HTTPS application access, a working Kubernetes deployment, Argo CD reporting `Synced` / `Healthy`, and Prometheus/Grafana monitoring. The node group was configured for four desired workers; preserved screenshots show two Ready nodes at an earlier stage rather than independently proving four were running simultaneously.

**[Explore source code, architecture and troubleshooting](https://github.com/ismaaeelahmed11/eks-project)** · **[Watch walkthrough (2:29)](https://youtu.be/RDmnaTi2auE)**

---

## 02 · AWS ECS Fargate — Production-Grade Infrastructure & CI/CD

**AWS · Terraform · Docker · ECS Fargate · ECR · ALB · GitHub Actions · OIDC · CloudWatch**

Built and deployed an **AWS ECS Fargate** environment for a containerised Go application. I first configured key AWS resources manually to understand their dependencies, then rebuilt the environment using **eight reusable Terraform modules** and GitHub Actions automation.

### Engineering Implementation

- Containerised a Go HTTP application with a **multi-stage Docker build**, producing a **4.42 MB**, non-root, `scratch`-based image.
- Provisioned infrastructure through **eight Terraform modules**, including VPC, ECR, security groups, IAM, ACM, ALB, ECS and OIDC.
- Configured **S3 remote Terraform state** with encryption, versioning and native state locking.
- Set up an **Application Load Balancer**, target group, health checks, ACM-managed HTTPS and Cloudflare DNS.
- Created **four GitHub Actions workflows** for container image publishing, Terraform planning, infrastructure provisioning and teardown.
- Used **AWS OIDC federation** in GitHub Actions rather than storing long-lived AWS access keys.
- Integrated **Amazon CloudWatch Logs** for application diagnostics.

### Troubleshooting & Problem Solving

- **Container startup:** Resolved a privileged-port binding issue by running the application on port `8080`.
- **IAM and logging:** Corrected missing CloudWatch Logs permissions for ECS.
- **GitHub Actions:** Fixed workflows that failed to trigger because of their repository location.
- **Terraform state:** Resolved S3 locking compatibility by aligning the Terraform version in CI with the backend configuration.
- **Load balancing:** Investigated and resolved an ALB target group conflict during provisioning.

**Verified outcome:** Deployed and tested the Go application over a custom HTTPS domain using Terraform-managed AWS infrastructure, ECS health checks and CloudWatch logging. The image workflow publishes to ECR; **image publication alone does not automatically roll out a new ECS service revision**.

**[Explore source code, architecture and workflows](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)** · **[Watch walkthrough (2:11)](https://youtu.be/qpIZlJkWmos)**

---

## 03 · Self-Managed Kubernetes — kubeadm & Cluster Operations

**Linux · Kubernetes Administration · kubeadm · containerd · Calico · Networking · Troubleshooting**

After building on managed Amazon EKS, I independently created a **two-node Kubernetes v1.35.9 cluster** on Ubuntu VMs to understand the underlying administration and networking rather than relying on a managed control plane.

### Engineering Implementation

- Created **Ubuntu control-plane and worker-node VMs** using Oracle VirtualBox.
- Configured **NAT, host-only networking and static IP addresses** for node communication and access.
- Bootstrapped Kubernetes with **kubeadm**, configured **containerd** and installed **Calico CNI** for pod networking.
- Deployed **four NGINX replicas** from declarative Kubernetes YAML.
- Exposed workloads through **ClusterIP and NodePort Services** and configured health probes and CPU/memory resources.
- Tested **manual scaling, Pod replacement/self-healing, rolling updates and rollback**.
- Preserved Kubernetes manifests, architecture diagrams, a technical walkthrough and **19 implementation screenshots**.

### Troubleshooting & Problem Solving

- **Virtualisation:** Investigated VM CPU lockups and recovered the environment during cluster bootstrap.
- **Cluster administration:** Diagnosed administrative Kubernetes API access and RBAC issues.
- **Networking:** Verified Calico, node connectivity, Kubernetes system components and workload access.

**Verified outcome:** Both nodes reached `Ready`, four NGINX replicas were available, and the application was accessible from the Windows host through NodePort. This was a self-managed lab, **not a highly available production cluster**.

**[Explore source code, manifests and evidence](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab)** · **[Watch walkthrough (2:00)](https://youtu.be/a9hATioCGcs)**

---

> **Project context:** AWS ECS and EKS were completed during my CoderCo DevOps Engineering programme (January–October 2026), using real AWS services and production-grade engineering practices. I built the kubeadm lab independently afterwards. These are **hands-on engineering portfolio projects**, not claims of commercial production ownership. The AWS resources were intentionally removed after successful demonstrations to manage costs; source code, architecture diagrams, workflow results and walkthroughs remain available.

---

## How I Approach Engineering

What I enjoy most is **troubleshooting**: working out why something failed, tracing the issue through the system and understanding the root cause rather than stopping once a command succeeds.

- **Understand the system:** Map service dependencies, networking, identity and request paths before automating.
- **Build repeatably:** Use Terraform modules, remote state, version control and declarative Kubernetes manifests.
- **Automate delivery:** Use GitHub Actions for image publishing, infrastructure workflows and Kubernetes application delivery where configured.
- **Apply security practices:** Use IAM, OIDC, HTTPS/TLS and security-scanning tools; document controls not yet enforced.
- **Observe and verify:** Inspect logs, metrics, workload health, workflow results and application reachability.
- **Investigate failures:** Work from evidence across IAM, network paths, storage, scheduling and tool compatibility.
- **Document the outcome:** Preserve architecture diagrams, implementation evidence, root causes and known limitations.

---

## Technical Skills

| Area | Technologies & Hands-on Experience |
| --- | --- |
| **Cloud & Infrastructure** | AWS, VPC, EC2, ECS Fargate, EKS, IAM, ECR, ALB/NLB, ACM, CloudWatch |
| **Infrastructure as Code** | Terraform, reusable modules, variables, outputs, S3 remote state, native state locking |
| **Containers & Kubernetes** | Docker, Kubernetes, kubeadm, containerd, Calico, Helm, NGINX Ingress |
| **CI/CD & Automation** | GitHub Actions, container image publishing, Terraform plan/apply/teardown, application deployment workflows |
| **GitOps** | Argo CD, declarative manifests, Git-based application reconciliation |
| **Monitoring & Observability** | Prometheus, Grafana, CloudWatch Logs, Kubernetes health checks |
| **Linux & Scripting** | Ubuntu, Bash, permissions, processes, services, filesystems, CLI troubleshooting |
| **Networking** | TCP/IP, DNS, routing, subnetting, NAT, load balancing, HTTPS/TLS |
| **Version Control** | Git, GitHub, branches, pull requests, merges and rebasing |
| **Security Practices** | AWS IAM/OIDC, TLS certificates, Checkov and Trivy reporting |

*Skills demonstrated through the projects and practical labs linked above, not represented as years of commercial DevOps experience.*

---

## Background & Training

Completed the **CoderCo DevOps Engineering programme (January–October 2026)**, covering nine practical modules:

**Linux · Bash · Git · Networking · Docker · AWS · Terraform · CI/CD · Kubernetes**

I also bring **two years of professional IT support experience**, troubleshooting Windows systems, connectivity, staff access and day-to-day technology operations. That background informs my approach to incident investigation and reliable infrastructure.

I'm continuing to develop my AWS architecture, infrastructure automation, scripting and Kubernetes administration skills alongside my job search.

**[Explore DevOps training and technical labs](https://github.com/ismaaeelahmed11/devops-learning)** · **[Explore Git and version-control labs](https://github.com/ismaaeelahmed11/git-labs)**

---

## Connect

I'm open to opportunities in **DevOps Engineering, Cloud Engineering, Platform Engineering and Infrastructure Operations** where I can contribute practical engineering skills, continue learning and help build reliable systems.

**Based in the United Kingdom** · **British citizen — no visa sponsorship required**

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
- **GitHub:** [github.com/ismaaeelahmed11](https://github.com/ismaaeelahmed11)

---

*Building infrastructure. Automating delivery. Understanding systems.*
