# Jonathan DeLeon

I work on the infrastructure and security side of things, and I like keeping those two connected instead of treating security like something you bolt on afterward. Day to day that looks like hypervisors, Kubernetes, IaC pipelines, identity, and the compliance work that ties it together.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/jonathan-deleon-cism/)
[![Credly](https://img.shields.io/badge/Credly-F7931E?style=flat-square&logo=credly&logoColor=white)](https://www.credly.com/users/jonathan-deleon.bfdd720a)
[![GitOps Notes](https://img.shields.io/badge/GitOps%20Notes-222222?style=flat-square&logo=githubpages&logoColor=white)](https://mrguato.github.io/gitops-notes/)
[![Landing Site](https://img.shields.io/badge/Landing%20Site-%236A5ACD?style=flat-square&logo=amazonaws&logoColor=white)](https://cloud.mrcyberleon.org/)

---

## Live: homelab k3s cluster

[![Cluster](https://img.shields.io/website?url=https%3A%2F%2Fstatus.deleontech.net&up_message=healthy&up_color=brightgreen&down_message=degraded&down_color=red&label=status.deleontech.net&style=for-the-badge&logo=kubernetes&logoColor=white)](https://status.deleontech.net)

Multi-arch k3s cluster running on a Raspberry Pi 4 and a Lenovo ThinkCentre I picked up secondhand. Everything is managed through FluxCD from [`MrGuato/pi-cluster`](https://github.com/MrGuato/pi-cluster) so I never really touch the cluster directly. Secrets are encrypted with SOPS and age and committed right into the repo. Traefik handles routing, Cloudflare Tunnel gets traffic in without exposing anything, Longhorn does the block storage, and Velero backs everything up to a MinIO bucket on a separate node. The dashboard above is pulling from kube-prometheus-stack.

---

## What I work on

A rough map of where I spend my time and the tools I tend to reach for.

| Area | Notes |
|---|---|
| Kubernetes | k3s, Helm, FluxCD, Kustomize, Longhorn, Velero. Currently looking at Talos and Omni. |
| IaC | Terraform, Ansible, and Packer. I usually build golden images with Packer, spin them up with Terraform, and let Ansible handle the config drift. |
| CI/CD | GitLab CI and GitHub Actions, with Flux for GitOps. I like keeping scanning (SAST, SBOM, container, IaC) as actual gates in the pipeline so things fail fast. |
| Virtualization | vSphere and ProxMox. Hardened base images and automated patching. |
| Network | FortiGate, Palo Alto, Ubiquiti, Cisco. |
| Identity | Entra ID and Conditional Access. |
| Compliance | Leading a CMMC Level 2 program. Also comfortable with CIS v8, NIST CSF 2.0, and Zero Trust work. |
| Security ops | Sentinel, SentinelOne, Rapid7, Defender XDR, and Tines for SOAR. Good telemetry usually makes detection a lot easier. |

---

## Projects

### [pi-cluster](https://github.com/MrGuato/pi-cluster)
My homelab cluster, fully declarative. Flux reconciles apps and infrastructure from Git, SOPS-encrypted secrets live in the public repo, and Renovate keeps image tags fresh with automated PRs. Velero does restic backups out to MinIO on a separate node, and Longhorn handles distributed block storage across the ARM and x86 nodes. The live dashboard at the top of this README runs on it.

### [enshrouded-docker](https://github.com/MrGuato/enshrouded-docker)
Containerized game server for Enshrouded, built from scratch on ubuntu:22.04 with WineHQ and SteamCMD. Runs as non-root with semantic versioning and a GitHub Actions pipeline that publishes signed images to GHCR. Getting SteamCMD symlinks and Xvfb lock files to behave in a clean container was more fun than I expected.

### [Azure-Blob-Sync-Action](https://github.com/MrGuato/Azure-Blob-Sync-Action)
A small reusable GitHub Action I wrote for syncing build artifacts to Azure Blob Storage. Published publicly so other folks can use it.

### [AWS-Cloud-Challenge](https://github.com/MrGuato/AWS-Cloud-Challenge)
A serverless site on S3, CloudFront, Lambda, API Gateway, and DynamoDB, all provisioned through CloudFormation with least-privilege IAM and a proper deploy pipeline.

---

## Stack

#### Platform
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)
![FluxCD](https://img.shields.io/badge/FluxCD-5468FF?style=for-the-badge&logo=flux&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=for-the-badge&logo=proxmox&logoColor=white)
![vSphere](https://img.shields.io/badge/vSphere-607078?style=for-the-badge&logo=vmware&logoColor=white)

#### Infrastructure as Code
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Packer](https://img.shields.io/badge/Packer-02A8EF?style=for-the-badge&logo=packer&logoColor=white)
![CloudFormation](https://img.shields.io/badge/CloudFormation-FF4F8B?style=for-the-badge&logo=amazonaws&logoColor=white)

#### Pipelines and supply chain
![GitLab CI](https://img.shields.io/badge/GitLab%20CI-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Snyk](https://img.shields.io/badge/Snyk-4C4A73?style=for-the-badge&logo=snyk&logoColor=white)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=for-the-badge&logo=aqua&logoColor=white)
![SOPS](https://img.shields.io/badge/SOPS%2Fage-000000?style=for-the-badge)
![Renovate](https://img.shields.io/badge/Renovate-1A1F6C?style=for-the-badge&logo=renovatebot&logoColor=white)

#### Cloud and edge
![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Traefik](https://img.shields.io/badge/Traefik-24A1C1?style=for-the-badge&logo=traefikproxy&logoColor=white)

#### Network
![Fortinet](https://img.shields.io/badge/FortiGate-EE2E24?style=for-the-badge&logo=fortinet&logoColor=white)
![Palo Alto](https://img.shields.io/badge/Palo%20Alto-172A6B?style=for-the-badge&logo=paloaltonetworks&logoColor=white)
![Ubiquiti](https://img.shields.io/badge/Ubiquiti-0559C9?style=for-the-badge&logo=ubiquiti&logoColor=white)

#### Observability
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F5A800?style=for-the-badge&logo=grafana&logoColor=white)

#### Security operations
![Sentinel](https://img.shields.io/badge/Sentinel-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![SentinelOne](https://img.shields.io/badge/SentinelOne-5B2E91?style=for-the-badge&logo=sentinelone&logoColor=white)
![Rapid7](https://img.shields.io/badge/Rapid7-D02F2F?style=for-the-badge&logo=rapid7&logoColor=white)
![Defender XDR](https://img.shields.io/badge/Defender%20XDR-00A4EF?style=for-the-badge&logo=microsoft&logoColor=white)
![Tines](https://img.shields.io/badge/Tines-5A67D8?style=for-the-badge)
![Nessus](https://img.shields.io/badge/Nessus-00B3E3?style=for-the-badge&logo=tenable&logoColor=white)

#### Compliance
![CMMC L2](https://img.shields.io/badge/CMMC%20L2-006400?style=for-the-badge)
![NIST 800-171](https://img.shields.io/badge/NIST%20800--171-4CAF50?style=for-the-badge)
![NIST CSF 2.0](https://img.shields.io/badge/NIST%20CSF%202.0-4CAF50?style=for-the-badge)
![CIS v8](https://img.shields.io/badge/CIS%20v8-E91E63?style=for-the-badge)
![Zero Trust](https://img.shields.io/badge/Zero%20Trust-FF6F00?style=for-the-badge)

---

## Credentials

<img src="https://images.credly.com/size/680x680/images/d0891dee-6360-496c-9981-40652523b502/dbdea6794f1a6bbcc18d90eea923421aac7df6b5.png" alt="CISM" width="50" height="50"> <img src="https://images.credly.com/size/340x340/images/38b12225-5b48-44e1-8750-20928cc595ea/image.png" alt="Badge 1" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/564a69d3-b7c6-4738-aa2e-1d803869876c/blob" alt="Badge 1A" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/6b9a3559-90bd-4412-b156-21f99670206a/image.png" alt="Badge 1B" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/fc1352af-87fa-4947-ba54-398a0e63322e/security-compliance-and-identity-fundamentals-600x600.png" alt="Badge 2" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/be8fcaeb-c769-4858-b567-ffaaa73ce8cf/image.png" alt="Badge 3" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/20082fc1-94af-4773-9df0-28856b566748/image.png" alt="Badge 4" width="50" height="50"><img src="https://www.itonlinelearning.com/wp-content/uploads/2024/01/04294-comptia-cert-badges_specialist-ccap-540x503.png" alt="CompTIA CCAP" width="50" height="50"><img src="https://comptiacdn.azureedge.net/webcontent/images/default-source/certproduct/pathways/04294-comptia-cert-badges-csis.png?sfvrsn=64a8a736_2" alt="CompTIA CSIS" width="50" height="50"><img src="https://nyledige.dk/media/2155/secure-cloud-professional-cscp-for-ledige.png?width=1024&height=1024&mode=min" alt="Badge 6" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/7495098d-c8c3-41a8-a81a-772cdc7e6a95/image.png" alt="Badge 7" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/1d36cb36-20fc-4961-8d70-6307c015d1aa/blob" alt="Badge 8" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/3595706b-442c-455b-9bb1-18fa81b3f8cf/image.png" alt="Badge 9" width="50" height="50"><img src="https://images.credly.com/size/680x680/images/2f73db94-bd85-4391-8885-6c14862457eb/image.png" alt="APIsec Certified Practitioner" width="50" height="50"><img src="https://images.credly.com/size/340x340/images/8b943c4b-c186-4e9f-84aa-004322b76eed/image.png" alt="ITIL" width="50" height="50">

## Education
<p>
    <img src="https://www.besthealthdegrees.com/wp-content/uploads/2018/04/western-governors-university-1024x1024.png" alt="WGU Graduate - Network Engineering & Cybersecurity" width="50" height="50">
</p>

## Working Towards
<p>
  <img src="https://images.credly.com/size/680x680/images/1ad16b6f-2c71-4a2e-ae74-ec69c4766039/azure-security-engineer-associate600x600.png" alt="Microsoft Security Engineer" width="50" height="50">
  <img src="https://training.linuxfoundation.org/wp-content/uploads/2021/09/KCNA-Logo-1000x1000.png" alt="Kubernetes and Cloud Native Associate (KCNA)" width="50" height="50">
  <img src="https://training.linuxfoundation.org/wp-content/uploads/2023/01/kcsa_badge_new-300x300.png" alt="Kubernetes and Cloud Native Security Associate (KCSA)" width="50" height="50">

    
</p>

---

[![MrGuato's GitHub stats - Dark](https://github-readme-stats.vercel.app/api?username=mrguato&show_icons=true&theme=dark&bg_color=0d1117&icon_color=58a6ff&title_color=58a6ff&text_color=c9d1d9#gh-dark-mode-only)](https://github.com/mrguato/github-readme-stats#gh-dark-mode-only)
[![MrGuato's GitHub stats - Light](https://github-readme-stats.vercel.app/api?username=mrguato&show_icons=true&theme=light&bg_color=f6f8fa&icon_color=1b1f23&title_color=0366d6&text_color=24292e#gh-light-mode-only)](https://github.com/mrguato/github-readme-stats#gh-light-mode-only)
[![Top Langs - Dark](https://github-readme-stats.vercel.app/api/top-langs/?username=mrguato&layout=compact&theme=dark&bg_color=0d1117&title_color=58a6ff&text_color=c9d1d9#gh-dark-mode-only)](https://github.com/mrguato/github-readme-stats#gh-dark-mode-only)
[![Top Langs - Light](https://github-readme-stats.vercel.app/api/top-langs/?username=mrguato&layout=compact&theme=light&bg_color=f6f8fa&title_color=0366d6&text_color=24292e#gh-light-mode-only)](https://github.com/mrguato/github-readme-stats#gh-light-mode-only)
