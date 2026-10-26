# Jonathan DeLeon

**Infrastructure and Security Lead.** I build and run the platforms, and I secure them while I'm building them instead of bolting security on afterward. Day to day that looks like hypervisors, Kubernetes, IaC pipelines, identity, detection, and the compliance work that ties it all together. After hours it's a homelab that runs like production, open source security tooling, and self-hosted servers for my family and friends.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/jonathan-deleon-cism/)
[![Credly](https://img.shields.io/badge/Credly-F7931E?style=flat-square&logo=credly&logoColor=white)](https://www.credly.com/users/jonathan-deleon.bfdd720a)
[![GitOps Notes](https://img.shields.io/badge/GitOps%20Notes-222222?style=flat-square&logo=astro&logoColor=white)](https://notes.deleontech.net)
[![pisentry](https://img.shields.io/badge/pisentry-0E9F6E?style=flat-square&logo=raspberrypi&logoColor=white)](https://mrguato.github.io/pisentry/)
[![Landing Site](https://img.shields.io/badge/Landing%20Site-%236A5ACD?style=flat-square&logo=amazonaws&logoColor=white)](https://cloud.mrcyberleon.org/)

---

## Now

- Taking **[pisentry](https://github.com/MrGuato/pisentry)** from v0.1 toward 1.0. A versioned rule schema and drop-in rules in `rules.d` are landing now.
- Contributing upstream to **[OpenSign](https://github.com/OpenSignLabs/OpenSign/pulls?q=author%3AMrGuato)**, the open source DocuSign alternative (docs and Docker deployment).
- Building WoW 3.3.5a addons and contributing to AzerothCore modules in the mod-playerbots ecosystem.
- Studying for AZ-500, KCNA, and KCSA, and looking at Talos and Omni for the next version of the cluster.

---

## Live: homelab k3s cluster

[![Cluster](https://img.shields.io/website?url=https%3A%2F%2Fstatus.deleontech.net&up_message=healthy&up_color=brightgreen&down_message=degraded&down_color=red&label=status.deleontech.net&style=for-the-badge&logo=kubernetes&logoColor=white)](https://status.deleontech.net)

Mixed-architecture k3s cluster on three Raspberry Pi 4s (Debian 13) and a Lenovo ThinkStation (RHEL 10.1). Everything is managed through FluxCD from [`MrGuato/pi-cluster`](https://github.com/MrGuato/pi-cluster) with separate base and staging overlays, so I never really touch the cluster directly. Secrets are encrypted with SOPS and age and committed right into the repo. Cloudflare Tunnel gets traffic in with zero open ports, Longhorn does the block storage, and Velero backs everything up to MinIO on a separate node. Falco watches the container runtime and [pisentry](https://github.com/MrGuato/pisentry) runs as a DaemonSet watching the hosts underneath. The dashboard above is pulling from kube-prometheus-stack.

---

## What I work on

A rough map of where I spend my time and the tools I tend to reach for.

| Area | Notes |
|---|---|
| Kubernetes | k3s, Helm, FluxCD, Kustomize, Longhorn, Velero, Falco. Currently looking at Talos and Omni. |
| IaC | Terraform, Ansible, and Packer. I usually build golden images with Packer, spin them up with Terraform, and let Ansible handle the config drift. |
| CI/CD and supply chain | GitLab CI and GitHub Actions, with Flux for GitOps. Scanning (SAST, SBOM, container, IaC) runs as real gates so things fail fast, and what I ship goes out as signed GHCR images with build provenance, CodeQL, and OpenSSF Scorecard. |
| Virtualization | vSphere and Proxmox. Hardened base images and automated patching. |
| Network | FortiGate, Palo Alto, Ubiquiti, Cisco. Zero-open-port ingress with Cloudflare Tunnel wherever I can get away with it. |
| Identity | Entra ID, Conditional Access, and least-privilege IAM across Azure and AWS. |
| Detection and response | Sentinel, SentinelOne, Rapid7, Defender XDR, and Tines for SOAR. On the host side I write my own detections, mapped to MITRE ATT&CK. Good telemetry usually makes detection a lot easier. |
| Compliance | CMMC Level 2 and NIST 800-171 in practice, plus CIS v8, NIST CSF 2.0, and Zero Trust. |
| Code | Go for security tooling, Bash for anything that runs in a container, Lua for WoW addons, and JavaScript for the dashboards and sites around all of it. |

---

## Featured: pisentry

<p align="center">
  <a href="https://github.com/MrGuato/pisentry">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/MrGuato/pisentry/main/docs/assets/readme-banner-dark.svg">
      <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/MrGuato/pisentry/main/docs/assets/readme-banner-light.svg">
      <img alt="pisentry: host security agent for Raspberry Pi and ARM Linux" src="https://raw.githubusercontent.com/MrGuato/pisentry/main/docs/assets/readme-banner-dark.svg" width="100%">
    </picture>
  </a>
</p>

**[Repo](https://github.com/MrGuato/pisentry) · [Website](https://mrguato.github.io/pisentry/) · [Releases](https://github.com/MrGuato/pisentry/releases) · [Container](https://github.com/MrGuato/pisentry/pkgs/container/pisentry)**

My main open source project. A single static Go binary that watches a small Linux host for the ten attacks that hit it most (SSH brute force, suspicious logins, privilege escalation, persistence, cryptominers, reverse shells, file tampering and more), ranks them, and tells you where to look first. Standard library only, about 12 MB resident, under 1% CPU on a 2 GB Pi. Output goes out as Prometheus metrics, JSON events, a terminal Top 10 report, and push alerts to ntfy, Discord, Slack, or any webhook. It runs as a hardened systemd service or a Flux-managed DaemonSet, right next to Falco: Falco covers the container runtime, pisentry covers the host.

![GitHub release](https://img.shields.io/github/v/release/MrGuato/pisentry?style=flat-square)
[![ci](https://github.com/MrGuato/pisentry/actions/workflows/ci.yml/badge.svg)](https://github.com/MrGuato/pisentry/actions/workflows/ci.yml)
[![codeql](https://github.com/MrGuato/pisentry/actions/workflows/codeql.yml/badge.svg)](https://github.com/MrGuato/pisentry/actions/workflows/codeql.yml)
[![OpenSSF Scorecard](https://img.shields.io/ossf-scorecard/github.com/MrGuato/pisentry?label=OpenSSF%20Scorecard&style=flat-square)](https://scorecard.dev/viewer/?uri=github.com/MrGuato/pisentry)
![Dependencies](https://img.shields.io/badge/Dependencies-none%2C%20stdlib%20only-blue?style=flat-square)
![Platforms](https://img.shields.io/badge/Platforms-arm64%20%7C%20armv7%20%7C%20amd64-success?style=flat-square&logo=raspberrypi)

---

## Projects

### Platform

#### [pi-cluster](https://github.com/MrGuato/pi-cluster) · [live status](https://status.deleontech.net)
My homelab cluster, fully declarative. Flux reconciles apps and infrastructure from Git, SOPS-encrypted secrets live in the public repo, and Renovate keeps image tags fresh with automated PRs. Velero does backups out to MinIO on a separate node, and Longhorn handles distributed block storage across the ARM and x86 nodes. It also hosts Forgejo, Docmost, Vikunja, linkding, Headlamp, and my notes site. The live dashboard at the top of this README runs on it.

#### [gitops-notes](https://github.com/MrGuato/gitops-notes) · [notes.deleontech.net](https://notes.deleontech.net)
A running journal of GitOps and DevOps experiments, built with Astro and served from the cluster. Writeups and lessons from the homelab, including the failures and not just the happy path.

### Self-hosted game servers

#### [valheim-game-server](https://github.com/MrGuato/valheim-game-server) · [docs](https://mrguato.github.io/valheim-game-server/) · [image](https://github.com/MrGuato/valheim-game-server/pkgs/container/valheim-game-server)
A Valheim dedicated server I host for family and friends, packaged so I can stop thinking about it. One CLI for setup, start, status, logs, backup, restore, and update, all driven from a single `.env`. Runs as non-root, saves cleanly on shutdown, takes verified backups with retention, and patches the game on every start so the image never goes stale. Opt-in BepInEx for mods. Our world is past 300,000 objects and still running on it.

#### [Longhouse](https://github.com/MrGuato/valheim-game-dashboard) · [live demo](https://mrguato.github.io/valheim-game-dashboard/) · [docs](https://mrguato.github.io/valheim-game-dashboard/docs.html)
The companion dashboard for that server, built because the group chat kept asking "who's on?" Server status straight from Steam's query, the in-game day, boss progression, weekly playtime and death leaderboards, a play-time heatmap, and armory-style profiles with a 3D voxel figure wearing each player's real gear. Runs in Docker next to the server.

#### [enshrouded-docker](https://github.com/MrGuato/enshrouded-docker) · [docs](https://mrguato.github.io/enshrouded-docker/) · [image](https://github.com/MrGuato/enshrouded-docker/pkgs/container/enshrouded-docker)
The Enshrouded sibling of my Valheim server. Enshrouded only ships a Windows dedicated server, so the image runs it under Wine and Xvfb, forces SteamCMD to fetch the Windows build, and patches the game on every start. One `./enshrouded` CLI covers setup, status, logs, updates, backups and restores, settings and Admin/Friend/Guest role passwords come from a single `.env`, and a one-line installer takes a fresh Linux host to a running server. Non-root, nightly Watchtower updates, and every change goes through hadolint, shellcheck, CodeQL, gitleaks and Trivy. Getting Xvfb lock files and SteamCMD to behave in a clean container was more fun than I expected.

### World of Warcraft

#### [muster](https://github.com/MrGuato/muster) · [docs](https://mrguato.github.io/muster/)
A WoW 3.3.5a addon for [mod-playerbots](https://github.com/mod-playerbots/mod-playerbots). Raise a whole dungeon or raid group from a template in one click, give orders by role or to a single bot, and switch each bot's strategies with checkboxes, all from one panel and a pinnable command bar.

#### [DialedInUI](https://github.com/MrGuato/DialedInUI) · [CurseForge](https://www.curseforge.com/wow/addons/dialedinui) and [NodeNotes](https://github.com/MrGuato/NodeNotes) · [CurseForge](https://www.curseforge.com/wow/addons/nodenotes)
Two published addons. DialedInUI gives you one-click layouts for Blizzard's own UI: pick from ten popular setups, preview them, apply through Edit Mode, and undo any time. NodeNotes remembers every herb and ore node you've gathered, what each one gave you, and lets you pin your own notes to them on the map.

#### Module contributions · [mod-dungeon-clear](https://github.com/jrad7/mod-dungeon-clear/pulls?q=author%3AMrGuato) and [its addon](https://github.com/jrad7/mod-dungeon-clear-addon/pulls?q=author%3AMrGuato)
Upstream work on an AzerothCore module that teaches playerbots to clear dungeons and raids: new boss handling for Arlokk and Ouro, raid fixes from Blackwing Lair, and a new event status state in the companion addon.

### Earlier

#### [AWS-Cloud-Challenge](https://github.com/MrGuato/AWS-Cloud-Challenge) · [site](https://cloud.mrcyberleon.org)
A serverless site on S3, CloudFront, Lambda, API Gateway, and DynamoDB, all provisioned through CloudFormation with least-privilege IAM and a proper deploy pipeline.

---

## Stack

#### Platform
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)
![FluxCD](https://img.shields.io/badge/FluxCD-5468FF?style=for-the-badge&logo=flux&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Longhorn](https://img.shields.io/badge/Longhorn-5F224B?style=for-the-badge&logo=longhorn&logoColor=white)
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=for-the-badge&logo=proxmox&logoColor=white)
![vSphere](https://img.shields.io/badge/vSphere-607078?style=for-the-badge&logo=vmware&logoColor=white)
![RHEL](https://img.shields.io/badge/RHEL-CC0000?style=for-the-badge&logo=redhat&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white)

#### Infrastructure as Code
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Packer](https://img.shields.io/badge/Packer-02A8EF?style=for-the-badge&logo=packer&logoColor=white)
![CloudFormation](https://img.shields.io/badge/CloudFormation-FF4F8B?style=for-the-badge&logo=amazonaws&logoColor=white)

#### Pipelines and supply chain
![GitLab CI](https://img.shields.io/badge/GitLab%20CI-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![GHCR](https://img.shields.io/badge/GHCR-181717?style=for-the-badge&logo=github&logoColor=white)
![CodeQL](https://img.shields.io/badge/CodeQL-2F363D?style=for-the-badge&logo=github&logoColor=white)
![Snyk](https://img.shields.io/badge/Snyk-4C4A73?style=for-the-badge&logo=snyk&logoColor=white)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=for-the-badge&logo=aqua&logoColor=white)
![SOPS](https://img.shields.io/badge/SOPS%2Fage-000000?style=for-the-badge)
![Renovate](https://img.shields.io/badge/Renovate-1A1F6C?style=for-the-badge&logo=renovatebot&logoColor=white)

#### Cloud and edge
![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Traefik](https://img.shields.io/badge/Traefik-24A1C1?style=for-the-badge&logo=traefikproxy&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-222222?style=for-the-badge&logo=githubpages&logoColor=white)

#### Network
![Fortinet](https://img.shields.io/badge/FortiGate-EE2E24?style=for-the-badge&logo=fortinet&logoColor=white)
![Palo Alto](https://img.shields.io/badge/Palo%20Alto-172A6B?style=for-the-badge&logo=paloaltonetworks&logoColor=white)
![Ubiquiti](https://img.shields.io/badge/Ubiquiti-0559C9?style=for-the-badge&logo=ubiquiti&logoColor=white)
![Cisco](https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)

#### Observability
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F5A800?style=for-the-badge&logo=grafana&logoColor=white)

#### Security operations
![Sentinel](https://img.shields.io/badge/Sentinel-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![SentinelOne](https://img.shields.io/badge/SentinelOne-5B2E91?style=for-the-badge&logo=sentinelone&logoColor=white)
![Rapid7](https://img.shields.io/badge/Rapid7-D02F2F?style=for-the-badge&logo=rapid7&logoColor=white)
![Defender XDR](https://img.shields.io/badge/Defender%20XDR-00A4EF?style=for-the-badge&logo=microsoft&logoColor=white)
![Entra ID](https://img.shields.io/badge/Entra%20ID-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Falco](https://img.shields.io/badge/Falco-00AEC7?style=for-the-badge&logo=falco&logoColor=white)
![Tines](https://img.shields.io/badge/Tines-5A67D8?style=for-the-badge)
![Nessus](https://img.shields.io/badge/Nessus-00B3E3?style=for-the-badge&logo=tenable&logoColor=white)

#### Languages
![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Lua](https://img.shields.io/badge/Lua-2C2D72?style=for-the-badge&logo=lua&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

#### Compliance
![CMMC L2](https://img.shields.io/badge/CMMC%20L2-006400?style=for-the-badge)
![NIST 800-171](https://img.shields.io/badge/NIST%20800--171-4CAF50?style=for-the-badge)
![NIST CSF 2.0](https://img.shields.io/badge/NIST%20CSF%202.0-4CAF50?style=for-the-badge)
![CIS v8](https://img.shields.io/badge/CIS%20v8-E91E63?style=for-the-badge)
![Zero Trust](https://img.shields.io/badge/Zero%20Trust-FF6F00?style=for-the-badge)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-C8102E?style=for-the-badge)

---

## Credentials

<table><tr>
<td><img src="https://images.credly.com/size/680x680/images/d0891dee-6360-496c-9981-40652523b502/dbdea6794f1a6bbcc18d90eea923421aac7df6b5.png" alt="CISM" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/38b12225-5b48-44e1-8750-20928cc595ea/image.png" alt="CCSP" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/564a69d3-b7c6-4738-aa2e-1d803869876c/blob" alt="SentinelOne Administrator" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/6b9a3559-90bd-4412-b156-21f99670206a/image.png" alt="SentinelOne Incident Responder" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/fc1352af-87fa-4947-ba54-398a0e63322e/security-compliance-and-identity-fundamentals-600x600.png" alt="Microsoft Security Compliance and Identity Fundamentals" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/be8fcaeb-c769-4858-b567-ffaaa73ce8cf/image.png" alt="Azure Fundamentals" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/20082fc1-94af-4773-9df0-28856b566748/image.png" alt="Fortinet Certified Associate Cybersecurity" width="50" height="50"></td>
<td><img src="https://www.itonlinelearning.com/wp-content/uploads/2024/01/04294-comptia-cert-badges_specialist-ccap-540x503.png" alt="CompTIA CCAP" width="50" height="50"></td>
</tr><tr>
<td><img src="https://comptiacdn.azureedge.net/webcontent/images/default-source/certproduct/pathways/04294-comptia-cert-badges-csis.png?sfvrsn=64a8a736_2" alt="CompTIA CSIS" width="50" height="50"></td>
<td><img src="https://nyledige.dk/media/2155/secure-cloud-professional-cscp-for-ledige.png?width=1024&height=1024&mode=min" alt="CompTIA CSCP" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/7495098d-c8c3-41a8-a81a-772cdc7e6a95/image.png" alt="CCSK" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/1d36cb36-20fc-4961-8d70-6307c015d1aa/blob" alt="Credly Badge" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/3595706b-442c-455b-9bb1-18fa81b3f8cf/image.png" alt="Credly Badge" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/680x680/images/2f73db94-bd85-4391-8885-6c14862457eb/image.png" alt="APIsec Certified Practitioner" width="50" height="50"></td>
<td><img src="https://images.credly.com/size/340x340/images/8b943c4b-c186-4e9f-84aa-004322b76eed/image.png" alt="ITIL" width="50" height="50"></td>
<td></td>
</tr></table>

## Education

<img src="https://www.besthealthdegrees.com/wp-content/uploads/2018/04/western-governors-university-1024x1024.png" alt="WGU Graduate, Network Engineering and Cybersecurity" width="50" height="50">

## Working Towards

<table><tr>
<td><img src="https://images.credly.com/size/680x680/images/1ad16b6f-2c71-4a2e-ae74-ec69c4766039/azure-security-engineer-associate600x600.png" alt="Microsoft Security Engineer" width="50" height="50"></td>
<td><img src="https://training.linuxfoundation.org/wp-content/uploads/2021/09/KCNA-Logo-1000x1000.png" alt="Kubernetes and Cloud Native Associate (KCNA)" width="50" height="50"></td>
<td><img src="https://training.linuxfoundation.org/wp-content/uploads/2023/01/kcsa_badge_new-300x300.png" alt="Kubernetes and Cloud Native Security Associate (KCSA)" width="50" height="50"></td>
</tr></table>

---

[![MrGuato's GitHub stats - Dark](https://github-readme-stats.vercel.app/api?username=mrguato&show_icons=true&theme=dark&bg_color=0d1117&icon_color=58a6ff&title_color=58a6ff&text_color=c9d1d9#gh-dark-mode-only)](https://github.com/MrGuato)
[![MrGuato's GitHub stats - Light](https://github-readme-stats.vercel.app/api?username=mrguato&show_icons=true&theme=light&bg_color=f6f8fa&icon_color=1b1f23&title_color=0366d6&text_color=24292e#gh-light-mode-only)](https://github.com/MrGuato)
[![Top Langs - Dark](https://github-readme-stats.vercel.app/api/top-langs/?username=mrguato&layout=compact&theme=dark&bg_color=0d1117&title_color=58a6ff&text_color=c9d1d9#gh-dark-mode-only)](https://github.com/MrGuato)
[![Top Langs - Light](https://github-readme-stats.vercel.app/api/top-langs/?username=mrguato&layout=compact&theme=light&bg_color=f6f8fa&title_color=0366d6&text_color=24292e#gh-light-mode-only)](https://github.com/MrGuato)
