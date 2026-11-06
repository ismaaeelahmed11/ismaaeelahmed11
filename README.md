# Ismaaeel Ahmed

### DevOps Engineer | AWS · Kubernetes · Terraform · CI/CD · Linux

I build and automate **end-to-end cloud infrastructure**, containerised applications and Kubernetes environments, applying **production-grade engineering practices** across infrastructure as code, deployment automation, security, monitoring and troubleshooting.

I combine hands-on DevOps, cloud and platform engineering with **professional IT infrastructure engineering experience** spanning resilient networking, Windows systems administration, security, disaster recovery and complex technical troubleshooting.

My portfolio focuses on three complementary engineering projects:

- **AWS EKS:** A Kubernetes platform with Terraform, GitOps, CI/CD, HTTPS and observability.
- **AWS ECS Fargate:** Containerised application infrastructure built with eight Terraform modules and GitHub Actions workflows.
- **Self-Managed Kubernetes:** An independently engineered two-node kubeadm cluster using Ubuntu, containerd and Calico.

I work through the full engineering process: provisioning infrastructure, configuring networking and access, deploying applications, validating behaviour and investigating failures. My repositories include **source code, architecture diagrams, deployment evidence, technical walkthroughs and root-cause investigations** so you can inspect the work rather than simply read a list of tools.

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

Built and demonstrated an end-to-end Kubernetes platform on **Amazon EKS**, applying production-grade engineering practices across AWS infrastructure provisioning, Kubernetes operations, GitOps, monitoring and security reporting.

### Engineering Implementation

- Provisioned a VPC, public/private subnets, Amazon EKS and a managed node group with **Terraform**, configuring **four desired worker nodes across two Availability Zones**.
- Deployed the **IT-Tools** application with **two Kubernetes replicas**, health probes and resource requests/limits.
- Configured **NGINX Ingress, cert-manager and ExternalDNS** for HTTPS application access, Let's Encrypt certificates and Cloudflare DNS.
- Implemented **Argo CD** for Git-based Kubernetes reconciliation, with observed `Synced` and `Healthy` application status.
- Deployed **Prometheus and Grafana** for cluster and workload metrics; configured EBS-backed storage for monitoring components.
- Built **GitHub Actions** workflows for infrastructure provisioning, image publishing, application deployment and controlled teardown using **AWS OIDC** authentication.
- Integrated **Checkov and Trivy** to report infrastructure and container security findings. These scans were **non-blocking**, rather than enforced deployment gates.

### Troubleshooting & Problem Solving

- **Persistent Storage:** Investigated PVC provisioning failures and configured the Amazon EBS CSI Driver with the required IAM permissions.
- **Scheduling and Capacity:** Diagnosed Pods stuck in `Pending` and increased the managed node group's configured capacity.
- **Cluster Access:** Resolved conflicting EKS access configuration through explicit access entries.
- **CI/CD Authentication:** Investigated GitHub OIDC trust-policy conditions to restore AWS access from workflows.

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
- Improved infrastructure security by removing the broad `AdministratorAccess` policy attachment, restricting GitHub OIDC trust to the `main` branch and defining repository-scoped ECR image-publishing permissions.

### Troubleshooting & Problem Solving

- **Container Startup:** Resolved a privileged-port binding issue by running the application on port `8080`.
- **IAM and Logging:** Corrected missing CloudWatch Logs permissions for ECS.
- **GitHub Actions:** Fixed workflows that failed to trigger because of their repository location.
- **Terraform State:** Resolved S3 locking compatibility by aligning the Terraform version in CI with the backend configuration.
- **Load Balancing:** Investigated and resolved an ALB target group conflict during provisioning.

**Verified outcome:** Deployed and tested the Go application over a custom HTTPS domain using Terraform-managed AWS infrastructure, ECS health checks and CloudWatch logging. The image workflow publishes to ECR; **image publication alone does not automatically roll out a new ECS service revision**.

**Current automation status:** Terraform Apply requires manual triggering, and pull-request validation runs without AWS credentials. The IAM configuration includes restricted ECR publishing permissions, while separate roles and scoped permissions for future Terraform planning and deployment remain to be completed. The original AWS infrastructure was removed after successful demonstrations to control costs.

**[Explore source code, architecture and workflows](https://github.com/ismaaeelahmed11/devops-learning/tree/main/ecs-project)** · **[Watch walkthrough (2:11)](https://youtu.be/qpIZlJkWmos)**

---

## 03 · Self-Managed Kubernetes — kubeadm & Cluster Operations

**Linux · Kubernetes Administration · kubeadm · containerd · Calico · Networking · Troubleshooting**

Following my work with managed Amazon EKS, I independently engineered a **two-node Kubernetes v1.35.9 cluster** on Ubuntu VMs as part of my hands-on DevOps engineering development. The objective was to understand the underlying Linux infrastructure, control-plane administration and Kubernetes networking rather than relying entirely on a managed cloud platform.

### Engineering Implementation

- Created **Ubuntu control-plane and worker-node VMs** using Oracle VirtualBox.
- Configured **NAT, host-only networking and static IP addresses** for node communication and access.
- Bootstrapped Kubernetes with **kubeadm**, configured **containerd** and installed **Calico CNI** for pod networking.
- Deployed **four NGINX replicas** using declarative Kubernetes YAML.
- Exposed workloads through **ClusterIP and NodePort Services** and configured health probes and CPU/memory resource constraints.
- Tested **manual scaling, Pod replacement/self-healing, rolling updates and rollback**.
- Preserved Kubernetes manifests, architecture diagrams, a technical walkthrough and **19 implementation screenshots**.

### Troubleshooting & Problem Solving

- **Virtualisation:** Investigated VM CPU lockups and recovered the environment during cluster bootstrap.
- **Cluster Administration:** Diagnosed administrative Kubernetes API access and RBAC issues.
- **Networking:** Verified Calico, node connectivity, Kubernetes system components and workload access.

**Verified outcome:** Both nodes reached `Ready`, four NGINX replicas were available, and the application was accessible from the Windows host through NodePort. This was a self-managed lab, **not a highly available production cluster**.

**[Explore source code, manifests and evidence](https://github.com/ismaaeelahmed11/kubeadm-kubernetes-lab)** · **[Watch walkthrough (2:00)](https://youtu.be/a9hATioCGcs)**

---

> **Project context:** AWS ECS and EKS were completed during my CoderCo DevOps Engineering programme (January–October 2026), using real AWS services and production-grade engineering practices. I built the kubeadm lab independently as a complementary project during my continued DevOps engineering development, following EKS. These are **hands-on engineering portfolio projects**, not claims of commercial production ownership. The AWS resources were intentionally removed after successful demonstrations to manage costs; source code, architecture diagrams, workflow results and walkthroughs remain available.

---

## How I Approach Engineering

What I enjoy most is **troubleshooting**: working out why something failed, tracing the issue through the system and understanding the root cause rather than stopping once a command succeeds.

- **Understand the System:** Map service dependencies, networking, identity and request paths before automating.
- **Build Repeatably:** Use Terraform modules, remote state, version control and declarative Kubernetes manifests.
- **Automate Delivery:** Use GitHub Actions for image publishing, infrastructure workflows and Kubernetes application delivery where configured.
- **Apply Security Practices:** Use IAM, OIDC, HTTPS/TLS, network security controls and security-scanning tools; identify and document controls not yet enforced.
- **Observe and Verify:** Inspect logs, metrics, workload health, workflow results and application reachability.
- **Investigate Failures:** Work from evidence across IAM, network paths, storage, scheduling and tool compatibility.
- **Document Outcomes:** Preserve architecture diagrams, implementation evidence, root causes, fixes and known limitations.

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
| **Systems & Infrastructure Operations** | Windows administration, network resilience, WAN failover, network segmentation, endpoint security, backups and disaster recovery |

*Technical capabilities demonstrated through the engineering projects, practical labs and professional infrastructure experience described here.*

---

## Professional Infrastructure Engineering Background & Training

### IT Infrastructure Engineer | Arif Mobiles & Travel

**Luton, United Kingdom · 2022–2024**

Professional experience maintaining and securing business-critical infrastructure supporting travel bookings, payment processing, financial remittances and daily business operations.

- **Network Resilience:** Engineered and maintained business-critical networking, implementing automated **4G/5G WAN failover** to improve connectivity resilience.
- **Network Security:** Implemented **network segmentation and endpoint security controls**, isolating guest Wi-Fi from sensitive business transaction environments.
- **Systems Administration:** Administered **Windows systems, POS infrastructure and business applications**, including software deployments, security patching and maintenance.
- **Technical Troubleshooting:** Acted as the primary technical escalation contact, diagnosing and resolving complex hardware, TCP/IP networking and third-party integration failures with vendors.
- **Backup & Disaster Recovery:** Designed and maintained **encrypted cloud and on-premises backup processes**, supporting data protection, recovery and business continuity.

This professional infrastructure background informs how I approach cloud infrastructure, network architecture, IAM, system resilience, incident investigation and automation.

### DevOps Engineering | CoderCo

**January–October 2026**

Completed the **CoderCo DevOps Engineering programme**, covering nine practical modules:

**Linux · Bash · Git · Networking · Docker · AWS · Terraform · CI/CD · Kubernetes**

Applied these technologies through hands-on engineering projects, including AWS ECS Fargate, Amazon EKS, Terraform infrastructure automation and CI/CD workflows, alongside independent self-managed Kubernetes development.

I'm continuing to develop my AWS architecture, infrastructure automation, scripting and Kubernetes administration skills alongside my job search.

**[Explore DevOps training and technical labs](https://github.com/ismaaeelahmed11/devops-learning)** · **[Explore Git and version-control labs](https://github.com/ismaaeelahmed11/git-labs)**

---

## Connect

I'm open to opportunities in **DevOps Engineering, Cloud Engineering, Platform Engineering and Infrastructure Engineering**, where I can contribute practical engineering skills, professional infrastructure experience and a strong approach to automation, troubleshooting and reliability.

**Based in the United Kingdom** · **British citizen — no visa sponsorship required**

- **LinkedIn:** [linkedin.com/in/ismaaeelahmed](https://www.linkedin.com/in/ismaaeelahmed)
- **Email:** [ismaaeelahmed11@gmail.com](mailto:ismaaeelahmed11@gmail.com)
- **GitHub:** [github.com/ismaaeelahmed11](https://github.com/ismaaeelahmed11)

---

*Building infrastructure. Automating delivery. Understanding systems.*
